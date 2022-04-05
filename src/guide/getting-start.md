
# 快速开始

**目前我们仍在公测中，部分功能尚不完善甚至会出现 Bugs 不过别担心，我们会修好的 😅**

**Pro Tips: 在页面底部可以切换网站语言哦 🤫**

**目前我们没有 Example 共各位开发者学习，我们推荐你们使用 Postman 来实验 🧪**

在快速开始使用 LumbaShark 之前，我们需要您注册一个您喜欢的提供商的开发者账户。或者注册成我们 SmartSheep Studio Cloud 官方的免费 LumbaShark 开发者成员，在官方提供的 LumbaShark 里您也可以收到我们官方举办的活动等其他同志，在 [此处](https://lumbashark.smartsheep.space/user/signup) 注册

注册完成账号后，在首页点击 [Become a Developer(成为开发者)](https://lumbashark.smartsheep.space/developer/signup)

以上完成了之后，你只需要访问 [Developer Center](https://lumbashark.smartsheep.space/developer) 点击 New(新建) 按钮，填写表单创建一个客户端，其中可用的 Scope(作用域) 如下:

1. `all` —— 全部权限 **(不推荐 我们会提示用户谨慎授权)**
2. `read:profile` —— 读取用户的 Email 和 Profile 属性，用于获取用户基本信息
3. `read:developer` —— 读取开发者的基本数据，包括客户端数据，统计数据等
4. `remove:developer` —— 删除开发者的客户端
5. `write:developer` —— 创建客户端等和开发者相关的数据

创建完成客户端之后你就可以在开发者中心发现多出了一个条目：

![Developer Center](https://s2.loli.net/2022/04/05/gqmNzWxtYk8dbAT.png)

**在 1.2.1 版本之后，创建成功客户端会弹出一个现实着 Client ID 与 Client Secret 的窗口出现，请保存下来 Client Secret，因为我们不会再次显示，也无法再次显示，因为 Secret 已被哈希加密**

点击客户端 ID 一栏的数据即可拷贝它。得会我们会用到。

打开 Postman，创建一个请求，您可以使用 `/api/authenticate/profile` 来获取用户信息，这个 API 十分适合测试获取 OAuth Access Token。

打开请求页面，转到「Authorization」并且在「Type」中选择 OAuth2，按照以下来填写配置

![Postman Screeshot](https://s2.loli.net/2022/04/05/MB9zk6N1YvFtTUc.png)

我们之前准备的 Client ID 和 Client Secret 在这就可以用到啦，正常填写完成之后，点击页面最下方的 Get New Access Token 按钮即可，之后 Postman 会打开一个页面让您输入您的用户名和密码来登陆，登陆之后点击 Grant access(授权) 按钮即可，之后 Postman 会打开一个确认页面，依次点击 「Processed」->「Use Token」按钮即可。

## 对比不同

使用 JWT Bearer 验证同样能获取到用户信息，接下来，让我们看看，这两个请求响应有什么区别

1. OAuth2 请求响应

```json
{
    "id": "cee7be2a-c522-4531-9a3c-91c978d7536a",
    "username": "LittleSheep",
    "email": "littlesheep.code@hotmail.com",
    "profile": {},
    "group_id": 1,
    "is_active": true,
    "is_locked": false,
    "created_at": "2022-04-05T09:12:56.000Z",
    "update_at": "2022-04-05T09:12:56.000Z",
    "client": {
        "id": "fa044e78-4558-4700-ad2b-9779e88406e1",
        "client_name": "Demo",
        "client_id": "28E3FD106108-4653-B184-080AA2CC6C06",
        "scope": "all",
        "developer_id": "cee7be2a-c522-4531-9a3c-91c978d7536a",
        "avatar": "https://s2.loli.net/2022/03/28/6hi3Ez8YCV5IG7w.png",
        "created_at": "2022-04-05T10:26:27.000Z",
        "updated_at": "2022-04-05T10:26:27.000Z"
    }
}
```

2. JWT Bearer 响应

```json
{
    "id": "cee7be2a-c522-4531-9a3c-91c978d7536a",
    "username": "LittleSheep",
    "email": "littlesheep.code@hotmail.com",
    "profile": {},
    "group_id": 1,
    "is_active": true,
    "is_locked": false,
    "created_at": "2022-04-05T09:12:56.000Z",
    "update_at": "2022-04-05T09:12:56.000Z",
}
```

可以很明显发现，一个拥有 `client` 属性，一个没有。

所以 OAuth2 Client 的访问令牌受到权限和 Scope(作用域) 限制，JWT Bearer 只受到权限限制。