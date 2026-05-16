# Excel 序列日期转 Unix 时间戳

Excel 以浮点序列存储日期（自 1900-01-01 或 1904-01-01 起的天数）。当读取器返回 `double` 形态的日期单元格时，可以使用 `timestampFromDateDouble()` 将其转换为 Unix 时间戳。

## 函数原型

```php
static Excel::timestampFromDateDouble(float $excelSerial): int
```

> 当 `$excelSerial <= 0` 时返回 `0`。

## 示例

```php
$timestamp = \Vtiful\Kernel\Excel::timestampFromDateDouble(44197.0);

echo date('Y-m-d', $timestamp); // 2021-01-01
```
