# 介绍

LumbaShark 是一个开发者友好的基于 OAuth2 第三方授权服务系统，您只需要注册成我们的开发者以及注册客户端就可以简单的使用我们的服务啦。本次文档我们会从 0 到 1 手把手的教你如何使用我们的服务 😉

## 什么是第三方授权服务

第三方授权服务是指您无需在一个网站上注册以用户名和密码为授权方式的应用，而是在别的您信任的网站上注册账号，在目标网站上支持您信任的网站的授权，这样您就可以使用您信任的网站的用户无需注册也能使用目标网站的服务了。

当然这么解释十分迷糊，我们以 StackOver Flow 举例

![CleanShot 2022-04-05 at 15.10.17@2x.png](https://s2.loli.net/2022/04/05/Nf4i8SGyQEIMAOm.png)

图中所指的就是第三方是授权系统，三个熟知的 404 网站下面的就是第一方授权系统，也就是用户名密码。

我们的 LumbaShark 就是这样的授权系统。