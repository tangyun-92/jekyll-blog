---
layout: post
title: "vue+axios将后端返回的图片流显示到img中"
categories: [Vue, Axios]
description: ""
keywords: "Vue, Axios"
---

```js
 axios.get("接口地址", {
   responseType: "arraybuffer",
   params: 传给后端的数据
 })
   .then(response => {
   return (
     "data:image/png;base64," +
     btoa(
       new Uint8Array(response.data).reduce(
         (data, byte) => data + String.fromCharCode(byte),
         ""
       )
     )
   )
 })
   .then(data => {
   this.imgUrl = data; //赋值给img标签的src属性
 })
```