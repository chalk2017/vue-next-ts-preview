# 使用方式
## 一、安装
```npm
npm install lzx-uploader
```
## 二、使用方式
```javascript
import { Uploader } from 'lzx-uploader'
```

```javascript
const uploader = new Uploader({
  el:document.getElementById("upload-button"), // 用于触发上传选择的元素
  env: 'pc', // pc 端 mobile 移动端
  chunkSize: 1024 * 4, //4kb的分片，默认分片大小为5M
  path: '/backend/storage/upload/prepare', // 服务器上传地址，请配置相关代理
  accept: 'image/*', // 接收的可上传的文件类型
  multiple:true, // 是否可进行多选
  getDetail:true // 是否获取文件详情
})
// loaded 上传的文件对应的进度百分比(0--100) number类型
uploader.$on('progress', (loaded, file, response, index) => {
  console.log('progress',loaded, file, response, index)
})
uploader.$on('md5', (files) => {
  console.log('md5', files)
})
// 上传完成
uploader.$on('success', (file, response, index) => {
  console.log('success', file, response, index)
})
// 上传暂停
uploader.$on('pause', (file, response, index) => {
  console.log('pause', file, response, index)
})
// 获取文件上传成功后的详细信息，需要设置getDetail为true才会触发此事件
uploader.$on('detail', (fileDetail, response,index) => {
  console.log('detail', fileDetail, response, index)
})
```
