# Check whether a worksheet exists

## Function Prototype

```php
existSheet(string $sheetName): bool
```

## Example

```php
$config = ['path' => './tests'];

$fileObject = new \Vtiful\Kernel\Excel($config);

$fileObject->fileName('tutorial.xlsx')
    // add a worksheet named twoSheet
    ->addSheet('twoSheet');

var_dump($fileObject->existSheet('twoSheet'));
var_dump($fileObject->existSheet('notFoundSheet'));
```

## Example output

```php
bool(true)
bool(false)
```
