# ACL4SSR 远程开发者配置

## 个人需求记录

### 基础信息
- **职业**: 全职远程开发者
- **使用场景**: 开发环境 + 日常上网

### 常用服务
| 类型 | 服务 |
|------|------|
| AI 服务 | OpenAI (ChatGPT)、Claude Code、谷歌 AI |
| 搜索引擎 | Google |
| 通信工具 | Telegram |
| 虚拟货币 | 币安、Bybit、Ready、OKX |

### 特殊偏好
- ❌ 不喜欢频繁自动切换节点
- ✅ 虚拟货币 APP 需要走代理
- ✅ AI 服务稳定连接

## 配置说明

### 配置文件
- `RemoteDev_Config.ini` - 自定义远程开发配置
- `ACL4SSR_Online_Full_Google.ini` - 原始完整配置（备用）

### 配置特点
1. **减少自动测速频率**: 测速间隔改为 600 秒（原本 300 秒），减少节点切换
2. **简化代理组**: 移除不必要的分流组，保留核心功能
3. **AI 服务独立分组**: 手动选择节点，保证稳定性
4. **虚拟货币走代理**: 交易所相关流量走代理

### 代理组优先级
```
AI 服务 🤖 → 🇺🇲 美国节点 / 🇭🇰 香港节点
虚拟货币 💰 → 🇭🇰 香港节点 / 🇺🇲 美国节点
电报消息 📲 → 🇭🇰 香港节点 / 🇸🇬 狮城节点
谷歌 📢 → 🇺🇲 美国节点 / 🇭🇰 香港节点
```

## 使用方法

### 生成 Clash 配置
```bash
curl -s "http://127.0.0.1:25500/sub?target=clash&url=你的订阅链接&upload=false&config=配置URL" > clash.yml
```

### 本地订阅转换
```bash
# 使用自定义配置
curl -s "http://127.0.0.1:25500/sub?target=clash&url=你的订阅链接&upload=false&config=https://raw.githubusercontent.com/你的用户名/acl4ssr/master/RemoteDev_Config.ini" > clash.yml
```

### Docker 服务
```bash
# 启动
docker-compose up -d

# 查看日志
docker-compose logs -f

# 重启
docker-compose restart

# 停止
docker-compose down
```

## 推荐的节点选择策略

| 使用场景 | 推荐节点 |
|---------|---------|
| ChatGPT / Claude | 美国节点 |
| 谷歌搜索 | 美国/香港节点 |
| 虚拟货币交易所 | 香港节点（延迟低） |
| Telegram | 香港/新加坡节点 |
| Netflix/YouTube | 香港/新加坡节点 |

## 更新日志

| 日期 | 说明 |
|------|------|
| 2026-01-07 | 初始配置，基于 ACL4SSR Full_Google 规则精简 |
