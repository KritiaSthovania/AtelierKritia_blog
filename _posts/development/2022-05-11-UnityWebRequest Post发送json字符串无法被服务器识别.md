---
title: UnityWebRequest Post发送json字符串无法被服务器识别
Author: Yanxi Liu
category: Development
---

最近的一个需求需要用Unity调用某个平台的Rest API，各种尝试之后发现Post方法总是不好用，Get方法却没有问题，并且以及正确设置了Header。在各种尝试以及抓包对比之后发现是UnityWebRequest.Post方法的编码似乎有一些问题，传json格式的字符串进去后出来的也是一些奇怪的东西。（另外，Unity也无法自动将http转为https）。

解决方法有二，比较麻烦的一个是手动构建一个UploadHandler，用Encoding.UTF8手动编码一个json字符串。这里主要说一下另一种比较tricky的方法：先用UnityWebRequest.Put方法构建字符串，然后再把"method"设置成"POST"，如下所示：