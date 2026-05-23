# Claude 專屬懶人包 #09：全平台服務連接與自動化技能大整合（macOS 版）

> **版本**：v1.0-macOS（Claude 專屬版）
> **更新日期**：2026-05-23
> **語系偏好**：預設繁體中文（Taiwan）
> **適用系統**：macOS 12 Monterey 及以上版本
> **改編自**：[GmiiLiao/antigravity-lazy-pack-macos](https://github.com/GmiiLiao/antigravity-lazy-pack-macos)

---

## 🚀 這個懶人包會幫你做什麼？

本懶人包是專為在 **macOS** 上使用 **Claude**（包含 [claude.ai](https://claude.ai) 網頁版與 **Claude Code** CLI）的使用者設計的終極整合指南。照著本懶人包的步驟，您將能一步步引導 Claude 連接您所有的雲端與本地服務，並打造全自動化的「開工/收工/專案初始化」工作流：

1. **基礎環境確認**：Homebrew、Python 3、Node.js 一次到位
2. **NotebookLM 連接**：透過 `notebooklm-mcp-cli` 讀寫您的 NotebookLM 筆記與來源
3. **Firebase 連接**：透過 `firebase-tools` 管理並部署您的 Firebase 雲端資料庫
4. **GitHub 連接**：透過 `gh` CLI 進行自動化 Git commit、push 與遠端倉庫建立
5. **Obsidian 第二大腦連接**：透過 `@bitbonsai/mcpvault` 與本地 Markdown 筆記雙向同步
6. **原生 AI 生圖**：利用 Claude 內建生圖能力，以**繁體中文**為優先生成高品質資訊圖表
7. **「開工/收工/專案初始化」全自動技能**：透過 `CLAUDE.md` 專案駕駛艙落實 SOP 流程

---

## 📋 第零步：macOS 基礎環境確認

### 1. 安裝 Homebrew

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
brew --version
```

### 2. 確認 Python 3

```bash
python3 --version
# 若無：brew install python3
```

### 3. 確認 Node.js

```bash
node --version && npm --version
# 若無：brew install node
```

### 4. 安裝 Claude Code（CLI）

```bash
npm install -g @anthropic-ai/claude-code
claude  # 首次執行引導瀏覽器授權
```

### ✅ 一鍵環境驗證

```bash
echo "=== 基礎環境驗證 ===" && \
echo "Homebrew : $(brew --version | head -1)" && \
echo "Python   : $(python3 --version)" && \
echo "Node.js  : $(node --version)" && \
echo "npm      : $(npm --version)" && \
echo "Git      : $(git --version)" && \
echo "Claude Code: $(claude --version 2>/dev/null || echo '❌ 尚未安裝')" && \
echo "=== 驗證完成 ==="
```

---

## 🛠️ 第一部分：全平台服務連接指南

### 🎯 步驟一：連接 Google NotebookLM（MCP）

```bash
pip3 install notebooklm-mcp-cli
nlm login    # 開啟瀏覽器授權
nlm list     # 驗證連線
```

> ✅ macOS 預設 UTF-8，無需設定 PYTHONIOENCODING。

若 `nlm` 找不到，加入 PATH：
```bash
echo 'export PATH="$HOME/Library/Python/3.11/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc
```

Claude Code MCP 設定（`~/.claude/claude.json`）：
```json
{
  "mcpServers": {
    "notebooklm": {
      "command": "nlm",
      "args": ["mcp"],
      "env": {}
    }
  }
}
```

---

### 🎯 步驟二：連接 Firebase 資料庫

```bash
npm install -g firebase-tools
firebase login           # 自動開啟瀏覽器授權
firebase projects:list   # 確認連線
```

> ✅ macOS 無需 cmd /c 包裝，可直接執行 firebase 指令。

---

### 🎯 步驟三：連接 GitHub 帳戶（gh CLI）

```bash
brew install gh
unset GITHUB_TOKEN
gh auth login --web --git-protocol https
gh auth status
git config --global user.name "您的名字"
git config --global user.email "您的email@example.com"
```

---

### 🎯 步驟四：連接 Obsidian 第二大腦（mcpvault）

```bash
npm install -g @bitbonsai/mcpvault
mcpvault init --vault ~/Documents/ObsidianVault
mcpvault start &
```

Claude Code MCP 設定（加入 `~/.claude/claude.json`）：
```json
{
  "mcpServers": {
    "obsidian": {
      "command": "mcpvault",
      "args": ["serve"],
      "env": {
        "VAULT_PATH": "/Users/您的使用者名稱/Documents/ObsidianVault"
      }
    }
  }
}
```

> 💡 iCloud Vault 路徑：`~/Library/Mobile Documents/iCloud~md~obsidian/Documents/Vault名稱`

---

## 🎨 第二部分：原生免 API Key 繁體中文生圖

### 方法一：claude.ai 直接生圖

```
請生成一張關於「AI 教育代理人應用」的繁體中文資訊圖表，
包含主題：個人化學習、教師助理、智慧教室、心理健康預警。
使用深色系配色，所有文字以繁體中文呈現，風格簡約專業。
```

### 方法二：Claude Code 生成互動式圖表

```
請生成互動式「AI 應用趨勢」圖表，
使用 React + Recharts，繁體中文標示，
包含長條圖、圓餅圖與時間軸，輸出為 Artifact。
```

| 技巧 | 說明 |
|------|------|
| 明確指定語言 | 加入「所有文字使用繁體中文」 |
| 指定配色風格 | 「深色背景」、「莫蘭迪色系」、「企業藍白」 |
| 指定版型 | 「寬版橫幅」、「正方形」、「直式 A4 海報」 |
| 迭代優化 | 「請把標題字加大」、「換成藍色主題」 |

---

## 🤖 第三部分：建立 CLAUDE.md 專案駕駛艙

**Claude Code 會自動讀取專案根目錄下的 `CLAUDE.md`**，這是官方支援功能。

```bash
touch ~/Projects/CLAUDE.md
```

範本內容：

```markdown
# 🚀 專案駕駛艙（Project Cockpit）

## 我的工作環境
- **作業系統**：macOS
- **主要工作目錄**：~/Projects/
- **Obsidian Vault**：~/Documents/ObsidianVault/
- **GitHub 帳號**：您的GitHub帳號
- **語言偏好**：繁體中文（Taiwan）

## 🌅 開工 SOP
1. 顯示今天日期時間（YYYY-MM-DD HH:mm）
2. 列出 ~/Projects/ 所有專案資料夾
3. 讀取 Obsidian 的「今日任務」筆記
4. 顯示 GitHub 最近 5 個 commit
5. 整理成「今日工作摘要」

## 🌙 收工 SOP
1. 自動 commit 今日修改（格式：`[YYYY-MM-DD] 摘要`）
2. 在 Obsidian 建立工作日誌 YYYY-MM-DD.md
3. 顯示明日建議優先事項

## 🚀 專案初始化 SOP
1. 建立新專案資料夾（先詢問名稱）
2. git init + .gitignore
3. gh repo create --public --source=. --push
4. 建立 CLAUDE.md
5. Obsidian 建立對應專案筆記

## 常用指令速查
| 任務 | 指令 |
|------|------|
| 快速 commit | `git add . && git commit -m "[日期] 描述"` |
| 推送 GitHub | `git push origin main` |
| Firebase 部署 | `firebase deploy` |
| 列出 NotebookLM | `nlm list` |
```

---

## 🍎 macOS 專屬實用技巧

### 環境變數持久化

```bash
nano ~/.zshrc
# 加入：
export PATH="$HOME/Library/Python/3.11/bin:$PATH"
export PATH="$HOME/.npm-global/bin:$PATH"
source ~/.zshrc
```

### Windows → macOS 指令對照

| 說明 | Windows | macOS |
|------|---------|-------|
| Shell | PowerShell | Terminal（zsh）|
| 環境變數 | `$env:VAR="值"` | `export VAR="值"` |
| 套件管理 | Chocolatey | **Homebrew** |
| Firebase 執行 | `cmd /c firebase` | 直接 `firebase` |
| NotebookLM 編碼 | `PYTHONIOENCODING=utf-8` | ✅ 不需要 |

---

## 🔧 macOS 常見問題排解

### ❓ Q1：pip3 Permission denied / externally-managed-environment

```bash
# 方法一：--user 安裝
pip3 install --user notebooklm-mcp-cli
# 方法二：虛擬環境（推薦）
python3 -m venv ~/.venv/claude
source ~/.venv/claude/bin/activate
pip install notebooklm-mcp-cli
```

### ❓ Q2：npm install -g Permission denied

```bash
mkdir ~/.npm-global
npm config set prefix '~/.npm-global'
echo 'export PATH=~/.npm-global/bin:$PATH' >> ~/.zshrc
source ~/.zshrc
```

### ❓ Q3：firebase login 無法開啟瀏覽器

```bash
firebase login --no-localhost
```

### ❓ Q4：gh 指令找不到

```bash
brew install gh
```

### ❓ Q5：Apple Silicon（M1/M2/M3/M4）相容性

```bash
which brew      # 應為 /opt/homebrew/bin/brew
node -e "console.log(process.arch)"   # 應為 arm64
```

### ❓ Q6：nlm 指令找不到

```bash
python3 -m site --user-base
echo 'export PATH="$HOME/Library/Python/3.11/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc
```

### ❓ Q7：Claude Code 登入失敗

```bash
claude auth logout && claude auth login
```

### ❓ Q8：mcpvault 連線失敗

```bash
cat ~/.claude/claude.json   # 確認設定格式
claude --debug              # 查看詳細錯誤
```

---

## ✅ 完整驗證清單

```bash
echo "=== Claude 環境完整驗證 ===" && \
echo "Python   : $(python3 --version 2>/dev/null || echo '❌')" && \
echo "Node.js  : $(node --version 2>/dev/null || echo '❌')" && \
echo "Git      : $(git --version 2>/dev/null || echo '❌')" && \
echo "Claude Code : $(claude --version 2>/dev/null || echo '❌ 未安裝')" && \
echo "GitHub CLI  : $(gh --version 2>/dev/null | head -1 || echo '❌')" && \
echo "Firebase CLI: $(firebase --version 2>/dev/null || echo '❌')" && \
echo "NotebookLM  : $(nlm --version 2>/dev/null || echo '❌ 或路徑未加入 PATH')" && \
echo "mcpvault    : $(mcpvault --version 2>/dev/null || echo '❌')" && \
gh auth status 2>&1 | head -3 && \
echo "=== 驗證完成 🎉 ==="
```

---

祝您與 Claude 在 macOS 上合作愉快，享受極速開發的樂趣！🚀🍎
