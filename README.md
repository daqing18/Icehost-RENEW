# Icehost-RENEW
## ⚙️ 环境变量配置 (GitHub Secrets)

本项目依赖 GitHub Actions 自动运行，请在 Fork 或新建仓库后，进入仓库的 **Settings** -> **Secrets and variables** -> **Actions** -> **New repository secret**，依次添加以下 4 个环境变量：

| 变量名 (Name) | 说明与获取方式 (Secret) | 必填 |
| :--- | :--- | :---: |
| `ICEHOST_SERVER_URL` | **目标服务器面板地址**<br>登录 IceHost 后，进入能看到“续期/延长 6 小时”按钮的具体服务器页面，复制浏览器地址栏的完整链接。<br>*(示例: `https://dash.icehost.pl/server/xxxx`)* | ✅ |
| `ICEHOST_COOKIES` | **免登录身份凭证**<br>1. 浏览器登录 IceHost 面板并进入服务器页。<br>2. 按 `F12` 打开开发者工具，切换到 **Network (网络)** 标签页，按 `F5` 刷新。<br>3. 点击列表中的网页请求（如 `dash.icehost.pl`），在右侧找到 **Request Headers (请求头)**。<br>4. 复制 `cookie:` 后面完整的一长串字符（通常包含 `icehostpl_session=...`）。<br>*(注：脚本已做兼容，支持完整 Cookie 字符串或 JSON 格式注入)* | ✅ |
| `TG_BOT_TOKEN` | **Telegram 机器人 Token**<br>用于接收续期成功、失效或验证码盾的截图通知。在 TG 中向 `@BotFather` 发送 `/newbot` 申请获取。<br>*(示例: `1234567890:ABCDefghIJKLmnop...`)* | ❌ (可选) |
| `TG_CHAT_ID` | **Telegram 接收账号 ID**<br>你的个人 TG 账号 ID。在 TG 中向 `@userinfobot` 发送 `/start` 获取 `Id` 字段的纯数字。<br>*(示例: `123456789`)* | ❌ (可选) |

> **⚠️ 注意事项**：
> - 如果不配置 `TG_BOT_TOKEN` 和 `TG_CHAT_ID`，脚本依然会正常执行保活操作，只是不会发送 Telegram 通知。
> - 若运行失败，可前往 Actions 运行日志的 **Artifacts** 中下载 `icehost_debug_screenshot.png` 截图进行排错。
