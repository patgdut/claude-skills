---
name: chrome-browser
description: >
  This skill should be used when the user asks to "search the web", "Google search", "browse website", "open URL in browser", "analyze webpage", "research online", or needs real-time web information that WebFetch cannot access (e.g., dynamic content, JavaScript-rendered pages, or sites requiring browser interaction).
version: 1.0.0
user_invocable: true
---

# Chrome Browser Skill

通过 Chrome DevTools Protocol (CDP) 控制浏览器进行网页搜索和分析。

## 使用场景

- 需要搜索实时网络信息
- 分析 JavaScript 渲染的动态页面
- WebFetch 无法访问的内容
- 需要浏览器交互的场景

## 前置依赖

### 检查并安装依赖

```bash
# 检查 Python3
which python3 || echo "需要安装 Python3: brew install python3"

# 检查 websockets 库
python3 -c "import websockets" 2>/dev/null || pip3 install websockets

# 检查 Chrome 浏览器
ls /Applications/Google\ Chrome.app || echo "需要安装 Google Chrome"
```

## 操作步骤

### 1. 启动 Chrome 远程调试模式

```bash
# 检查是否已有 Chrome 调试实例运行
lsof -i :9222

# 如果没有，启动 Chrome（后台运行）
/Applications/Google\ Chrome.app/Contents/MacOS/Google\ Chrome --remote-debugging-port=9222 --no-first-run --no-default-browser-check &
```

### 2. 获取调试目标

```bash
# 获取可用的调试页面列表
curl -s http://localhost:9222/json
```

### 3. 创建新标签页

```bash
# 打开新标签页并导航到 Google（注意：需要用 PUT 方法）
curl -s -X PUT "http://localhost:9222/json/new?https://www.google.com"
```

### 4. 执行 Google 搜索

```bash
# 直接打开搜索结果页
curl -s -X PUT "http://localhost:9222/json/new?https://www.google.com/search?q=YOUR_SEARCH_QUERY"
```

### 5. 获取页面内容

使用 Python + websockets 获取页面文本：

```bash
python3 << 'EOF'
import asyncio, json, websockets

async def get_page_content(page_id):
    ws_url = f"ws://localhost:9222/devtools/page/{page_id}"
    async with websockets.connect(ws_url) as ws:
        await ws.send(json.dumps({
            "id": 1,
            "method": "Runtime.evaluate",
            "params": {"expression": "document.body.innerText"}
        }))
        result = json.loads(await ws.recv())
        print(result['result']['result'].get('value', ''))

# 替换 PAGE_ID 为实际页面 ID
asyncio.run(get_page_content("PAGE_ID"))
EOF
```

## 实用脚本

### 快速搜索脚本

```bash
# 搜索并获取结果（替换 QUERY 为搜索词）
QUERY="your search terms"
ENCODED_QUERY=$(python3 -c "import urllib.parse; print(urllib.parse.quote('$QUERY'))")
curl -s "http://localhost:9222/json/new?https://www.google.com/search?q=$ENCODED_QUERY"
```

### 获取页面 HTML

```bash
# 获取当前页面列表
PAGES=$(curl -s http://localhost:9222/json)
# 解析获取目标页面的 webSocketDebuggerUrl
```

## CDP 常用命令

通过 WebSocket 发送的 JSON 命令：

```json
// 导航到 URL
{"id": 1, "method": "Page.navigate", "params": {"url": "https://www.google.com"}}

// 获取 DOM
{"id": 2, "method": "DOM.getDocument"}

// 执行 JavaScript
{"id": 3, "method": "Runtime.evaluate", "params": {"expression": "document.body.innerText"}}

// 截图
{"id": 4, "method": "Page.captureScreenshot"}
```

## 注意事项

1. **端口占用**: 确保 9222 端口未被占用
2. **安全性**: 远程调试模式会暴露浏览器控制权，仅在本地使用
3. **资源清理**: 使用完毕后关闭不需要的标签页
4. **搜索限制**: 频繁搜索可能触发 Google 验证码

## 关闭调试实例

```bash
# 关闭所有 Chrome 调试标签页
curl http://localhost:9222/json/list | jq -r '.[].id' | xargs -I {} curl "http://localhost:9222/json/close/{}"

# 或直接关闭 Chrome 进程
pkill -f "remote-debugging-port=9222"
```
