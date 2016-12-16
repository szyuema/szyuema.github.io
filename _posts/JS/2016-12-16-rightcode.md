---
layout: post
title: 消除魔术字符串
keywords: JS
category : JS
tags : [JS]
---

魔术字符串实例
>魔术字符串指的是，在代码之中多次出现、与代码形成强耦合的某一个具体的字符串或者数值。
>风格良好的代码，应该尽量消除魔术字符串，该由含义清晰的变量代替。

``` javascript
function getArea(shape, options) {
  var area = 0;

  switch (shape) {
    case 'Triangle': // 魔术字符串
      area = .5 * options.width * options.height;
      break;
    /* ... more code ... */
  }

  return area;
}

getArea('Triangle', { width: 100, height: 100 }); // 魔术字符串
```

>上面代码中，字符串“Triangle”就是一个魔术字符串。它多次出现，与代码形成“强耦合”，不利于将来的修改和维护。

>常用的消除魔术字符串的方法，就是把它写成一个变量。

改进

>我们把“Triangle”写成shapeType对象的triangle属性，这样就消除了强耦合。

```javascript

var shapeType = {
  triangle: 'Triangle'
};

function getArea(shape, options) {
  var area = 0;
  switch (shape) {
    case shapeType.triangle:
      area = .5 * options.width * options.height;
      break;
  }
  return area;
}

getArea(shapeType.triangle, { width: 100, height: 100 });

```

