# OpenClaw Feishu Plugin

飞书插件 for OpenClaw（适配 clawdbot 改名后的版本）

> **⚠️ 声明**：本项目是基于 [m1heng/clawdbot-feishu](https://github.com/m1heng/clawdbot-feishu) 的适配版本，仅做了名称迁移修改以支持 OpenClaw。感谢原作者 m1heng 的辛勤开发！

---

## 📋 原始项目信息

| 项目 | 链接 |
|------|------|
| **原作者** | [@m1heng](https://github.com/m1heng) |
| **原仓库** | [m1heng/clawdbot-feishu](https://github.com/m1heng/clawdbot-feishu) |
| **原 NPM 包** | [@m1heng-clawd/feishu](https://www.npmjs.com/package/@m1heng-clawd/feishu) |

---

## 🔧 修改说明

由于 [Clawdbot](https://github.com/clawdbot/clawdbot) 项目已更名为 [OpenClaw](https://github.com/openclaw/openclaw)，原插件无法直接使用。本仓库做了以下兼容性修改：

### 1. 配置文件重命名
```
clawdbot.plugin.json → openclaw.plugin.json
```

### 2. package.json 更新
- `clawdbot` 字段 → `openclaw` 字段
- `devDependencies` 中的 `clawdbot` → `openclaw`
- `peerDependencies` 中的 `clawdbot` → `openclaw`

### 3. 源码导入路径更新
将所有 `clawdbot/plugin-sdk` 导入更新为 `openclaw/plugin-sdk`：

| 文件 | 修改内容 |
|------|----------|
| `index.ts` | 导入路径和类型名 |
| `src/accounts.ts` | 导入路径和类型名 |
| `src/bot.ts` | 导入路径和类型名 |
| `src/channel.ts` | 导入路径和类型名 |
| `src/directory.ts` | 导入路径和类型名 |
| `src/media.ts` | 导入路径和类型名 |
| `src/monitor.ts` | 导入路径和类型名 |
| `src/onboarding.ts` | 导入路径和类型名 |
| `src/outbound.ts` | 导入路径和类型名 |
| `src/policy.ts` | 导入路径和类型名 |
| `src/reactions.ts` | 导入路径和类型名 |
| `src/reply-dispatcher.ts` | 导入路径和类型名 |
| `src/runtime.ts` | 导入路径和类型名 |
| `src/send.ts` | 导入路径和类型名 |
| `src/typing.ts` | 导入路径和类型名 |

### 4. 类型名更新
- `ClawdbotPluginApi` → `OpenclawPluginApi`
- `ClawdbotConfig` → `OpenclawConfig`

---

## 📦 安装方法

### 一行命令安装
```bash
cd /tmp && wget -q https://github.com/Shuai-DaiDai/openclaw-feishu-plugin/releases/download/v0.1.1-openclaw/m1heng-clawd-feishu-0.1.1.tgz && openclaw plugins install ./m1heng-clawd-feishu-0.1.1.tgz && openclaw gateway restart && rm ./m1heng-clawd-feishu-0.1.1.tgz && echo "✅ 飞书插件安装完成！"
```

### 手动安装
```bash
# 1. 下载插件包
wget https://github.com/Shuai-DaiDai/openclaw-feishu-plugin/releases/download/v0.1.1-openclaw/m1heng-clawd-feishu-0.1.1.tgz

# 2. 安装插件
openclaw plugins install ./m1heng-clawd-feishu-0.1.1.tgz

# 3. 重启加载插件
openclaw gateway restart
```

---

## ⚙️ 配置飞书

```bash
# 启用飞书频道
openclaw config set channels.feishu.enabled true

# 设置飞书应用 ID（在飞书开放平台获取）
openclaw config set channels.feishu.appId "cli_xxxxx"

# 设置飞书应用 Secret
openclaw config set channels.feishu.appSecret "your_app_secret"

# 设置域名（国内用 feishu，国际版用 lark）
openclaw config set channels.feishu.domain "feishu"

# 再次重启
openclaw gateway restart
```

---

## 📝 飞书应用配置

详细配置请参考原项目的文档：
https://github.com/m1heng/clawdbot-feishu#readme

### 所需权限
- `contact:user.base:readonly` - 获取用户信息
- `im:message` - 发送和接收消息
- `im:message.p2p_msg:readonly` - 读取私聊消息
- `im:message.group_at_msg:readonly` - 接收群聊@消息
- `im:message:send_as_bot` - 以机器人身份发送消息
- `im:resource` - 上传下载媒体文件

---

## 🙏 致谢

- 感谢 [@m1heng](https://github.com/m1heng) 开发原版的飞书插件
- 感谢 [OpenClaw](https://github.com/openclaw/openclaw) 项目提供的框架

---

## 📄 许可证

本项目遵循原项目的 MIT 许可证。

---

**免责声明**：本项目仅为适配 OpenClaw 的名称变更而创建，所有核心代码版权归原开发者所有。如原开发者要求，本仓库可随时删除或合并到原项目。
