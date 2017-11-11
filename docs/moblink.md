<h1 class="bd-title" id="content">MobLink.js - 3.0.1</h1>

---
#### 默认浮框
![](ui.png)

属性 `el` 表示网页上Element的id值,该字段为空或者不写,则表示使用MobLink`默认浮层`样式,跳转则为浮层默认的`打开`按钮

```js
    MobLink({
        el: '',
        path: 'demo/a',
        params: {
            key1: 'value1',
            key2: 'value2',
        }
    });


```

#### 调用 (需要2步)
1. html
```html
    <!-- 在html上添加 -->
    <script type="text/javascript" src="//f.moblink.mob.com/3.0.1/moblink.js?appkey=您自己的AppKey"></script>
```
2. js
```js
    // 页面上有多个元素需要跳转时使用数组方式
    // 仅单个元素时可以使用对象的方式进行初始化
    //方式1
    MobLink([
            {
                el: '#openAppBtn', // (支持selector) 方式 1. '.class' 2. '#id1'  3. ['#id1','#id2']
                path: 'demo/b',
                params: {
                    key1: 'value1',
                    key2: 'value2',
                }
            },
        ]);
    //方式2
    MobLink({...})
```
