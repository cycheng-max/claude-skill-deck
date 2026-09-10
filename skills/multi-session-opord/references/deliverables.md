# 交付物版型與產出流程

## 作戰令互動頁（HTML）

單一 HTML，不依賴網路（Google Fonts 可載，缺了要有後備字型）。先叫 `html-large-type`。六個分頁用 tab 切換，網址 hash 記位置：

| 分頁 | 內容 |
|---|---|
| 摘要與拍板 | 一句結論、四個數字、編組一句話、拍板清單（勾選存 localStorage，只在瀏覽器本機）、v 幾修訂說明 |
| 一、情況 | 現況表（主張／證據位置／三態）、外部系統觀察、不能碰的東西 |
| 二、任務 | 待辦→工作包表（含原始編號對映與時間碼）、流程閉環卡、不進開發項、依賴表 |
| 三、執行 | 編組卡（逐檔邊界）、模型理由表、工作包規格（dl 列表：分支、改動面、不做、測試、驗收、風險、回滾）、時程 |
| 四、派工單 | 依 session 篩選晶片、每張單 `<pre>` 加複製鈕、派發時機 |
| 五、通信與驗收 | 通信規則卡、證據表、整合驗收清單、回滾表、核實處置表（每輪一段）、成本邊界 |

頁首 meta 放：發令日（含星期）、基準 commit、目標交付、修訂版與 md5 前 8 碼。列印樣式把所有分頁展開、隱藏導覽與複製鈕、字級改 pt。

## 拍板單前置文件（HTML → PDF）

結構見 templates.md「拍板單結構」。列印時 `h2` 換頁、決策卡 `break-inside: avoid`。

## HTML 印 PDF 並合併

Edge headless 在這台機器可用，字型會嵌入：

```powershell
$src="<html 絕對路徑>"; $out="$env:TEMP\a.pdf"; $uri=([System.Uri]$src).AbsoluteUri
& "C:\Program Files (x86)\Microsoft\Edge\Application\msedge.exe" --headless=new --disable-gpu --no-pdf-header-footer --virtual-time-budget=8000 "--print-to-pdf=$out" $uri | Out-Null
```

合併並加書籤與 metadata（pypdf 已裝）：

```python
from pypdf import PdfReader, PdfWriter
w = PdfWriter()
for src in ["cover.pdf", "strategy.pdf"]:
    for p in PdfReader(src).pages:
        w.add_page(p)
w.add_outline_item("說明與拍板單", 0)
w.add_outline_item("附錄：戰略頁全文", len(PdfReader("cover.pdf").pages))
w.add_metadata({"/Title": "...", "/Author": "總參謀長 session"})
w.write("out.pdf")
```

輸出檔被開著會 `PermissionError`，改存 `_v2` 檔名，不要覆蓋。印完用 `pdftoppm -r 45 -f 1 -l 1 -png` 看一頁確認版面。

## zip 交付

內含：先讀我（檔案清單與先看哪份）、PDF、兩份 HTML 來源檔、證據 md（會議擷取、repo 調查簡報）。用 Python `zipfile` 寫（檔名 UTF-8 旗標，`unzip -l` 在終端顯示亂碼是 codepage，Explorer 正常）。打包前：

```bash
grep -l -i -E "channel_secret|BEGIN PRIVATE|api_key=" *.html *.md
```

命中要逐一看是不是規則說明文字。個資目錄的內容不進 zip。

## 給決策者的 LINE 訊息

五句以內：這是什麼、先看哪份幾分鐘、要他決定什麼（建議先只核准查核）、要他給什麼、不勾什麼都不會動。決策者只批一小塊時，回覆也只講那一塊，附驗收分幾階段。
