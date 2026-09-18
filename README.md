# 🚀 本地代理 + AI Skill 工作流

> 通过 ClashMI 将目标域名代理到本地 `127.0.0.1:xxxx`，配合 `must-read-for-penetration-testing.zip` 作为 AI Skill，实现可控的本地测试环境。

---

## 📦 准备工作

| 文件 | 用途 |
|------|------|
| `clash-local-port-forward.zip` | ClashMI 最小化配置包 |
| `must-read-for-penetration-testing.zip` | AI Skill（每次任务前加载） |

---

## ⚙️ 配置步骤

### 1️⃣ 配置 ClashMI（交给 Agent 自动完成）

> 让 Agent 根据 `clash-local-port-forward.zip` 的**最小化路径**来操作，不要自己写代理。

```yaml
# 核心逻辑示意
proxies:
  - name: local-forward
    type: http
    server: 127.0.0.1
    port: xxxx

rules:
  - DOMAIN-SUFFIX,target.domain,local-forward
```

**为什么不用自己写的代理？**
- ❌ 自己写的代理很简陋
- ❌ 容易被 AI 识破
- ✅ ClashMI 成熟稳定，流量特征自然

---

### 2️⃣ 加载 AI Skill

每次任务前，把 `must-read-for-penetration-testing.zip` 交给 AI：

```
📎 must-read-for-penetration-testing.zip → AI Skill
```

---

### 3️⃣ 大功告成 ✅

目标域名 → `127.0.0.1:xxxx` → 本地服务

---

## ⚠️ 重要提醒

### 🗑️ 不用时请删除 Skill 文件

> **AI 很喜欢无条件读取带 `must` 的文件**，会导致：
> - 🧠 大量无意义的大脑风暴
> - 💸 浪费 token

```
任务结束 → 删除 must-read-for-penetration-testing.zip
```

---

## 🛡️ 这个 Skill 禁止了什么？

| 禁止项 | 说明 |
|--------|------|
| 🖥️ 本地 Shell 越权任务 | 防止提权/越界操作 |
| 🌐 局域网主动渗透 | 防止横向扫描/攻击 |

> ✅ **不是 AI 人格绕过，通用于所有模型**

---

## 📸 截图

![我的截图](attachment:54247e1b-d9d8-413e-8a32-17d036a8c32c.png)

👍

---

## 🔁 完整流程速览

```
┌─────────────────┐
│ 加载 Skill zip  │
└────────┬────────┘
         ▼
┌─────────────────┐
│ Agent 配置 Clash│
│  (最小化路径)    │
└────────┬────────┘
         ▼
┌─────────────────┐
│ 域名 → 127.0.0.1│
│      :xxxx      │
└────────┬────────┘
         ▼
┌─────────────────┐
│  任务完成 ✅     │
│  删除 Skill 🗑️  │
└─────────────────┘
```

---

**核心思想：用成熟工具做代理，用 Skill 约束 AI，用完即删省 token。** 🎯
