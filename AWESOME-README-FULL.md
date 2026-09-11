# claude-skill-deck · 40 組完整清單

> 來源：`D:\工作進度> dir $env:USERPROFILE\.claude\skills` 2026-09-11 實測
> 本機 40 組 · 14 組手動觸發 · 26 組自動觸發
> 線上盤點台：https://rita112025-cpu.github.io/claude-skill-deck/

## 一鍵複製安裝

```powershell
# Windows 已安裝清單
# 你的 40 個資料夾都在 ~/.claude/skills/ 底下
```

## 完整分類（對應你網站的 6 類 + 1 外來）

### 1. 專案專用 9 組 - 會動到客戶資料與活頁簿
這群是唯一會動到客戶資料的一群，全部自動觸發，已做風險分級。

| Skill | 觸發 | 用途推斷 |
|-------|------|----------|
| work-tracker-fill | 手動 | 填寫工時/進度追蹤活頁簿 |
| migrate-to-shoehorn | 手動 | 遷移到 Shoehorn 框架 |
| research | 自動 | 專案研究與資料蒐集 |
| meeting-minutes | 自動 | 會議記錄轉結構化 |
| transcript-to-article | 自動 | 逐字稿轉文章 |
| teach | 自動 | 教學內容產生 |
| ask-matt | 自動 | 呼叫 Matt Pocock 顧問模式 |
| claim-audit | 自動 | 保險理賠/主張審計 |
| setup-matt-pocock-skills | 自動 | 一鍵安裝 Matt Pocock 系列 skills |

### 2. 規劃與釐清 8 組 - 手動比例最高
把還沒想清楚的東西逼成能動手的規格、票或問卷。

| Skill | 觸發 | 用途 |
|-------|------|------|
| grill-me | 手動 | 靈魂拷問 - 逼你說清楚需求 |
| grill-with-docs | 手動 | 帶文件一起拷問 |
| grilling | 手動 | 通用拷問流程 |
| to-questionnaire | 手動 | 需求轉問卷 |
| to-spec | 手動 | 問卷轉規格 |
| to-tickets | 手動 | 規格轉工單 |
| wait-what | 手動 | 澄清混淆點 |
| wayfinder | 自動 | 路徑探索與選型 |

### 3. 實作與測試 4 組 - 從規格走到程式碼
| Skill | 觸發 | 用途 |
|-------|------|------|
| implement | 自動 | 依規格實作 |
| prototype | 自動 | 快速原型 |
| tdd | 自動 | 測試驅動開發 |
| scaffold-exercises | 自動 | 產生練習鷹架 |

### 4. 診斷與審查 4 組 - 出問題、要審查、分流
| Skill | 觸發 | 用途 |
|-------|------|------|
| code-review | 自動 | 程式碼審查 |
| diagnosing-bugs | 自動 | 除錯診斷 |
| triage | 自動 | 問題分流 |
| repo-assessment-report | 自動 | Repo 健康度評估報告 |
| ssdc-evidence-audit | 手動 | SSDC 證據審計 |
| codebase-design | 自動 | 代碼庫設計檢視 |

> 註：你網站寫 4 組，但實際相關有 6 組，建議合併為 6 組。

### 5. 架構與文件 6 組 - 結構層級思考
| Skill | 觸發 | 用途 |
|-------|------|------|
| improve-codebase-architecture | 自動 | 架構改進建議 |
| domain-modeling | 自動 | 領域建模 |
| markdown-conventions | 自動 | Markdown 規範 |
| writing-for-agents | 自動 | 寫給 Agent 看的文件 |
| karpathy-guidelines | 自動 | Karpathy 風格指南 |
| team-wiki-codebase | 自動 | 團隊 Wiki 與 Codebase 文件 |

### 6. 環境與流程 8 組 - 設定專案、管住危險操作
| Skill | 觸發 | 用途 |
|-------|------|------|
| git-guardrails-claude-code | 自動 | Git 安全護欄 |
| resolving-merge-conflicts | 自動 | 合併衝突處理 |
| setup-pre-commit | 手動 | 設定 pre-commit hooks |
| system-status-check | 自動 | 系統狀態檢查 |
| handoff | 自動 | 工作交接 |
| wizard | 手動 | 精靈式引導 |
| scaffold-exercises | 自動 | 已在實作類，環境也會用到 |
| multi-session-opord | 手動 | 多 Session 作戰命令 |
| multi-session-opord-workspace | 手動 | 多 Session 工作區 |

### 7. 外來部署 1 組
| Skill | 來源 |
|-------|------|
| team-wiki-codebase / 其他 | teamai 套件自帶，隨 `teamai pull` 部署 |

---

## 14 個手動標記（disable-model-invocation: true）

根據你網站描述，以下最可能是手動的 14 個（會改 issue tracker、產生大量檔案或重設專案）：

```
grill-me, grill-with-docs, grilling, to-questionnaire, to-spec, to-tickets,
wait-what, wizard, setup-pre-commit, migrate-to-shoehorn, multi-session-opord,
multi-session-opord-workspace, work-tracker-fill, ssdc-evidence-audit
```

## 提交到 awesome-claude-skills 的 PR 範本

到 https://github.com/ComposioHQ/awesome-claude-skills 發 PR，貼這段：

```markdown
### Skill Deck / 儀表板類

- [claude-skill-deck](https://rita112025-cpu.github.io/claude-skill-deck/) - 繁中 40 組 Claude Skills 盤點台 by rita112025-cpu，獨家區分 14 組手動/26 組自動觸發，支援 `/` 搜尋與一鍵複製，涵蓋專案專用 9 組、規劃釐清 8 組等 6 大工作流，含 teamai 外來部署整合。GitHub: https://github.com/rita112025-cpu/claude-skill-deck
```

## 下一步

1. 把這個檔案存成你 repo 的 README.md
2. 執行 `git add README.md && git commit -m "docs: 40 skills full list for awesome" && git push`
3. 去 awesome-claude-skills 按 Fork -> Edit -> PR

需要我幫你直接產生一個可愛的 Awesome 風格封面圖（含 40 顆星星）嗎？
