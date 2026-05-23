# 🤖 Claude 專屬懶人包 — macOS 版

> 全平台服務連接與開發自動化指南（Claude 調適版）

改編自 [GmiiLiao/antigravity-lazy-pack-macos](https://github.com/GmiiLiao/antigravity-lazy-pack-macos)，將 Anti-Gravity 2 的所有設定全面調適為 **Claude** 與 **Claude Code**。

---

## 📂 檔案說明

| 檔案 | 說明 |
|------|------|
| 📖 [09-Claude專屬懶人包-macOS版.md](./09-Claude專屬懶人包-macOS版.md) | **核心指南主檔**：完整的服務連接步驟、SOP 設定、常見問題排解（337 行）|
| 🚀 [CLAUDE.md](./CLAUDE.md) | **專案駕駛艙範本**：Claude Code 自動讀取，含開工/收工/專案初始化 SOP |
| 📊 [ai_educational_agents_trends.md](./ai_educational_agents_trends.md) | **AI 教育代理人趨勢報告**：Claude 實戰產出範例，涵蓋個人化學習、心理健康預警等 |
| 🎨 [ai_educational_agents_infographic_zh.html](./ai_educational_agents_infographic_zh.html) | **繁體中文資訊圖表**：Claude 原生生成的 SVG/HTML 視覺化圖表 |
| 🛡️ [.gitignore](./.gitignore) | **版本控制忽略規則**：macOS + Node.js + Python + Firebase + Claude Code |
| 📝 [README.md](./README.md) | 本說明文件 |

---

## 🚀 核心內容

### 第零步：基礎環境
- Homebrew、Python 3、Node.js 安裝確認
- **Claude Code** CLI 安裝（`npm install -g @anthropic-ai/claude-code`）

### 第一部分：全平台服務連接
- 🗒️ **Google NotebookLM**：`notebooklm-mcp-cli`，支援 Claude Code MCP 整合
- 🔥 **Firebase**：`firebase-tools`，macOS 無需 cmd /c 包裝
- 🐙 **GitHub**：`gh` CLI，自動化 commit / push / repo 建立
- 🧠 **Obsidian 第二大腦**：`@bitbonsai/mcpvault`，雙向同步本地筆記

### 第二部分：繁體中文 AI 生圖
- claude.ai 網頁版直接生圖（免 API Key）
- Claude Code 生成互動式 React/HTML 圖表
- 實戰範例：[ai_educational_agents_infographic_zh.html](./ai_educational_agents_infographic_zh.html)

### 第三部分：CLAUDE.md 專案駕駛艙
- 原版 `ANTIGRAVITY.md` 的 Claude 對應版本
- Claude Code **自動讀取**專案根目錄的 `CLAUDE.md`
- 包含開工 / 收工 / 專案初始化三套完整 SOP

---

## ⚡ 快速開始

```bash
# 1. 安裝 Claude Code
npm install -g @anthropic-ai/claude-code

# 2. 啟動並登入
claude

# 3. 在專案目錄建立駕駛艙
cp CLAUDE.md ~/Projects/your-project/CLAUDE.md

# 4. 環境一鍵驗證
echo "Python: $(python3 --version)" && \
echo "Node: $(node --version)" && \
echo "gh: $(gh --version | head -1)" && \
echo "Firebase: $(firebase --version)" && \
echo "Claude Code: $(claude --version 2>/dev/null || echo '請安裝')"
```

---

## 🍎 vs 🪟 Windows vs macOS 主要差異

| 項目 | Windows 版（Anti-Gravity 2）| macOS 版（Claude）|
|------|---------------------------|-----------------|
| AI 工具 | Anti-Gravity 2 | **Claude / Claude Code** |
| SOP 檔案 | `ANTIGRAVITY.md` | **`CLAUDE.md`**（Claude Code 自動讀取）|
| Shell | PowerShell / CMD | Terminal（zsh）|
| 套件管理 | Chocolatey / winget | **Homebrew** |
| NotebookLM 編碼 | 需設定 `PYTHONIOENCODING` | ✅ 預設 UTF-8，免設定 |
| Firebase 執行 | `cmd /c firebase ...` | ✅ 直接 `firebase ...` |
| 生圖工具 | Anti-Gravity `generate_image` | claude.ai 內建生圖 / Artifacts |
| MCP 設定檔 | Anti-Gravity 設定 | `~/.claude/claude.json` |

---

## 🔧 涵蓋的常見問題（Q1–Q8）

- ❓ `pip3` Permission denied / externally-managed-environment
- ❓ `npm install -g` EACCES 權限問題
- ❓ `firebase login` 無法開啟瀏覽器（--no-localhost 解法）
- ❓ `gh` 指令找不到
- ❓ Apple Silicon（M1/M2/M3/M4）相容性
- ❓ `nlm` 指令找不到（PATH 未設定）
- ❓ Claude Code 登入失敗 / Token 過期
- ❓ mcpvault 連線失敗

---

## 📜 來源與致謝

- 原版懶人包：[mathruffian-dot/antigravity-lazy-pack](https://github.com/mathruffian-dot/antigravity-lazy-pack)
- macOS 調適版：[GmiiLiao/antigravity-lazy-pack-macos](https://github.com/GmiiLiao/antigravity-lazy-pack-macos)
- Claude 版改編：本 repo（由 Claude + Claude in Chrome 協作完成）

---

祝您與 Claude 在 macOS 上合作愉快，享受極速開發的樂趣！🚀🍎
