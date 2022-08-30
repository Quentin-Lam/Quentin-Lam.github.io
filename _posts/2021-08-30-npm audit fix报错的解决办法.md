---
title: npm audit fix报错的解决办法
date: 2022-08-30 20:25:00 +0800
categories: [随笔]
tags: [Markdown插件]
pin: true
author: Quentin Lam

toc: true
comments: true
typora-root-url: ../../Quentin-Lam.github.io
math: false
mermaid: true
---

# 问题提出

用npm audit fix 安装包的更新时出现

```properties
➜   npm audit
npm ERR! code ENOLOCK
npm ERR! audit This command requires an existing lockfile.
npm ERR! audit Try creating one first with: npm i --package-lock-only
npm ERR! audit Original error: loadVirtual requires existing shrinkwrap file
```

# 解决方法

参考文章：https://stackoom.com/question/4R8gN#:~:text=npm%20i%20--package-lock-only%20%E5%8F%AA%E7%94%9F%E6%88%90%2F%E6%9B%B4%E6%96%B0,package-lock.json%20%E6%97%A0%E9%9C%80%E9%87%8D%E6%96%B0%E5%AE%89%E8%A3%85%EF%BC%9B%20npm%20i%20%E5%B0%86%E9%87%8D%E6%96%B0%E5%AE%89%E8%A3%85%E5%B9%B6%E7%94%9F%E6%88%90%E4%B8%80%E4%B8%AA%EF%BC%88%E5%9F%BA%E4%BA%8E%E6%82%A8%E7%9A%84%E9%85%8D%E7%BD%AE%EF%BC%89%E3%80%82



依次输入

```
npm i --package-lock-only
```

```
npm config get package-lock
```

```
npm config get shrinkwrap
```

```
npm i --package-lock-only
```

```
npm audit fix
```

解决，效果如图

![屏幕截图 2022-08-30 195842](/assets/blog_res/2021-08-30-npm%20audit%20fix%E6%8A%A5%E9%94%99%E7%9A%84%E8%A7%A3%E5%86%B3%E5%8A%9E%E6%B3%95.assets/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE%202022-08-30%20195842.png)

# 我本来想干啥

我想装个markdown的html生成插件（链接如下

https://github.com/azu/mdline

![image-20220830203348877](/assets/blog_res/2021-08-30-npm%20audit%20fix%E6%8A%A5%E9%94%99%E7%9A%84%E8%A7%A3%E5%86%B3%E5%8A%9E%E6%B3%95.assets/image-20220830203348877.png)

主要是这个时间流的效果很让我心动，然后我先在这里

https://nodejs.org/en/download/

装了node.js，然后通过`npm`安装插件：

```
npm install --global mdline
```

然后就出现了这个诡异的更新提示（其实可以不管），但只要你跟着他的提示走，你就会发现开头提出的问题，很烦。于是我浅搜了一下网上的方法，发现放在一个很偏的位置，就贴在这里（没准我的博客更偏，但也算是能搜到吧）

![image-20220830203859543](/assets/blog_res/2021-08-30-npm%20audit%20fix%E6%8A%A5%E9%94%99%E7%9A%84%E8%A7%A3%E5%86%B3%E5%8A%9E%E6%B3%95.assets/image-20220830203859543.png)

