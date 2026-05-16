# Skip leading rows

* Reading is available on Windows from extension `1.3.4.1` upwards;
* Extension version `>= 1.2.7`;
* When installing via PECL, answer `yes` when prompted to enable the reader.

## Function Prototype

```php
setSkipRows(int $skipRows): self
```

> Discards the first `$skipRows` rows of the active sheet from the iterator. Apply it after `openSheet()` and before `nextRow()` / `getSheetData()`.

## Test data preparation

```php
$config = ['path' => './tests'];
$excel  = new \Vtiful\Kernel\Excel($config);

$filePath = $excel->fileName('tutorial.xlsx')
    ->header(['', 'Cost'])
    ->data([
        [],
        ['viest', '']
    ])
    ->output();
```

## Example 1

```php
// read all data, skipping the first row
$data = $excel->openFile('tutorial.xlsx')
    ->openSheet('Sheet1')
    ->setSkipRows(1)
    ->getSheetData();
```

## Example 2

```php
// read all data, skipping the first two rows
$data = $excel->openFile('tutorial.xlsx')
    ->openSheet('Sheet1')
    ->setSkipRows(2)
    ->getSheetData();
```
