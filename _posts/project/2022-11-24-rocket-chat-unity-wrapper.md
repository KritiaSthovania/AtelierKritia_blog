---
title: Rocket.Chat Unity Wrapper
Author: Yanxi Liu
category: Project
---



Rocket.Chat 是一款类似Slack, Teams等的即时通讯软件，但是它是开源的，只不过需要自己搭建服务器。前段时间组内从Slack迁移到了Rocket.Chat（因为Slack免费版不能保存以前的消息记录），需要一个在Unity中和Rocket.Chat通讯的插件，于是我便开发了这个Rocket.Chat Client插件，或者说一个Wrapper，主要使用了UnityWebRequest来包装REST API以及用WebSocket进行订阅。中间也遇到了一些坑，比如在[这篇文章](https://yanxi-kritia.com/development-troubleshooting/unity/unitywebrequest-post%e5%8f%91%e9%80%81json%e5%ad%97%e7%ac%a6%e4%b8%b2%e6%97%a0%e6%b3%95%e8%a2%ab%e6%9c%8d%e5%8a%a1%e5%99%a8%e8%af%86%e5%88%ab/)中提到的UnityWebRequest初始化的一些问题。此外还有UnityWebRequest并不能自动将Http跳转到Https，需要注意。

这个Wrapper已经被合并到了i5-Toolkit-for-Unity中，具体文档可以在[这里](https://rwth-acis.github.io/i5-Toolkit-for-Unity/1.8.1/manual/RocketChat-Client.html)找到。考虑到使用频率，Rocket.Chat Client提供了直接进行登录、发送消息、接收（订阅）消息流、获取公开或私人的Channel，Group，Team的方法，此外也提供了可以直接调用任意Rocket.Chat API的通用方法，包括REST API和基于WebSocket的Realitm API。