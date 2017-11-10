<h1 class="bd-title" id="content">MobLink.js</h1>

---
#### 默认浮框
---


属性 `el` 表示网页上Element的id值,该字段为空或者不写则表示MobLink默认浮层上的打开按钮 (支持selector)。

```js
    MobLink([
        {
            el: '',
            path: 'demo/a',
            params: {
                key1: 'value1',
                key2: 'value2',
            }
        },
        {
            el: '#openAppBtn',
            path: 'demo/b',
            params: {
                key1: 'value1',
                key2: 'value2',
            }
        },
    ]);
```
#### 调用
html
```html
    <!-- 在html上添加 -->
    <script type="text/javascript" src="//f.moblink.mob.com/3.0.1/moblink.js?appkey=`您自己的AppKey`"></script>
```
javascript
```js
    // 页面上有多个元素需要跳转时使用数组方式,仅单个元素时可以使用对象的方式进行初始化
    //方式1
    MobLink([...])
    //方式2
    MobLink({...})
```

### 配置

| 参数       | 类型    | 可选值                        | 说明 |
|----------  |--------|-------------------------------|------|
| `el`       | string, Array | `'.class'` `['#id1','#id2']` | 跳转链接的承载元素 |
| `path`     | string | `site/page` | 对应App里的路径（`必须一一对应`） |
| `params`   | Object | `{key: value}` | 网页需要带给客户端的参数 |

第一个参数 {

failcallback 引导页回调(初始配置，后台配置，env)
}
第二个参数 后台配置获取成功失败回调  （后台配置，生成的url）

第三个参数 创建moblin请求后台配置之前的回调（env）  return false 可以阻止请求后台配置接口


javascript
```js
    MobLink({
        appkey: config.appkey,
        el: '#moblink',
        path: config.path,
        params: config.params,
        autoOpenApp: true,
        failcallback: (cfg,data,env) => {
            console.log(cfg)
            console.log(data)
            console.log(env)
           window.location.href = env.isIOS() ? data.iosurl : data.andurl
        },
    },res=>{
        if(res.ui && res.ui.icon) {
            document.getElementById('icon').src = res.ui.icon
        }


    },(env)=>{

        if(env.isIOS() && env.isWx()){
            document.getElementById("mask-img").src = '../images/guide_ios.png'
            document.getElementById("mask").style.display = 'block'
            return false

        }
        if(env.isAndroid() && env.isWx()){
            document.getElementById("mask-img").src = '../images/guide_android.png'
            document.getElementById("mask").style.display = 'block'
            return false
        }

    });
```