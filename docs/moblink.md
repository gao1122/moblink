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
页面上有多个元素需要跳转时使用数组方式,仅单个元素时可以使用对象的方式进行初始化
```js
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


