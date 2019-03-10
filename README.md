Taro Qiniu Webpack Plugin
====================

> 上传 Webpack Assets 至 七牛 CDN

## 前提

需要 Node 版本在 v4.0 以上

## 安装

```sh
npm i -D taro-qiniu@1.0.0
```

## 使用方法

支持的配置项:

+ `accessKey` 七牛 AccessKey
+ `secretKey` 七牛 SecretKey
+ `bucket` 七牛存储对象名称
+ `path` 存储路径， 默认为 `[hash]`，也可以指定 hash 长度，如: `[hash:8]`
+ `exclude` 可选，排除特定文件，正则表达式，如: `/index\.html$/`
+ `include` 可选，指定要上传的文件，正则表达式，如: `/app\.js$/`
+ `batch` 可选，批量上传文件并发数，默认 20
+ `zone` 可选，存储在七牛的机房（华东 `Zone_z0`、华北 `Zone_z1`、华南 `Zone_z2`、北美 `Zone_na0`）

***注: Webpack 的 `output.publicPath` 要指向七牛云（或自定义的）域名地址***

```js
// 引入
const QiniuPlugin = require('taro-qiniu');

// 配置 Plugin
const qiniuPlugin = new QiniuPlugin({
  accessKey: 'my-access-key',
  secretKey: 'my-secret-key',
  bucket: 'my-bucket',
  path: '[hash]/'
});

// Webpack 的配置
module.exports = {
 output: {
    // 此处为七牛提供的域名(http://7xqhak.com1.z0.glb.clouddn.com) 加上 path([hash]/)
    publicPath: "http://7xqhak.com1.z0.glb.clouddn.com/[hash]/"
    // ...
 },
 plugins: [
   qiniuPlugin
   // ...
 ]
 // ...
}
```

## 效果图

无图无真相 ^\_\^

![Preview](preview.png)