# 客製化浴缸網站 — 專案交接說明（HANDOFF）

> 最後更新：2026-06-29　|　作者：Lyric ＋ AI
> 用途：在另一台電腦上接續本專案。讀完這份即可掌握全貌、檔案結構與後續待辦。

---

## 1. 專案目標

依照 6/29 與 Masa 的電話會議結論，把「**Customize Your Own Bathtub（客製化浴缸）**」做成一個成品網站。
核心精神（出自 Masa 電話與 NotebookLM 影片方法論）：

- 不做固定型錄（沒有 Database），改走**客製化模式**當「拋磚引玉」的入口。
- 目標客群：**設計師 / 室內設計師 / 全球行銷人員**。
- 照影片「24 小時用 AI 開公司」的流程邏輯：強鉤子 landing、痛點文案、即時視覺 WOW、24/7 接洽、低門檻收線索。
- 先做到約 90% 再從中修改。

---

## 2. 資料來源（決策依據）

| 來源 | 內容 | 位置 |
|---|---|---|
| 電話/會議紀錄 | 6/29「浴缸客製化業務 AI 建置討論」需求 | Notion 頁面「會議 @今天」 |
| 影片方法論 | 「I Built A Business With AI In 24 Hours」8 步驟＋核心邏輯 | NotebookLM 同名 notebook |
| 行銷概念書 | 定位、USP、客群、銷售漏斗 | `全球客製浴缸專案_行銷概念書與前置作業清單.md` |
| 3D 工具調研 | 草圖→3D 雙路徑管線（Tripo/Hunyuan3D + Rhino MCP） | `3D工具調研報告_2026-06.md` |
| 競品分析 | Badeloft 銷售漏斗、競品全表、風險清單 | `Bathtub B2C Custom Market - Competitor Analysis & Badeloft Sales Model.docx` 等 |
| 材質網路研究 | 壓克力 vs 石樹脂 vs 銅（重量/保溫/價格/維護數據） | 見本檔第 9 節 |

**最重要的策略結論**：全球沒有人做「**壓克力 ＋ 真客製 ＋ B2C 線上下單**」——這是空白市場。最大對手 Badeloft 用石樹脂、把壓克力貶為「便宜材料」，且它的「Custom Tub Builder」是假的（點了跳回標準型錄）。我們正面打壓克力的優勢，並做出**真正的線上設計工具**。

---

## 3. 重要決策脈絡（為什麼這樣做）

1. **定位轉向**：初版把壓克力當缺點藏起來；讀完競品分析後改為**正面主打壓克力**（更輕、更好塑形、便宜 30–50%、澳洲在地）。
2. **從單頁改多頁**：使用者要求正式「網站架構」，故拆成多頁、共用頁首/頁尾。
3. **語言邏輯**：第一次進站＝英文（不自動偵測）；選了語言後用 `localStorage` 記住、跨頁固定。支援 **English / 简体中文 / ไทย**。
4. **無後端**：目前是純前端 demo。詢價表單是即時確認＋`mailto` 備援，**尚未接真正的寄送/CRM**（見第 8 節待辦）。

---

## 4. 檔案結構

```
客製化浴缸專案/
├─ 專案說明_HANDOFF.md         ← 本檔
├─ website/                    ← ★ 正式網站（在這裡開發）
│   ├─ index.html              首頁
│   ├─ customize.html          客製化設計室（互動配置器）
│   ├─ why-acrylic.html        為什麼選壓克力（6 賣點＋對照表）
│   ├─ how-it-works.html       流程與報價（4 步驟＋樣品包＋$399 諮詢）
│   ├─ designers.html          設計師專區（Trade Programme）
│   ├─ portfolio.html          作品集（概念渲染，待換真實照）
│   ├─ acrylic-vs-stone-resin.html   SEO 文章：壓克力 vs 石樹脂
│   ├─ materials-guide.html    觀念普及文章：壓克力 vs 石樹脂 vs 銅
│   ├─ contact.html            詢價表單（讀 URL 參數帶入設計）
│   ├─ styles.css              共用樣式（深色奢華＋金色）
│   └─ app.js                  共用 JS（配置器＋i18n＋表單＋頁尾注入）
├─ customize-your-own-bathtub.html   ← 舊的單頁版（已被 website/ 取代，可保留或刪除）
├─ （各份研究報告 .md / .docx）
```

開啟方式：直接用瀏覽器打開 `website/index.html` 即可（純靜態，無需伺服器）。

---

## 5. 網站架構與頁面間串接

- 共用**頁首導覽**（Home / Customize / Why Acrylic / How It Works / For Designers / Portfolio ＋ CTA）與**頁尾**，右上角有**語言選擇器**。手機版導覽收合成漢堡選單。
- **設計室 → 詢價的資料傳遞**：在 `customize.html` 按「Send this design to our atelier」會把目前選的形狀/材質/顏色/尺寸/加值，用 **query string** 帶到 `contact.html`，`contact.html` 讀取後自動填好設計摘要＋預覽圖。（不用 localStorage 傳資料，純網址參數。）

---

## 6. 技術說明（接手前必看）

