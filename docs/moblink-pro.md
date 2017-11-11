### 配置

| 参数       | 类型    | 可选值                        | 说明 |
|----------  |--------|-------------------------------|------|
| `el`       | string, Array | `'.class'` `['#id1','#id2']` | 跳转链接的承载元素 |
| `path`     | string | `site/page` | 对应App里的路径（`必须一一对应`） |
| `params`   | Object | `{key: value}` | 网页需要带给客户端的参数 |
| `appkey`   | string | `{key: value}` | 选填 |
| `autoOpenApp`   | Boolean | `true`,`false` | 自动跳转App（只能设置一个） |
| `failcallback`   | Function | args => `cfg,data,env` | 跳转失败回调|

---
### 多需求配置


```js
    // MobLink({...},fn,fn.fn)  => 如下:

    MobLink({
        appkey: config.appkey,
        el: '#moblink',
        path: config.path,
        params: config.params,
        autoOpenApp: true,
        failcallback: (cfg,data,env) => {
            console.log(cfg)  // 传入的参数
            console.log(data) // 后台配置
            console.log(env)  // 设备识别函数
           // window.location.href = env.isIOS() ? data.iosurl : data.andurl  // 获取下载链接
        },
    },(res,url)=>{
        // 后台配置获取 成功/失败 回调
        // @ res 后台配置
        // @ url 生成的跳转链接


    },(env)=>{
        // 创建moblin请求后台配置之前的回调
        // @ env 设备识别函数

        return false //阻止MobLink继续执行
    });
```