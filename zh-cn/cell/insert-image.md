# 插入图片

支持两种方式插入 PNG 或 JPEG 图像：图像位于本地磁盘时使用路径方式，已经持有字节流（上传、对象存储、流式读取等）时使用缓冲区方式。

## **函数原型**

```php
insertImage(int $row, int $column, string $localImagePath, double $widthScale = 1.0, double $heightScale = 1.0): self

insertImageBuffer(int $row, int $column, string $bytes, ?array $options = null): self
```

### **int $row**

> 单元格所在行

### **int $column**

> 单元格所在列

### **string $localImagePath**

> 图片路径（PNG 或 JPEG）

### **double $widthScale**

> 对图像 X 轴进行缩放处理；默认为 1，保持原始宽度；值为 0.5 时，图像宽度为原图的 1/2。

### **double $heightScale**

> 对图像 Y 轴进行缩放处理；默认为 1，保持原始高度；值为 0.5 时，图像高度为原图的 1/2。

### **string $bytes**

> 原始图片字节流，例如 `file_get_contents()` 或网络流读取的返回值。

### **array $options**（`insertImageBuffer` 可选参数）

> 全部为可选键：
>
> - `x_offset` _int_ —— 横向像素偏移
> - `y_offset` _int_ —— 纵向像素偏移
> - `x_scale` _double_ —— 横向缩放比例（默认 `1.0`）
> - `y_scale` _double_ —— 纵向缩放比例（默认 `1.0`）
> - `object_position` _int_ —— 锚定模式（默认 `2`）
> - `url` _string_ —— 图像链接地址
> - `description` _string_ —— 无障碍 / 替代文本描述

## 示例 —— 本地路径

```php
$excel = new \Vtiful\Kernel\Excel($config);

$excel->fileName('tutorial.xlsx')
      ->insertImage(5, 0, '/vagrant/logo.png')
      ->output();
```

## 示例 —— 内存字节流

```php
$excel = new \Vtiful\Kernel\Excel($config);

$bytes = file_get_contents('/vagrant/logo.png');

$excel->fileName('tutorial.xlsx')
      ->insertImageBuffer(5, 0, $bytes, [
          'x_scale'     => 0.5,
          'y_scale'     => 0.5,
          'url'         => 'https://github.com/viest/php-ext-xlswriter',
          'description' => 'xlswriter logo',
      ])
      ->output();
```
