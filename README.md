# bmp tools

用于一位 bmp 图的转换等。

## 使用

```javascript
import bmp from "@tikkhun/bmp";

export async function bmpTo1Bit(image) {
  const buffer = await image.getBufferAsync(Jimp.MIME_BMP);
  const bitmap = bmp.decode(buffer);
  bitmap.bitPP = 1;
  const { data } = bmp.encode(bitmap);
  return data;
}
```

完整例子

```javascript
import Jimp from "jimp";
async function bootstrap() {
  const imagePath = "test.png";
  const image = await Jimp.read(imagePath);
  const buffer = await image.getBufferAsync(Jimp.MIME_BMP);
  const oneBitBmpBuffer = await bmpTo1Bit(buffer);
  const savedPath = "test.bmp"
  fs.writeFileSync(savedPath, oneBitBmpBuffer);
}
bootstrap();
```
