# 微信小程序上传文件至阿里云
###快速使用三部曲
```
1.在config文件配置阿里云
    let fileHost="http://frdscm.oss-cn-shenzhen.aliyuncs.com"
    let config = {
      uploadImageUrl: `${fileHost}`, //默认存在根目录，可根据需求改
      AccessKeySecret: 'h3RdiKm0ohUUN5tzRMoZ0nvqhxxxxx',
      OSSAccessKeyId: 'LTAIbH8hu0Uexxxx',
      timeout: 87600 //这个是上传文件时Policy的失效时间
    };
 2.导入上传方法
    const uploadImage = require('@src/untils/upload/uploadAliyun.js')
 3.使用
     uploadAioss = (filePath, key) => { // 上传阿里云
        return new Promise((reslove, reject) => {
            uploadImage(
                filePath, // 文件真实上传路径
                "",
                key, // 传给后台的路径 => 自己拼的路径 一般为时间+uuid+文件名等因人而异
                (res) => {
                    reslove(res)
                    console.log("上传成功", res)
                },
                (e) => {
                    reject(e)
                }
            )
        })
      }
 
 注：文件真实上传路径移步小程序api wx.uploadFile
```
