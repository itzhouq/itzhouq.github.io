---
layout: post
title: "MacM1 安装 OpenClaw完全指南：从踩坑到飞书机器人上线"
subtitle: "MacM1 安装 OpenClaw完全指南：从踩坑到飞书机器人上线"
date: 2026-03-01
author: "风飞扬itzhouq"
header-/img: "/img/post-bg-2015.jpg"
tags: [openclaw]
---

过了个年的功夫，又是 Seedance 又是 Openclaw，AI 的变化太快了。

不过，对于新技术我一向是谨慎乐观，不追工具但注重 AI 提效和产品落地。

未来尝试将一些网站落地、文案编写、方案调研、数据整理、咨询信息收集等工作交给Openclaw 来完成或者解决80%，提高我个人的效率。
*ˆ*
我使用一周下来，感觉确实提效很多，也有一些经验玩法。

这里把使用的经验记录下来，如果能帮到你可以点赞收藏。

全民 AI 时代，自己动手尝试解决一些手头的小事，比陷入 AI 焦虑更有智慧。

![](/img//in-post/MacM1%20安装%20OpenClaw完全指南：从踩坑到飞书机器人上线/file-20260228223417232.png)
下面开始正式的教程记录。
## 一、OpenClaw 是什么？

简单说，**OpenClaw 是一个开源的 AI Agent 框架**，让你可以：

- 🤖 部署自己的 AI 助手（支持多种大模型）
- 💬 接入多种渠道（飞书、钉钉、Telegram、Slack 等）
- 🛠️ 调用各种工具（文件操作、浏览器控制、代码执行）
- ⏰ 设置定时任务（自动备份、定时检查）

相比直接用 ChatGPT，OpenClaw 的优势是**数据私有化**+**功能可扩展**。
![](/img//in-post/MacM1%20安装%20OpenClaw完全指南：从踩坑到飞书机器人上线/file-20260301004350795.png)

#  二、前置准备

## 2.1 确保你的 Mac M1 已安装：

```bash
# 检查 Node.js（需 v18+）
node --version

# 检查 npm
npm --version

# 建议安装 Homebrew（如果还没有）
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

**⚠️ M1 特别提醒**：部分工具可能需要 Rosetta 2
```bash
softwareupdate --install-rosetta
```

## 2.2 模型服务商
国内推荐 kimi 、Minimax、GLM 的 coding plan 自行付费购买。claude code 和 openclaw 通用（注意各家政策有所差别，自行选购）。
# 三、安装 OpenClaw
使用[官网](https://openclaw.ai/)安装命令：`curl -fsSL https://openclaw.ai/install.sh | bash`复制到终端执行。
![](/img//in-post/MacM1%20安装%20OpenClaw完全指南：从踩坑到飞书机器人上线/file-20260228223902190.png)
按照提示选择对应选项。
![](/img//in-post/MacM1%20安装%20OpenClaw完全指南：从踩坑到飞书机器人上线/file-20260228224057237.png)
模型我这里选择的是 kimi 的 Coding Plan 模型。
![](/img//in-post/MacM1%20安装%20OpenClaw完全指南：从踩坑到飞书机器人上线/file-20260228225125230.png)
通道这里先不选择，等下openclaw 安装成功让 AI 自动帮我们完成配置更简单。
![](/img//in-post/MacM1%20安装%20OpenClaw完全指南：从踩坑到飞书机器人上线/file-20260228225709095.png)
![](/img//in-post/MacM1%20安装%20OpenClaw完全指南：从踩坑到飞书机器人上线/file-20260228225810437.png)

马上成功了。
![](/img//in-post/MacM1%20安装%20OpenClaw完全指南：从踩坑到飞书机器人上线/file-20260228230121210.png)
选择网络浏览器打开
![](/img//in-post/MacM1%20安装%20OpenClaw完全指南：从踩坑到飞书机器人上线/file-20260228230210880.png)
如果你能到到这里说明你的机器人已经完成安装成功了，你可以在浏览器中和机器人对话，完成了目标的一大半。
![](/img//in-post/MacM1%20安装%20OpenClaw完全指南：从踩坑到飞书机器人上线/file-20260228230452523.png)

# 四、安装飞书机器人
下面就是通过对话的方式开始指挥机器人帮你安装飞书机器人，不需要你自己手动配置，手动改配置文件，操作不方便还容易出错。
机器人收到指示开始干活：
![](/img//in-post/MacM1%20安装%20OpenClaw完全指南：从踩坑到飞书机器人上线/file-20260228230650455.png)
安装过程 AI 机器人会自动修复一些问题（后面还有别的问题）。
![](/img//in-post/MacM1%20安装%20OpenClaw完全指南：从踩坑到飞书机器人上线/file-20260301000513569.png)
到这一步如果没有报错可以开始在飞书开放平台新建机器人。

#  五、配置飞书机器人
打开飞书开放平台：https://open.feishu.cn/app?lang=zh-CN新建自建应用。
![](/img//in-post/MacM1%20安装%20OpenClaw完全指南：从踩坑到飞书机器人上线/file-20260301000818057.png)
名称随便写。
![](/img//in-post/MacM1%20安装%20OpenClaw完全指南：从踩坑到飞书机器人上线/file-20260301000912394.png)
进入应用后，点击左侧凭证与基础信息，复制 appId 和 AppSecret 等一会儿使用。
![](/img//in-post/MacM1%20安装%20OpenClaw完全指南：从踩坑到飞书机器人上线/file-20260301001150408.png)
点击添加机器人：
![](/img//in-post/MacM1%20安装%20OpenClaw完全指南：从踩坑到飞书机器人上线/file-20260301001305686.png)

点击权限管理，点击批量导入/导出权限，复制下面的 json 进去（原有默认值被覆盖）：
```json
{
  "scopes": {
    "tenant": [
      "aily:file:read",
      "aily:file:write",
      "application:application.app_message_stats.overview:readonly",
      "application:application:self_manage",
      "application:bot.menu:write",
      "cardkit:card:write",
      "contact:contact.base:readonly",
      "contact:user.base:readonly",
      "contact:user.employee_id:readonly",
      "corehr:file:download",
      "docs:document.content:read",
      "event:ip_list",
      "im:chat",
      "im:chat.access_event.bot_p2p_chat:read",
      "im:chat.members:bot_access",
      "im:chat:read",
      "im:message",
      "im:message.group_at_msg:readonly",
      "im:message.group_msg",
      "im:message.p2p_msg:readonly",
      "im:message:readonly",
      "im:message:send_as_bot",
      "im:resource",
      "sheets:spreadsheet",
      "wiki:wiki:readonly"
    ],
    "user": [
      "aily:file:read",
      "aily:file:write",
      "contact:contact.base:readonly",
      "im:chat.access_event.bot_p2p_chat:read"
    ]
  }
}
```
![](/img//in-post/MacM1%20安装%20OpenClaw完全指南：从踩坑到飞书机器人上线/file-20260301001527377.png)
点击确认。
接着点击左侧版本管理发布，创建版本。
![](/img//in-post/MacM1%20安装%20OpenClaw完全指南：从踩坑到飞书机器人上线/file-20260301001809907.png)
版本号和版本说明按照 1.0.1、1.0.2 这样的格式写，可以多次发布，每次版本号递增就行。
![](/img//in-post/MacM1%20安装%20OpenClaw完全指南：从踩坑到飞书机器人上线/file-20260301001917930.png)
点击保存：
![](/img//in-post/MacM1%20安装%20OpenClaw完全指南：从踩坑到飞书机器人上线/file-20260301001944194.png)
确认发布。
![](/img//in-post/MacM1%20安装%20OpenClaw完全指南：从踩坑到飞书机器人上线/file-20260301002007432.png)
发布完后可以把刚刚复制出来的 appId 和 Appsecret 发给 AI 让他帮你配置。
![](/img//in-post/MacM1%20安装%20OpenClaw完全指南：从踩坑到飞书机器人上线/file-20260301002232626.png)
这个过程 AI 会自动从起网关，需要等待一会儿。如果报错，可以优先让机器人自查自修。
![](/img//in-post/MacM1%20安装%20OpenClaw完全指南：从踩坑到飞书机器人上线/file-20260301002804100.png)
![](/img//in-post/MacM1%20安装%20OpenClaw完全指南：从踩坑到飞书机器人上线/file-20260301002846459.png)
如果机器人无法自行修复，可以新开一个终端 terminal 查看日志：
![](/img//in-post/MacM1%20安装%20OpenClaw完全指南：从踩坑到飞书机器人上线/file-20260301002936759.png)
如果看到有类似 error 的关键词，可以复制关键信息给大模型比如千问、豆包等模型排查。
![](/img//in-post/MacM1%20安装%20OpenClaw完全指南：从踩坑到飞书机器人上线/file-20260301003216635.png)
![](/img//in-post/MacM1%20安装%20OpenClaw完全指南：从踩坑到飞书机器人上线/file-20260301003231366.png)
![](/img//in-post/MacM1%20安装%20OpenClaw完全指南：从踩坑到飞书机器人上线/file-20260301003243740.png)
![](/img//in-post/MacM1%20安装%20OpenClaw完全指南：从踩坑到飞书机器人上线/file-20260301003254524.png)
我这里就是飞书插件冲突并且然后我告诉机器人我只需要一个 openclaw 原生插件就行，帮我修复。我没有手动改配置。
这里有几个命令可以记录下，查看 openclaw 网关服务状态的，用来判断 openclaw 是否启动。

```bash
# 检查状态
openclaw gateway status

# 启动服务
openclaw gateway start

# 验证
openclaw gateway status
```
好了到这一个可能以为对接飞书完成了，但是给飞书机器人发消息发现他不是装死就是报错。
![](/img//in-post/MacM1%20安装%20OpenClaw完全指南：从踩坑到飞书机器人上线/file-20260301003644401.png)
那就需要在事件与回调中增加配置，通过长连接方式订阅：
![](/img//in-post/MacM1%20安装%20OpenClaw完全指南：从踩坑到飞书机器人上线/file-20260301003753464.png)
回调配置也需要：
![](/img//in-post/MacM1%20安装%20OpenClaw完全指南：从踩坑到飞书机器人上线/file-20260301003839083.png)
再走一遍发版流程。飞书中跟机器人打招呼成功。
![](/img//in-post/MacM1%20安装%20OpenClaw完全指南：从踩坑到飞书机器人上线/file-20260301003932632.png)
后续就可以完美的在手机上指挥龙虾了。

# 六、备份（可选）
为了防止配置丢失，可以在 codeup 或者github 私有仓库做备份。![](/img//in-post/MacM1%20安装%20OpenClaw完全指南：从踩坑到飞书机器人上线/file-20260301004143266.png)

好了到了这里，你已经强得可怕。

OpenClaw 更新非常快，任何教程可能都会迅速过时，但是只要学会了如何指挥 AI + 尝试看报错信息。你基本都可以在一到两个小时内完成。

未来，一人公司，一定会大爆发，人和人的差距在于行动力。

当下 AI 可能还不够智能，但是 AI 时代下会使用工具和不会使用工具的人 ，会有十倍百倍的差距。

如果我的文章对你有所帮助，不要忘记点个赞支持一下。

