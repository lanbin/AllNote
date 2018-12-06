## 1. wx.request对RESTful API支持

官方的说明是这样写的 : [小程序开发 - 基本能力](https://developers.weixin.qq.com/miniprogram/dev/framework/ability/network.html#%E5%9B%9E%E8%B0%83%E5%87%BD%E6%95%B0)
> **回调函数**
> 只要成功接收到服务器返回，无论 statusCode 是多少，都会进入 success 回调。请开发者根据业务逻辑对返回值进行判断。

即便是支持Promise的[**wx-promise-pro**](https://github.com/youngjuning/wxPromise/)也没有很好对这个部分进行支持.
所以, 在项目的__src/main.js__文件中,增加一个方法对RESTFul方法进行支持

```javascript
wx.proRequest = param => {
    return new Promise((resolve, reject) => {
        param.data = param.data || {}

        // get request add timestamp
        param.method = param.method ? param.method : 'get'
        if (param.method.toLowerCase() !== 'post') {
            param.data['_t'] = Date.now()
        }

        // 这里还可以增加各种拦截器要做的事情
        wx.request({
            success(res) {
                if (res.statusCode === 200) {
                    resolve(res)
                } else {
                    reject(res)
                }
            },
            fail(res) {
                reject(res)
            },
            ...param
        })
    })
}
```

## 2. 剩下的都是坑.要不是有流量...
