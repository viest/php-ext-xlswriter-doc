# Excel serial date to unix timestamp

Excel stores dates as a floating-point serial (days since 1900-01-01 or 1904-01-01). When the reader returns a date cell as a `double`, use `timestampFromDateDouble()` to convert it into a Unix timestamp.

## Function Prototype

```php
static Excel::timestampFromDateDouble(float $excelSerial): int
```

> Returns `0` when `$excelSerial <= 0`.

## Example

```php
$timestamp = \Vtiful\Kernel\Excel::timestampFromDateDouble(44197.0);

echo date('Y-m-d', $timestamp); // 2021-01-01
```