### 6.1 互動配置器（`app.js` 內 `buildTubSVG` 等）
- 浴缸預覽是**純 SVG 程式生成**（非圖片）：依形狀(oval/rect/slipper/round/japanese)、材質色、尺寸、加值即時重繪。
- 容量是粗估公式（`capacityOf`），非精算。
- 同一個 `buildTubSVG` 也用於首頁 hero 與作品集卡片。

### 6.2 多語系 i18n（重點機制）
全部集中在 `app.js`，**8 個 HTML 不含翻譯**，原理是「文字節點字典替換」：

- `DICT`＝英文→简中字典；`DICTTH`＝英文→泰文字典；`TITLES`/`TITLES_TH`＝頁面標題翻譯。
- 載入時 `initCache()` 走訪所有文字節點記下英文原文；切換語言時依字典替換，切回英文則還原。
- 動態文字（形狀名、材質名、加值、作品集、確認訊息、顧問彈窗）另用 `shapeZH/shapeTH`、`finishZH/finishTH`、`addonZH/addonTH`、`tagZH/tagTH`、`MSG` 處理。
- 預設英文；選擇存進 `localStorage("ka_lang")`（加 cookie 備援），每頁載入自動套用。

**要新增/修改翻譯**：在 `app.js` 的 `DICT`（簡中）和 `DICTTH`（泰文）裡，以「**英文原句為 key**」加一行即可。key 必須跟頁面上的英文**完全一致**（含標點、破折號 `—`、`·`、`→`）。句子中有 `<b>` 會被拆成多個文字節點，需個別翻譯每段。

**要再加一種語言（例如繁中）**：複製一份字典（如 `DICTZHTW`）、在 `dictFor()`/`titleFor()`/各 `*Maps`/`MSG` 加該語言分支、語言選擇器 `<option>` 加一項即可。

### 6.3 頁尾「Materials Guide」連結
是由 `app.js` 在載入時**自動注入**到每頁頁尾（找 `acrylic-vs-stone-resin.html` 連結後插入），所以不必改 9 個 HTML。

---

## 7. 如何在另一台電腦繼續

1. 把整個 `客製化浴缸專案/` 資料夾（含 `website/`）複製過去。
2. 直接用瀏覽器開 `website/index.html` 預覽；改 HTML/CSS/JS 後重新整理即可。
3. **驗證方式**（選用，需 Node.js）：本專案開發時用 jsdom 做無頭測試——載入每頁、跑配置器/表單、切三語掃描殘留英文、檢查失連。可請 AI 重新產生測試腳本執行（過去結果：JS 零錯誤、零失連、三語零殘留）。
4. 編輯建議：文字內容改 HTML；**翻譯一定要同步改 `app.js` 的 `DICT` 與 `DICTTH`**，否則切語言會露出英文。

---

## 8. 已知缺口 / 待辦（接手後可做）

- [ ] **詢價表單接真正寄送**：目前是前端確認＋mailto，需接 email/表單服務或 CRM。
- [ ] **作品集換真實照**：`portfolio.html` 目前是概念渲染（`app.js` 內 `pieces` 陣列），等 Masa 的真實浴缸照替換；hero 也可換真實照。
- [ ] **社群證明**：加 Houzz / Google 評價區（競品 Badeloft 有 251 則五星，是它的優勢）。
- [ ] **金流/成交**：Badeloft 能線上刷卡/分期直接成交，我們尚無；可評估加購物車或訂金連結。
- [ ] **AR 試擺**：研究建議的升級項（壓克力較易建模），尚未做。
- [ ] **分期試算器**：拉霸看每月付款。
- [ ] **舊檔處理**：根目錄 `customize-your-own-bathtub.html` 已被 `website/` 取代，可移到備份或刪除。
- [ ] （可選）語言選擇反映在網址 `?lang=th` 以便分享特定語言版連結。

---

## 9. 內容要點速查

**定位**：設計師專屬的客製壓克力浴缸引擎，全世界只有一個；澳洲製造、工廠直供、無 MOQ。

**四大 USP**：① 世界唯一（壓克力＋真客製＋B2C 線上）② 依你的 CAD 任意曲線（對手不收外部 CAD）③ 更輕好裝（vs 石樹脂 200–350 lb）④ 便宜 30–50%＋Afterpay/Zip 分期。

**漏斗（照搬並升級 Badeloft）**：免費樣品包（lead magnet）→ 付費設計諮詢 AUD $399（可全額折抵）→ 3D 圖＋簽署設計規格書 → 2–3 回合修改 → 開模生產（全程進度照）→ 澳洲配送。設計師另有 Trade Programme（15–25% 折扣、依 CAD 製造、專屬窗口）。

**材質數據（觀念普及文章用）**：
- 重量：壓克力 27–45 kg｜石樹脂 90–160 kg｜銅 160–270 kg
- 保溫：壓克力導熱低(~0.2 W/m·K)觸感溫；石樹脂熱質量大、長泡保溫最久；銅初觸冰冷
- 設計：壓克力熱塑＝可塑性最高；石樹脂鑄型有限；銅手工經典款
- 價格：壓克力最實惠；銅最貴(AUD $3,000–$15,000+)
- 維護：壓克力無孔好修；銅需拋光防鏽；石樹脂缺角難修

**材質研究來源**：Vanity Art、Bathtubs Plus、Kota Baths、Streamline Bath、William Holland、Magnus Home Products（壓克力 vs 石樹脂 vs 銅）。
