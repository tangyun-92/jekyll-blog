---
layout: post
title: "将一个数组的value作为另一个数组的key"
categories: [Javascript]
description: ""
keywords: "数据, Javascript"
---



```js

let arr = [
    {
        "productAttributeId": 2,
        "value": "白色",
        "name": "color"
    },{
        "productAttributeId": 2,
        "value": "黑色",
        "name": "color"
    },{
        "productAttributeId": 5,
        "value": "M",
        "name": "size"
    },{
        "productAttributeId": 5,
        "value": "X",
        "name": "size"
    },{
        "productAttributeId": 5,
        "value": "L",
        "name": "size"
    },
]
// 转换成多维数组
function getMultidimensional(arr) {
  const data = {};
  arr.forEach((item) => {
    const list = data[item.name] || [];
    list.push(item);
    data[item.name] = list;
  });
  return Object.keys(data).map((key) => data[key]);
}

// 求笛卡尔积
function getCartesianProduct(array) {
  if (!Array.isArray(array)) return [[]]; // 判断数组
  array = array.filter((_) => _.length > 0); // 清除数组里面的空数组
  if (array.length < 2) return array; // 数组少于两个 GG
  const list1 = array.splice(0, 1)[0]; // 取出第一个
  const list2 = array.splice(0, 1)[0]; // 取出第二个
  const list = [];
  list1.forEach((_list1) => {
    list2.forEach((_list2) => {
      if (_list1.name) {
        list.push({
          [_list1.name]: _list1.value,
          [_list2.name]: _list2.value,
        });
      } else {
        list.push({
          ..._list1,
          [_list2.name]: _list2.value,
        });
      }
    });
  });
  return getCartesianProduct([list].concat(array));
}
const list = getCartesianProduct(getMultidimensional(arr))
console.log(list)
```

![array.png](/images/posts/2020-10-12-value-to-key.png)