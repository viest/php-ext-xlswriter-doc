# Insert image

Embed a PNG or JPEG inside a cell. Use the path-based variant when the image lives on disk, or the buffer-based variant when the bytes are already in memory (uploads, S3, streamed data, …).

## **Function Prototype**

```php
insertImage(int $row, int $column, string $localImagePath, double $widthScale = 1.0, double $heightScale = 1.0): self

insertImageBuffer(int $row, int $column, string $bytes, ?array $options = null): self
```

### **int $row**

> cell row

### **int $column**

> cell column

### **string $localImagePath**

> Path to a PNG or JPEG file.

### **double $widthScale**

> Scale the image on the X axis; the default is 1, maintaining the original width; when the value is 0.5, the image width becomes 1/2 of the original.

### **double $heightScale**

> Scale the image on the Y axis; the default is 1, maintaining the original height; when the value is 0.5, the image height becomes 1/2 of the original.

### **string $bytes**

> Raw image bytes, e.g. the return value of `file_get_contents()` or a stream read.

### **array $options** (optional, for `insertImageBuffer`)

> All keys are optional:
>
> - `x_offset` _int_ — horizontal pixel offset
> - `y_offset` _int_ — vertical pixel offset
> - `x_scale` _double_ — horizontal scale factor (default `1.0`)
> - `y_scale` _double_ — vertical scale factor (default `1.0`)
> - `object_position` _int_ — anchor mode (default `2`)
> - `url` _string_ — hyperlink the image points to
> - `description` _string_ — accessibility / alt-text description

## Example — path

```php
$excel = new \Vtiful\Kernel\Excel($config);

$excel->fileName('tutorial.xlsx')
      ->insertImage(5, 0, '/vagrant/logo.png')
      ->output();
```

## Example — buffer

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
