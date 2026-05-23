# 🚀 專案駕駛艙（Project Cockpit）

> **Claude Code 會自動讀取此檔案**。請將此範本複製到您的專案根目錄，並依實際情況調整設定。
> 原版對應：`ANTIGRAVITY.md`（Anti-Gravity 2 版）→ **`CLAUDE.md`**（Claude 版）

---

## 🛠️ 我的工作環境

```
作業系統      : macOS
主要工作目錄  : ~/Projects/
Obsidian Vault : ~/Documents/ObsidianVault/
GitHub 帳號   : 您的GitHub帳號
Firebase 專案 : 您的Firebase專案ID
語言偏好      : 繁體中文（Taiwan）
程式碼風格    : 2 spaces 縮排，提交前執行 lint
```

---

## 🌅 開工 SOP

每天開始工作時，對 Claude 說：**「請執行開工 SOP」**

Claude 將依序完成：

1. 顯示今天的日期與時間（格式：YYYY-MM-DD HH:mm）
2. 列出 `~/Projects/` 目錄下的所有專案資料夾
3. 讀取 Obsidian 中的「今日任務」筆記（需已連接 mcpvault）
4. 顯示 GitHub 目前分支最近 5 個 commit 紀錄
5. 整理成「今日工作摘要」顯示

---

## 🌙 收工 SOP

每天結束工作時，對 Claude 說：**「請執行收工 SOP」**

Claude 將依序完成：

1. 將今日修改的程式碼自動 commit 到 GitHub
   - commit message 格式：`[YYYY-MM-DD] 今日工作摘要`
2. 在 Obsidian 建立或更新工作日誌：`工作日誌/YYYY-MM-DD.md`
   - 記錄今日完成事項、遇到的問題、明日待辦
3. 顯示明日建議優先處理的事項

---

## 🚀 專案初始化 SOP

開始新專案時，對 Claude 說：**「請執行專案初始化 SOP」**

Claude 將依序完成（資料夾名稱先詢問）：

1. 在 `~/Projects/` 下建立新專案資料夾
2. 初始化 git repo，建立 `.gitignore`（根據技術棧自動選擇）
3. 以 `gh repo create` 在 GitHub 建立同名公開 repo 並推送
4. 在專案根目錄建立 `CLAUDE.md`（複製本範本並調整）
5. 在 Obsidian 建立對應的專案筆記頁面（需已連接 mcpvault）
6. （選用）初始化 Firebase 專案：`firebase init`

---

## 🛠️ 常用指令速查

| 任務 | 指令 |
|------|------|
| 快速 commit | `git add . && git commit -m "[日期] 描述"` |
| 推送到 GitHub | `git push origin main` |
| 建立新 GitHub Repo | `gh repo create 名稱 --public --source=. --push` |
| Firebase 部署 | `firebase deploy` |
| 列出 NotebookLM 筆記本 | `nlm list` |
| 啟動 Obsidian MCP | `mcpvault start &` |
| 環境驗證 | `claude --version && gh auth status` |

---

## 🔌 MCP 服務連接狀態

> 編輯此區塊以追蹤您的服務連接狀態

| 服務 | 狀態 | 備註 |
|------|------|------|
| NotebookLM | ⬜ 未設定 | `pip3 install notebooklm-mcp-cli` |
| Firebase | ⬜ 未設定 | `npm install -g firebase-tools` |
| GitHub CLI | ⬜ 未設定 | `brew install gh` |
| Obsidian (mcpvault) | ⬜ 未設定 | `npm install -g @bitbonsai/mcpvault` |

完成設定後將 ⬜ 改為 ✅

---

## 📋 Claude Code MCP 設定範本

將以下內容寫入 `~/.claude/claude.json`：

```json
{
  "mcpServers": {
    "notebooklm": {
      "command": "nlm",
      "args": ["mcp"],
      "env": {}
    },
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

---

## 📝 專案筆記

> 在此記錄專案相關的重要資訊、決策、進度

- 建立日期：YYYY-MM-DD
- 專案目標：
- 技術棧：
- 相關連結：

---

*由 Claude 專屬懶人包 macOS 版自動生成 · 參考：[claude-lazy-pack-macos](https://github.com/GmiiLiao/claude-lazy-pack-macos)*
