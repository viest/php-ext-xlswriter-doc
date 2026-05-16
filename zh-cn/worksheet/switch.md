# 切换工作表

## **函数原型**

```php
checkoutSheet(string $sheetName): self

activateSheet(string $sheetName): bool
```

> `checkoutSheet` 用于切换当前写入工作表；`activateSheet` 用于设置打开 xlsx 时 Excel 默认展示的工作表，仅影响视图，不改变写入目标。

## **实例**

```php
$config = [
  'path' => './tests'
];

$excel      = new \Vtiful\Kernel\Excel($config);
$fileObject = $excel->fileName("tutorial01.xlsx");

$fileObject->header(['name', 'age'])
    ->data([
    ['viest', 21],
    ['viest', 22],
    ['viest', 23],
    ]);

// 添加工作表，并插入数据
$fileObject->addSheet('twoSheet')
    ->header(['name', 'age'])
    ->data([['vikin', 22]]);

// 切换回默认工作表，并追加数据
$fileObject->checkoutSheet('Sheet1')
    ->data([['sheet1']]);

$filePath = $fileObject->output();
```

