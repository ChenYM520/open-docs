# 简介

保存视频到系统相册。

## 使用限制

- 基础库 [1.10.0](https://opendocs.alipay.com/mini/framework/lib) 开始支持，低版本需要做 [兼容处理](https://docs.alipay.com/mini/framework/compatibility)。
- 此 API 支持个人支付宝小程序、企业支付宝小程序使用。
- 小程序开发者工具（IDE）暂不支持调试此 API，请使用 [真机调试](https://opendocs.alipay.com/mini/ide/remote-debug) 功能在真机进行调试。

# 接口调用

## 示例代码

### .js 示例代码
```javascript
// 本地文件
my.chooseVideo({
  sourceType: ['album','camera'],
  maxDuration: 60,
  camera: 'back',
  success(res) {
    my.saveVideoToPhotosAlbum({
     filePath: res.tempFilePath,
      complete(res2) {
       console.log(res2);
      }
    });
  }
})
// 网络路径
my.saveVideoToPhotosAlbum({
  filePath:'https://gw.alipayobjects.com/mdn/rms/afts/file/A*lj35SaIgk1sAAAAAAAAAAAAAARQnAQ',
  complete(res) {
    console.log(res);
  }
});
```

## 入参

Object 类型，属性如下：

| **属性** | **类型** | **必填** | **描述** |
| --- | --- | --- | --- |
| filePath | String | 是 | 视频文件路径，支持网络路径、[本地临时文件](https://opendocs.alipay.com/mini/03dt4s#%E6%9C%AC%E5%9C%B0%E4%B8%B4%E6%97%B6%E6%96%87%E4%BB%B6)、[本地缓存文件](https://opendocs.alipay.com/mini/03dt4s#%E6%9C%AC%E5%9C%B0%E7%BC%93%E5%AD%98%E6%96%87%E4%BB%B6)、[本地用户文件](https://opendocs.alipay.com/mini/03dt4s#%E6%9C%AC%E5%9C%B0%E7%94%A8%E6%88%B7%E6%96%87%E4%BB%B6)。其中本地缓存文件、本地用户文件路径客户端 10.2.70 开始支持，之前的客户端版本存在兼容性问题。 |
| success | Function | 否 | 调用成功的回调函数。 |
| fail | Function | 否 | 调用失败的回调函数。 |
| complete | Function | 否 | 调用结束的回调函数（调用成功、失败都会执行）。 |

### 错误码

| **错误码** | **描述** |
| --- | --- |
| 2 | 参数无效，没有传 filePath 参数。 |
| 15 | 没有开启相册权限（iOS only）。 |
| 16 | 手机相册存储空间不足（iOS only）。 |
| 17 | 保存图片过程中的其他错误。 |
