# Claude Skill 盤點台

這台機器 `~/.claude/skills` 底下 40 個 Claude Code skill 的指令小抄。其中 **14 個必須手動輸入指令才會啟動**，其餘 26 個會在情境符合時自動觸發。

線上版：<https://rita112025-cpu.github.io/claude-skill-deck/>，可搜尋、可篩選，點一下就能複製指令。

## 手動與自動的差別

標為「手動」的 skill，在 `SKILL.md` 裡寫了 `disable-model-invocation: true`，模型不會依情境自動觸發，必須自己輸入 `/指令名稱`。這是刻意的設計：它們多半會改動 issue tracker、產生大量檔案或重設專案設定。

## 來源

| 來源 | 數量 | 授權 |
|---|---|---|
| 自製 | 9 | 本 repo 未附授權聲明 |
| [mattpocock/skills](https://github.com/mattpocock/skills) | 29 | MIT |
| [multica-ai/andrej-karpathy-skills](https://github.com/multica-ai/andrej-karpathy-skills) | 1 | 原 repo 未標示 |
| teamai 套件 | 1 | 隨 `teamai pull` 部署 |

本 repo 只收錄自製 skill `multi-session-opord` 的原始檔（`skills/` 目錄）。其他 skill 請到各自的來源 repo 取得。來源是 2026-09-11 比對各來源 repo 的 skill 名稱後判定的。

## 清單

### 專案專用（9 個，自製）

為實際業務寫的，也是唯一會動到客戶資料與活頁簿的一群。

| 指令 | 觸發 | 用途 |
|---|---|---|
| `/work-tracker-fill` | 自動 | 維護工作追蹤活頁簿：寫入工作項目、完成版本升版、版面精簡 |
| `/ssdc-evidence-audit` | 自動 | SSDC 系統的第二階段原始碼實證研究，全程唯讀 |
| `/meeting-minutes` | 自動 | 逐字稿整理成決議、爭議、資訊、待辦四類會議紀錄 |
| `/system-status-check` | 自動 | 查 GitHub repo 狀態與健康檢查端點，兩邊比對後產出報告 |
| `/repo-assessment-report` | 自動 | 調查一個 repo 與它的線上端點，產出帶截圖的 PDF 評估報告 |
| `/claim-audit` | 自動 | 稽核文章或逐字稿的論述品質，回查每個具名來源的原文 |
| `/transcript-to-article` | 自動 | 把演講或訪談逐字稿重組成可發布的繁體中文文章 |
| `/markdown-conventions` | 自動 | 繁體中文 Markdown 的排版與結構規範 |
| `/multi-session-opord` | 自動 | 把會議待辦拆成多個 session 的分工計畫，附給決策者確認的清單 |

### 規劃與釐清（8 個，出自 mattpocock/skills）

| 指令 | 觸發 | 用途 |
|---|---|---|
| `/grilling` | 自動 | 針對計畫、決定或想法連續逼問，把思路壓到站得住為止 |
| `/grill-me` | 手動 | 同樣是逼問，但這個入口只能手動叫 |
| `/grill-with-docs` | 手動 | 逼問的同時把 ADR 與詞彙表一起寫出來 |
| `/wayfinder` | 手動 | 把一個 session 裝不下的大工程，拆成 issue tracker 上的決策票逐一解決 |
| `/to-spec` | 手動 | 把當前對話直接寫成規格並發到 issue tracker |
| `/to-tickets` | 手動 | 把計畫或對話拆成一組追蹤票，每張票標明它擋住誰 |
| `/to-questionnaire` | 手動 | 把答不了的決策轉成問卷，交給知道的人填 |
| `/prototype` | 自動 | 做一個拋棄式原型，回答某個設計問題 |

### 實作與測試（4 個，出自 mattpocock/skills）

| 指令 | 觸發 | 用途 |
|---|---|---|
| `/implement` | 手動 | 依照規格或一組票開始實作 |
| `/tdd` | 自動 | 測試先行的開發：紅、綠、重構 |
| `/scaffold-exercises` | 自動 | 建立練習題的目錄結構，含章節、題目、解答與講解 |
| `/migrate-to-shoehorn` | 自動 | 把測試檔裡的 `as` 型別斷言換成 shoehorn |

### 診斷與審查（4 個，出自 mattpocock/skills）

| 指令 | 觸發 | 用途 |
|---|---|---|
| `/diagnosing-bugs` | 自動 | 難纏 bug 與效能回歸的診斷迴圈 |
| `/code-review` | 自動 | 從標準與規格兩軸審查某個基準點之後的變更 |
| `/triage` | 手動 | 讓 issue 與外部 PR 走一套分流狀態機，最後產出可交辦的簡報 |
| `/resolving-merge-conflicts` | 自動 | 處理進行中的 merge 或 rebase 衝突 |

### 架構與文件（6 個，出自 mattpocock/skills）

| 指令 | 觸發 | 用途 |
|---|---|---|
| `/codebase-design` | 自動 | 設計深模組時的共用語彙 |
| `/improve-codebase-architecture` | 手動 | 掃描整個 codebase 找可深化處，出成視覺化 HTML 報告，再針對挑中的那個逼問 |
| `/domain-modeling` | 自動 | 建立並打磨專案的領域模型 |
| `/writing-for-agents` | 自動 | 寫給 agent 讀的文件 |
| `/research` | 自動 | 對高可信一手來源查證，並把結果寫成 repo 裡的 Markdown |
| `/teach` | 手動 | 在這個工作區裡教一個新技能或概念 |

### 環境與流程（8 個）

`/karpathy-guidelines` 出自 andrej-karpathy-skills，其餘 7 個出自 mattpocock/skills。

| 指令 | 觸發 | 用途 |
|---|---|---|
| `/setup-pre-commit` | 自動 | 在目前的 repo 裝 Husky 前置提交鉤子 |
| `/git-guardrails-claude-code` | 自動 | 設 hook 擋掉危險的 git 指令 |
| `/wizard` | 自動 | 產生互動式 bash 精靈，帶人走只有人能做的步驟 |
| `/karpathy-guidelines` | 自動 | 減少常見 LLM 編碼錯誤的行為準則 |
| `/setup-matt-pocock-skills` | 手動 | 一次性前置設定：issue tracker、分流標籤詞彙、領域文件配置 |
| `/ask-matt` | 手動 | 問哪個 skill 適合現在的情況 |
| `/handoff` | 手動 | 把當前對話壓縮成交接文件，讓另一個 session 接手 |
| `/wait-what` | 手動 | 上一則訊息沒說清楚，要求重講一次 |

### 外來部署（1 個，teamai 套件）

| 指令 | 觸發 | 用途 |
|---|---|---|
| `/team-wiki-codebase` | 自動 | 把多倉庫、多微服務的大型代碼庫壓成結構化知識庫 |

## 資料來源與維護

- **名稱與分類**：來自 2026-09-09 對 `~/.claude/skills` 的實際掃描，2026-09-10 補入 `multi-session-opord`。分類依用途歸納，不是原作者的分法。
- **用途說明**：取自各 skill 的 `SKILL.md`，改寫成一句話。
- **不列入的項目**：`multi-session-opord-workspace` 是工作資料夾，裡面沒有 `SKILL.md`，不是 skill。外掛提供的 skill 與 Claude Code 內建指令也不在此表。
- **更新方式**：README 依線上版 `index.html` 裡的 `DATA` 陣列整理。新增或修改 skill 時，兩邊要一起更新。
