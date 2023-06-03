---
title: Unity 报错：”Should not be capturing when there is a hotcontrol”，EditorWindow无法打开
Author: Yanxi Liu
category: Development
---

这个应该是Unity一个十分奇怪的报错了，报错原因很奇怪，并且十分难以定位（Unity里这种报错还不少），这里只提一下我遇到的情况。

今天在写一些关于EditorWindow的东西的时候，发现如果在打开EditorWindow的时候报错了，修改完后再打开的时候会提示如题的Warning，并且直接导致EditorWindow无法打开。这个报错可能在更改脚本的名字后也会出现，原因可能是尽管报错，Unity仍会打开一个这个Window，然后由于每个EditorWindow本身只允许同时存在一个实例，导致无法打开新的EditorWindow。在`Window/Panels`中也可以看到有这个Window，但是无法选中也无法关闭。

针对这个报错我目前没有发现很好的解决办法，比较直接的解决办法是复制一下对应脚本，然后删除它，再创建一个一模一样的脚本。另一种方法是可以保存一下常用的的`Layout（Window/Layout）`，然后报错后重新应用一下，这样也可以强制关闭不在Layout中的Window，当然前提是保存的Layout里没有打开这个报错的Window。