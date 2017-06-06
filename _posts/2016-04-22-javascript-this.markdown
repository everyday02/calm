---
layout:     post
title:      "javascript this关键字"
subtitle:   "The This"
date:       2016-02-11
author:     "HeHang"
header-img: "img/post-bg-js-version.jpg"
tags:
    - javaScript
---

### javascript this | 关键字

this是javaScript中的一个关键字，大多数情况下，函数的调用方式不同，this的指向也会动态发生改变。

> 需要记住的是：哪个对象调用的this，this就指向谁。


##### 全局环境下

当我们在全局环境下使用this时，将指向window对象。
```javascript
  console.info(this === window);
  // true

  var hello = 'Hello World';

  console.info(this.hello);
  // Hello World;
```

#### 在函数内

> 根据函数的归属对象不同，this指向也会有所不同。

##### 全局函数

```javascript

  // globalFunc归属于window对象。
  function globalFunc() {
    // this指向调用它的对象
    console.info(this === window);
  }

  globalFunc();
  // true
  window.globalFunc();
  // true

```


##### 指定对象

``` javascript

  function func() {
    console.info(this === window);
  }

  var obj = new Object();
  // obj自身函数
  obj.func = func;

  func();
  // true   等同于window.func()

  obj.func();
  // false  obj调用func

```

基于上面的栗子再进行扩展，更清晰的了解this此刻的指向

```javascript
  var hello = 'Global Hello';

  function func() {
    // console.info(this === window);
    console.info(this.hello);
  }

  var obj = new Object();
  obj.hello = 'Obj Hello';
  obj.func = func;

  func();
  // Global Hello

  obj.func();
  // Obj Hello

```

#### 印象加深
如果你能够正确识别以下栗子中this的指向，那么说明你已经对this有一定的了解。
> 请先尝试猜测以下this的指向，我会在最后对栗子进行说明。
