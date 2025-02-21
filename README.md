☁ **天翼云盘签到脚本** 🤖✨

---

### 🔑 账号配置 & 环境变量  
**路径**：  `Settings` → `Secrets and variables` → `Actions` → `Variables`  → `Environment variables`

在这里新建一个 `user`

在`Environment secrets`这里添加以下变量
| 变量名🐈             | 说明 📌                                                                 | 示例 🖼️                 |
|----------------------|-----------------------------------------------------------------------|-------------------------|
| `TY_ACCOUNTS`        | 账号密码组合，格式：`[{"userName":"账号","password":"密码"},...]`      | `[{"userName":"u1","password":"p1"},{"userName":"u2","password":"p2"}]` |
| `EXEC_THRESHOLD`     | 个人云和家庭云签到线程数（不填或者默认1就行，默认主号签到一次，小号签到10次）                                       | `1`                    |
| `FAMILYID`           | 家庭云ID抓取教程：[Alist文档](https://alist.nn.ci/zh/guide/drivers/189.html#%E5%AE%B6%E5%BA%AD%E8%BD%AC%E7%A7%BB)  | `123456`                |
| `WXPUSHER_UIDS`      | 微信推送UID（扫码获取）[二维码](https://wxpusher.zjiecode.com/api/qrcode/4Ix7noqD3L7DMBoSlvig3t4hqjFWzPkdHqAYsg8IzkPreW7d8uGUHi9LJO4EcyJg.jpg) | `UID_123`               |
| `WXPUSHER_APP_TOKEN`      | # wxpusher 的 appToken 官方文档: https://wxpusher.zjiecode.com/docs/ 管理后台: https://wxpusher.zjiecode.com/admin/(https://wxpusher.zjiecode.com/api/qrcode/4Ix7noqD3L7DMBoSlvig3t4hqjFWzPkdHqAYsg8IzkPreW7d8uGUHi9LJO4EcyJg.jpg) | ``               |

---
**如果EXEC_THRESHOLD不设置。或者设置为1。就主号签到一次个人跟家庭。其他号签到10次家庭。不签到个人。如果EXEC_THRESHOLD设置其他数字。所有号个人签到EXEC_THRESHOLD次数。家庭签到EXEC_THRESHOLD次数。TY_ACCOUNTS账密。跟群主格式一致FAMILYID家庭IDEXEC_THRESHOLD线程。不设置默认保号模式PUSH_PLUS_TOKEN推送
### 🚀 快速执行指南  
1️⃣ **启用Workflow**  
  ✅ 点击仓库顶部 `操作` → **`I understand my workflows, go ahead 和 enable them`**  

2️⃣ **触发运行**  
  🌟 给仓库点 **星标** 立即执行  

3️⃣ **定时任务**  
  ⏰ 每日 **北京时间 5:00** 自动签到  

---

### 🐉 青龙面板部署  
```bash
ql repo https://github.com/Aijiaobin/Cloud189Checkin.git "src|.env" "image" "src|.eslintrc.js|accounts.js|config.js|serverChan.js|telegramBot.js|wecomBot.js|wxPusher.js|.env" "main" "js" "rm -rf /ql/data/repo/wes-lin_Cloud189Checkin"
```

---
# 通知服务配置说明

## GOTIFY 通知
- **GOTIFY_URL**：Gotify 地址（如 `https://push.example.de:8080`）
- **GOTIFY_TOKEN**：Gotify 的消息应用 Token
- **GOTIFY_PRIORITY**：推送消息优先级（默认 `0`）

---

## go-cqhttp 通知
- **GOBOT_URL**：请求地址
  - 推送到个人 QQ：`http://127.0.0.1/send_private_msg`
  - 推送到群：`http://127.0.0.1/send_group_msg`
- **GOBOT_TOKEN**：go-cqhttp 配置的访问密钥
- **GOBOT_QQ**：
  - 若 `GOBOT_URL` 为 `/send_private_msg`，填写 `user_id=个人QQ`
  - 若为 `/send_group_msg`，填写 `group_id=QQ群`

---

## 微信 Server 酱通知
- **PUSH_KEY**：申请的 SCKEY

---

## PushDeer 通知
- **DEER_KEY**：PushDeer 的 KEY
- **DEER_URL**：PushDeer 的 URL（可选，默认 `https://api2.pushdeer.com/message/push`）

---

## Synology Chat 通知
- **CHAT_URL**：申请的 CHAT_URL
- **CHAT_TOKEN**：申请的 CHAT_TOKEN

---

## Bark App 通知
- **BARK_PUSH**：Bark 推送地址（如 `https://api.day.app/XXXXXXXX`）
- **BARK_ICON**：推送图标（仅 iOS15+ 生效）
- **BARK_SOUND**：推送铃声
- **BARK_GROUP**：消息分组（默认 `QingLong`）

---

## Telegram 机器人通知
- **TG_BOT_TOKEN**：Telegram Bot 的 Token
- **TG_USER_ID**：接收消息用户的 ID
- **TG_PROXY_HOST**：HTTP 代理主机地址
- **TG_PROXY_PORT**：HTTP 代理端口号
- **TG_PROXY_AUTH**：代理认证参数
- **TG_API_HOST**：Telegram API 反向代理地址（默认 `api.telegram.org`）

---

## 钉钉机器人通知
- **DD_BOT_TOKEN**：钉钉机器人 Webhook
- **DD_BOT_SECRET**：加签密钥（以 `SEC` 开头）

---

## 企业微信配置
### 基础设置
- **QYWX_ORIGIN**：反向代理地址（默认 `https://qyapi.weixin.qq.com`）

### 机器人通知
- **QYWX_KEY**：机器人 Webhook

### 应用消息通知
- **QYWX_AM**：依次填入 `corpid,corpsecret,touser(多成员用|隔开),agentid,消息类型（默认文本）`

---

## iGot 聚合推送
- **IGOT_PUSH_KEY**：iGot 推送 Key

---

## Push+ 设置
- **PUSH_PLUS_TOKEN**：一对一/多推送 Token
- **PUSH_PLUS_USER**：群组编码（一对多模式需填）

---

## Cool Push 设置
- **QQ_SKEY**：Cool Push 授权 Skey
- **QQ_MODE**：推送模式

---

## 智能微秘书设置
- **AIBOTK_KEY**：个人中心 API Key
- **AIBOTK_TYPE**：发送目标（`room` 或 `contact`）
- **AIBOTK_NAME**：目标名称（与类型对应）

---

## 飞书机器人设置
- **FSKEY**：飞书机器人 Key

---

## SMTP 邮件设置
- **SMTP_SERVER**：邮件服务器（如 `smtp.exmail.qq.com:465`）
- **SMTP_SSL**：是否启用 SSL（`true`/`false`）
- **SMTP_EMAIL**：收发件邮箱
- **SMTP_PASSWORD**：登录密码/特殊口令
- **SMTP_NAME**：收发件人姓名

---

## PushMe 通知
- **PUSHME_KEY**：PushMe 的 KEY
## WXPUSHER通知
- **WXPUSHER_APP_TOKEN:** '', // wxpusher 的 appToken
- **WXPUSHER_TOPIC_IDS: **'', // wxpusher 的 主题ID，多个用英文分号;分隔 topic_ids 与 uids 至少配置一个才行**
- **WXPUSHER_UIDS: **'', // wxpusher 的 用户ID，多个用英文分号;分隔 topic_ids 与 uids 至少配置一个才行

## 🙏 **特别鸣谢**  
- 原项目：[wes-lin/Cloud189Checkin](https://github.com/wes-lin/Cloud189Checkin)  
- README优化：[ShelbyAlan](https://github.com/ShelbyAlan) 💡  

## 交流群

![](https://cdn.jsdelivr.net/gh/wes-lin/Cloud189Checkin/image/group.jpg)

## [更新内容](https://github.com/wes-lin/Cloud189Checkin/wiki/更新内容)




# Cloud189Checkin

天翼网盘自动签到（随机容量），家庭空间签到（随机容量）。

# 重要说明！！！

请勿直接修改 .env，然后提交到 github，源码仓库是公开的，别人可以直接看到你的账号密码。因为错误使用本仓库导致账号密码泄漏，本人概不负责！！！

## **目录**

- [GitHub Action 运行](#GitHubAction运行)
- [本地运行](#本地运行)
- [其他环境集成](#其他环境集成)
- [交流群](#交流群)
- [更新内容](#更新内容)

## GitHub Action 运行

### Fork 此仓库

![](https://cdn.jsdelivr.net/gh/wes-lin/Cloud189Checkin/image/fork.png)

### 设置工作流权限

将 Settings -> Actions -> Workflow permissions 改成 Read and write permissions
![image](https://github.com/user-attachments/assets/28d27a78-73f2-489e-aa7e-cac87c0fc509)

### 设置账号密码

新版本的 git Action 需要创建 environment 来配合使用，创建一个名为 user 的环境。
![](https://cdn.jsdelivr.net/gh/wes-lin/Cloud189Checkin/image/env.png)
创建好后编辑 user 环境，添加变量 TY_ACCOUNTS, userName 和 password 为你的天翼账号和密码,可以添加多个账号如[{"userName":"账号 1","password":"账号 1 的密码"},{"userName":"账号 2","password":"账号 2 的密码"}]
![](https://cdn.jsdelivr.net/gh/wes-lin/Cloud189Checkin/image/accounts.jpg)

如果你遇到你账号密码中有特殊字符如#$等无法解析的[SyntaxError](https://github.com/wes-lin/Cloud189Checkin/issues/76),请在你的配置中将TY_ACCOUNTS用单引号包起来
例如'[{"userName":"1234567890","password":"123334#$#$"}]'

### 设置签到并发值

目前发现电信的签到, 在同时发送请求时, 能同时获取到奖励,这bug在个人和家庭的签到任务同样有生效. 但是这是具有一定风险性, 并且获取到奖励是不固定的,请谨慎使用.如果因为使用该脚本出现账号异常,本人概不负责. 设置环境变量 EXEC_THRESHOLD 默认是不开启, 默认签到执行一次,如设置建议并发数为5.
- `EXEC_THRESHOLD` 同时签到的最大进程数

### 设置家庭签到

目前电信的家庭签到可以将子账号的签到奖励叠加到主账号上,首先你需要把子账号都加入到你的主账号家庭组中,然后配置该环境变量.
- `TY_FAMILIES` 需要签到的主账号家庭名称,可以添加多个主账号如["18xxxxx","17xxxx"]
例如目前我的家庭组是18xxxxx,目前有三个账号,那么这个三个账号签到奖励都会汇集到主账号上, TY_FAMILIES 需要配置成["189xxxxx"],注意是你的家庭组的全名,我这里这是一个例子,因为客户端会将你名称打星号处理了,所以你要点app上的编辑家庭名称,来获取完整名称然后填到该变量上.
![](https://cdn.jsdelivr.net/gh/wes-lin/Cloud189Checkin/image/families.jpg)


### 设置推送

#### Server 酱

为了考虑到不同客户端兼容性,采用了 Server 酱,只需多配置下 SENDKEY
![](https://cdn.jsdelivr.net/gh/wes-lin/Cloud189Checkin/image/push.png)就行,Server 酱的配置和 sendkey 的获取可参看[Server 酱官网](https://sct.ftqq.com/)

#### TelegramBot 推送

- `TELEGRAM_BOT_TOKEN` _Telegram Bot Token_
- `TELEGRAM_CHAT_ID` _Telegram 接收推送消息的会话 ID_

#### 微信群机器人推送

- `WECOM_BOT_KEY ` _微信群机器人 webhook_
- `WECOM_BOT_TELPHONE ` _接收推送手机号_
  [群机器人配置说明](https://developer.work.weixin.qq.com/document/path/91770)

#### WxPusher 推送

- `WX_PUSHER_APP_TOKEN ` _WxPuser 推送 AppToken_
- `WX_PUSHER_UID ` _接收推送 UID_
  默认使用是我的 WxPusher,你也可以改成你自己 wxPusher 开发者账户,修改 WX_PUSHER_APP_TOKEN. 如果想直接使用我的 wxPush 应用,请扫描底下二维码进行关联.
  https://wxpusher.zjiecode.com/api/qrcode/4Ix7noqD3L7DMBoSlvig3t4hqjFWzPkdHqAYsg8IzkPreW7d8uGUHi9LJO4EcyJg.jpg
  然后拿到 UID 后,把 WX_PUSHER_UID 配成你拿到的 UID.
  ![](https://cdn.jsdelivr.net/gh/wes-lin/Cloud189Checkin/image/wxpusher.jpg)

#### pushPlus 推送

- `PUSH_PLUS_TOKEN ` _pushPlus 推送 token_
- 注册和获取 token：https://www.pushplus.plus/uc.html
- 拿到 token 后，把 PUSH_PLUS_TOKEN 配成你拿到的 token.
- 免费用户每天有 200 条推送额度

### 执行任务

1. 点击**Action**，再点击**I understand my workflows, go ahead and enable them**
2. 给自己仓库点个 start 或者修改任意文件后提交一次或者手动点击运行
   ![](http://tu.yaohuo.me/imgs/2020/06/34ca160c972b9927.png)
3. 每天早上 10:35 点执行任务

### 查看运行结果

Actions > Cloud check in action > build
![](https://cdn.jsdelivr.net/gh/wes-lin/Cloud189Checkin/image/action.png)

## 本地运行

### 环境配置

```
Node.js 18+
```

### 克隆项目

```bash
git clone https://github.com/wes-lin/Cloud189Checkin.git
```

```bash
cd Cloud189Checkin
```

### 安装依赖

```bash
npm install
```

### 运行

​ 修改源码中.env 中 userName 和 password 为你的天翼账号和密码,可以添加多个账号如[{"userName":"账号 1","password":"账号 1 的密码"},{"userName":"账号 2","password":"账号 2 的密码"}]

```bash
TY_ACCOUNTS=[{"userName":"userName","password":"password"}]
```

### 推送

修改 serverChan.js 或者添加环境变量 SENDKEY

执行命令

```bash
npm start
```

## 其他环境集成

我已经把天翼网盘的相关 API 集成到[SDK](https://github.com/wes-lin/cloud189-sdk)了，有编程能力的同学可以自行拓展，集成到自己的代码环境。

## 交流群

![](https://cdn.jsdelivr.net/gh/wes-lin/Cloud189Checkin/image/group.jpg)

## [更新内容](https://github.com/wes-lin/Cloud189Checkin/wiki/更新内容)
