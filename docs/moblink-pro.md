### 配置

| 参数       | 类型    | 可选值                        | 说明 |
|----------  |--------|-------------------------------|------|
| `el`       | string, Array | `'.class'` `['#id1','#id2']` | 跳转链接的承载元素 |
| `path`     | string | `site/page` | 对应App里的路径（`必须一一对应`） |
| `params`   | Object | `{key: value}` | 网页需要带给客户端的参数 |
| `failcallback`   | Function | args => `cfg,data,env` | 跳转失败回调|

---
### 跳转失败处理
跳转失败，会返回引导页，如不想跳转引导页，用 `failcallback` 函数

```js
    // MobLink({...})  => 如下:

    MobLink({
        el: '#moblink',
        path: 'demo/a',
        params: {},
        failcallback: (cfg,data,env) => {
            console.log(cfg)  // 传入的参数
            console.log(data) // 后台配置
            console.log(env)  // 设备识别函数
           // window.location.href = env.isIOS() ? data.iosurl : data.andurl  // 获取下载链接
        },
    });
```