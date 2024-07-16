<div align="center">
  <img width="200" height="200"
    src="./logo.png">
  <h1>bmp-ts</h1>
  <p>A pure typescript <code>bmp</code> encoder and decoder.</p>
</div>

[![Codecov](https://img.shields.io/codecov/c/github/hipstersmoothie/bmp-ts.svg?style=for-the-badge)](https://codecov.io/gh/hipstersmoothie/bmp-ts)
[![code style: prettier](https://img.shields.io/badge/code_style-prettier-ff69b4.svg?style=for-the-badge)](https://github.com/prettier/prettier)

Supports decoding and encoding in all bit depths (1, 4, 8, 16, 24, 32).

> 本仓库fork自[bmp-ts](https://github.com/jimp-dev/bmp-ts), 兼容了某些打印机打印深度为1的bmp格式的图片时，打印效果为反色的问题
> This repository is forked from [bmp-ts](https://github.com/jimp-dev/bmp-ts), and it addresses the issue where some printers print 1-bit BMP images in inverted colors.

## Install

```sh
npm install bmp-ts-for-printer
```

## Usage

### Example: convert image to 1 bit

```js
const bmp = require('bmp-ts-for-printer');
const Jimp = require('jimp');
const fs = require('fs');

const image = await Jimp.read(inputImagePath);
const buffer = await image
    .getBufferAsync(Jimp.MIME_BMP);
const bitmap = bmp.decode(buffer);
bitmap.bitPP = 1;
const { data } = bmp.encode(bitmap);
fs.writeFileSync('./image.bmp', data); 
```