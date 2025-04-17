# 使用Claw云平台部署自己的官方QQ机器人

## 目录
- [前言](#前言)
- [准备工作](#准备工作)
- [注册账号](#注册账号)
- [部署容器](#部署容器)
- [配置QQ机器人](#配置qq机器人)
- [添加大模型服务](#添加大模型服务)
- [添加百度地图的MCP服务（高级可选玩法）](#添加百度地图的mcp服务高级可选玩法)
- [总结](#总结)
- [致谢](#致谢)

## 前言

本教程将指导您如何使用[Claw云平台](https://run.claw.cloud/)来部署自己的官方QQ机器人。

## 准备工作

在开始之前，您需要准备以下内容：

- 一个谷歌账户或GitHub账号（推荐使用GitHub账号，根据官方的策略，使用180天以上的GitHub账号可以每月免费获得5美元的额度，不需要绑卡）
- 各大平台的API密钥
- 百度地图的apikey（MCP服务，可选）

## 注册账号

1. 点击以下链接进行注册（带有aff）：
   [https://console.run.claw.cloud/signin?link=7D47LG72PBLB](https://console.run.claw.cloud/signin?link=7D47LG72PBLB)

![注册页面](https://opaoai.com/upload/thumbnails/2025/w1600/image-lckC.png)

## 部署容器

1. 注册好之后，点击**app启动** --- 然后点击**创建app**
![应用创建](https://opaoai.com/upload/thumbnails/2025/w1600/image-kfyd.png)
![应用创建页面](https://opaoai.com/upload/1744892849405.jpg)
2. 修改镜像为：`soulter/astrbot:latest`  
2.1 应用名称可以根据自己的喜欢自定义，方便区分不同的容器  
2.2 镜像选择public，修改镜像名称为`soulter/astrbot:latest`  
![镜像配置](https://opaoai.com/upload/1744892960253.jpg)
3. 可以选择fixed，容器数量选择1个就够了。剩下的cpu和memory可以根据自己的需求选择。对于轻量使用，默认的即可满足运行要求。
![资源配置](https://opaoai.com/upload/image-CQkN.png)
4. 打开容器外部访问，新增两个容器端口：6185和6196，同时打开容器端口外部访问
   （可以自定义多个端口，如果需要同时部署多个机器人）
   
   ![端口配置](https://opaoai.com/upload/image-GYPF.png)
   
5. 添加必要的环境变量和文件存储  
   如下图所示，添加`TZ=Asia/Shanghai`的环境变量   
   添加`/AstrBot/data`的本地存储
   ![环境变量配置](https://opaoai.com/upload/image-gYvc.png)
   
6. 最后点击右上角的"部署"按钮即可
    ![部署按钮](https://opaoai.com/upload/image-jHvl.png)

## 配置QQ机器人

1. 点击打开6185对应的域名--如上图1所示的位置，选择public所对应的域名
   ![登录界面](https://opaoai.com/upload/image-vIHl.png)
   
2. 使用默认的账户密码登入（用户名和密码都是`astrbot`）
![登录界面](https://opaoai.com/upload/image-ImxO.png)
3. 点击"消息平台"，添加一个新的QQ机器人账号
   
   ![消息平台配置](https://opaoai.com/upload/thumbnails/2025/w1600/QQ1744718145531.png)
   
4. 选择"QQ官方"，"webhook类型"
   
   ![选择机器人类型](https://opaoai.com/upload/image-YHzq.png)
   
5. 填写QQ机器人的ID和密钥

  （关于机器人申请和密钥查看，请参考：[申请qqbot](https://bot.q.qq.com/wiki/#_3-%E4%B8%AA%E4%BA%BA%E4%B8%BB%E4%BD%93%E5%85%A5%E9%A9%BB)，[查看id和密钥](https://q.qq.com/qqbot/#/developer/developer-setting) ）
  ![机器人ID配置](https://opaoai.com/upload/image-RBXK.png)
  ![机器人密钥配置](https://opaoai.com/upload/image-MfRa.png)

6. 启动机器人后，回到QQ机器人平台
7. 导航到[**开发--回调配置**](https://q.qq.com/qqbot/#/developer/webhook-setting)
![回调配置](https://opaoai.com/upload/image-biUI.png)
8. 勾选所有四个事件，然后确认配置
9. 填写回调地址：`<你的域名>/astrbot-qo-webhook/callback`
   （这里的域名是指第二个端口6196对应的域名）

10. 回到qq机器人平台，查看你的日志，如果不出意外，应该会显示你的qqbot登录成功
![成功登录](https://opaoai.com/upload/image-vjYn.png)

额外配置：
如果第十步显示你的qqbot没有启动成功，显示不在白名单，那么，你需要使用[itdog](https://www.itdog.cn/)，ping一下你的域名，获取你的IP地址，然后将所获得的地址，填写如qqbot平台的白名单IP地方
![白名单配置](https://opaoai.com/upload/image-dGsb.png)

## 添加大模型服务

1. 根据自己拥有的API添加一个大模型服务
![AI模型配置](https://opaoai.com/upload/image-lQAN.png)
2. 配置完成后，重启服务
3. 等待3-5分钟，机器人就可以开始对话了
![对话示例](https://opaoai.com/upload/thumbnails/2025/w1600/b4979ea683925e973911b5c70a194e15.png)

## 添加百度地图的MCP服务（高级可选玩法）

1. 你需要在[百度地图开放平台](https://lbsyun.baidu.com/apiconsole/key)的控制台中创建一个服务端AK，通过AK你才能够调用百度地图API能力。
2. 去百度地图mcp的[开源仓库](https://github.com/baidu-maps/mcp/tree/main/src/baidu-map/python)，下载源代码
3. 将你下载的源代码，上传到你的claw云容器平台
![文件上传](https://opaoai.com/upload/image-yFpl.png)
![代码上传](https://opaoai.com/upload/image-pycL.png)
4. 回到你的qqbot平台，导航到 控制台，点击pip安装，安装UV库
![UV安装](https://opaoai.com/upload/image-qNFV.png)
5. 导航到MCP，选择右上角的新增服务器，填入下述配置
```
{
  "mcpServers": {
    "baidu-map": {
      "command": "uv",
      "args": [
        "mcp[cli]",
        "mcp",
        "run",
        "{YOUR_PATH}/mcp_server_baidu_maps/map.py"
      ],
      "env": {
        "BAIDU_MAPS_API_KEY": "<YOUR_API_KEY>"
      }
    }
  }
}
```

> **注意**：请将 `{YOUR_PATH}` 替换为您上传百度地图 MCP 服务代码的实际路径，并将 `<YOUR_API_KEY>` 替换为您在百度地图开放平台获取的 API Key。

6. 点击"启动"按钮，开始运行你的 MCP 服务。启动成功后，你的 QQ 机器人将具备查询地图、规划路线等地理位置服务能力。


## 总结

通过本教程，您已经成功：
- 在 Claw 云平台部署了自己的官方 QQ 机器人
- 配置了基础的聊天功能
- 添加了 AI 大模型支持
- 可选择性地配置了百度地图 MCP 服务增强功能

关于更多配置和插件的使用，可以在 QQ 交流群中与其他用户交流经验。

## 致谢

我要向Claw云平台表示诚挚的感谢，感谢其提供免费服务，使这样的项目成为可能。同时，特别感谢所有开源贡献者，他们的工作构成了AstrBot等工具和相关服务的基础。

更多开源项目和教程，请访问：[https://github.com/ClawCloud/Run-Blog](https://github.com/ClawCloud/Run-Blog)

祝您使用愉快！
