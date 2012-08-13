Store.js
======

`Store.js` 是一个以高级浏览器为目标对象的本地存储插件，其对`localStorage`抑或`sessionStorage`做了简单的封装,具体使用方法如下会有详细的说明。

`Store.js` 分为两个版本 ， 一个版本符合`CMD`模块规范 ，另一个版本则为原始代码。 


[CMD](https://github.com/seajs/seajs/issues/242)

API
------------------

### createStorage  param -> name : string  创建该name下的本地存储


根据创建成功与否会有不同的返回

`isSupport` boolean 客户端是否支持该name存储

### 失败返回

`isSupport : false`

### 成功返回

`isSupport : true`   

> `get : function(key){}`

key - string
返回 任何数据类型
获取key对应的key值

> `set : function(key,val){}`

key - string , val - 任何数据类型
无返回
置key以及对应的key值

> `remove : function(key){}`

key - string
无返回
删除对应的键以及键值

> `clear : function(prefix){}`

prefix  - string 可选 
无返回
在无prefix存在的情况下，调用clear将清除所有localStorage存储
在存在prefix的情况下，调用clear将清除所有含有该前缀的存储信息 

> `getAll : function(prefix){}`

prefix - string 可选
返回所有localStorage存储信息，或者含有prefix前缀的存储信息，如果没有任何存储信息，返回null



something else
------------------

在使用`CMD`模块时 ， 需要保证页面中已经引入了`seajs` [seajs](http://seajs.org)

`<script src="path/sea.js"></script>` 当然你也可以把seajs使用异步方式引入

```javascript

seajs.use('path/store',function(store){
  // use store to do something
})

```

### createStorage  param -> name : string 


使用如下方式创建本地存储

```javascript

var store = require('path/store')
// 需指明创建什么存储
var s = store.createStorage('localStorage')

```

当传入的`name` 为非`localStorage` 和 `sessionStorage`  直接返回 `false`

如果浏览器不支持`localStorage` 或 `sessionStorage` 也将返回 `false`

