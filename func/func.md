# 闭包作用域与构造函数结合

## 前言

由于对模块化一知半解，特想知根知底，故而记录此文。

## 为什么要模块化
* 网站慢慢变成web应用程序
* 站点变大，代码复杂性增加
* 最优化的部署代码
* 分离JS文件／模块

## 从设计模式开始

### 传统写法

> 污染全局导致命名冲突

```js
function func1() {}
function func2() {}
```

### 简单封装（命名空间模式）

> 减少了全局变量，但本质上还是一个对象，依旧不安全
```js
var MYOBJ = {
  func1: function() {},
  func2: function() {}
}
MYOBJ.func1()
```

### 匿名闭包（IIFE模式）

> 函数是JavaScript的唯一作用域

```js
var Module = (function() {
  var PRIVATE = `private variable`
  var func = function() {
    console.log(PRIVATE)
  }

  return {
    func: func
  }
})()

Module.func()
Module.PRIVATE // undefined
```
```