# Kreiner Atelier Website Optimization Recommendations

## 目前網站架構

目前網站不是單頁式網站，而是一個內容型 + 互動型的 B2C / B2B 混合網站。主要頁面包括：

- `index.html`：首頁，包含品牌主張、3D Hero、流程、作品、信任背書與 CTA。
- `customize.html`：6 步驟 3D Design Studio，讓使用者選外型、材質、尺寸、加購項目並送出需求。
- `contact.html`：詢價、樣品包、trade pricing、estimate 表單。
- `materials.html`：Acrylic 與 Solid Surface 材質比較。
- `how-it-works.html`：從草圖到 3D render、修改、生產與配送的流程。
- `designers.html`：室內設計師與建築師專區。
- `portfolio.html`：作品集與概念 render。
- `guides.html` 與多篇 SEO 文章：尺寸指南、人體工學、材質比較、freestanding vs built-in 等。

整體方向是好的：有高質感視覺、3D 互動、SEO 內容入口，以及表單轉換。但目前最大的問題是定位不夠單一：首頁與聯絡頁同時對屋主、設計師、建築師說話，導致 B2C 消費者的購買路徑不夠直覺。

## 核心診斷

目前網站比較像「高端設計師合作平台 + 客製浴缸展示」，但如果主要目標是 B2C，應該讓屋主一進站就清楚知道：

1. 這是不是適合我的浴室？
2. 大概多少錢？
3. 多久可以完成？
4. 我需要準備什麼？
5. 有沒有樣品、保固、配送與安裝支援？
6. 下一步要做什麼？

現在網站有回答其中一部分，但資訊分散在不同頁面，且很多文案使用 `your client`，比較像對設計師說話。B2C 首頁應該優先對「屋主本人」說話，設計師內容則放在 `For designers`。

## 建議的 B2C 主流程

建議把網站轉換流程調整成以下漏斗：

1. 使用者從 Google、AI 搜尋、社群、文章頁或首頁進站。
2. 使用者先看到清楚主張：為自己的浴室訂製一座合身浴缸。
3. 網站立即回答價格區間、交期、配送、材質與保固。
4. 使用者進入 Design Studio 或索取免費樣品包。
5. Design Studio 給出尺寸、材質、容量與初步估價區間。
6. 使用者留下 email / phone 儲存設計。
7. 使用者選擇下一步：
   - Get a price estimate
   - Book $399 3D design consultation
   - Request free sample kit
8. 系統自動寄出設計摘要與下一步。
9. 人工設計顧問跟進，完成報價、確認圖面與收訂金。
10. 生產、配送、售後與安裝照片回收。

這類高單價客製品不適合一開始就做完整購物車結帳。比較合理的 B2C 流程是「互動配置 + 低摩擦 lead capture + 設計諮詢訂金 + 人工成交」。

## 優先優化建議

### 1. 首頁改成 B2C 為主

目前很多文案偏向設計師，例如 `your client`。建議首頁改成直接對屋主說話。

建議主標方向：

```text
Design a bathtub made for your bathroom, your body, and your style.
```

中文方向：

```text
為你的浴室，訂製一座真正合身的浴缸。
```

首頁第一屏建議補上三個消費者最在意的資訊：

- 起價或典型價格範圍：例如 `Custom acrylic tubs from AUD $X`。
- 交期：例如 `3D render in 48 hours · production in X-Y weeks`。
- 配送與安裝：例如 `Delivered across Australia · lighter two-person install`。

### 2. CTA 統一成兩條路徑

目前 CTA 有 `Design yours`、`Start your design`、`Talk to the atelier`，語意略分散。建議全站固定兩個主要 CTA：

- 主要 CTA：`Design my bathtub` / `開始設計`
- 次要 CTA：`Get free sample kit` / `索取免費材質包`

`$399 consultation` 不建議放在最前面當唯一 CTA。它應該出現在使用者完成初步設計、看過流程或有較高購買意圖之後。

### 3. Design Studio 變成轉換工具

目前 Design Studio 互動完成度高，但 lead capture 太晚。建議：

- 第 1 步選完外型後，出現 `Save my design` email bar。
- 第 3 步輸入尺寸後，顯示初步價格區間。
- 最後一步不要只有 `send`，改成三個下一步：
  - `Get a price estimate`
  - `Book $399 3D design`
  - `Send me a sample kit`

這樣可以捕捉不同成熟度的使用者，而不是只等最高意圖者送出完整表單。

### 4. 補完整 B2C 購買資訊

目前流程有 `$399 design consultation`，但 B2C 還需要更多決策資訊。建議在 `how-it-works.html` 或新增一頁 `pricing.html` 補上：

- 起價或典型專案價格範圍。
- $399 是否可退、如何折抵。
- 修改幾輪包含在內。
- 是否包含運費。
- 是否包含安裝。
- 生產前如何確認尺寸與圖面。
- 付款節點。
- 保固年限與保固範圍。
- 客製品退貨規則。
- 樣品包包含哪些內容。

### 5. 強化信任感

目前首頁有 testimonials，但比較像示意文案；作品集也多為 render。B2C 使用者會更在意真實性。建議增加：

- 工廠照片。
- 製程照片。
- 材料剖面圖。
- 包裝與配送照片。
- 真實安裝案例，哪怕先只有 1-2 個。
- 澳洲聯絡資訊、ABN、服務區域。
- 保固說明。
- 付款安全與資料隱私說明。

### 6. SEO 文章要接回精準 CTA

目前 SEO 文章方向很好，但每篇文章的 CTA 應該更貼近搜尋意圖。

- 尺寸文章：`Get a life-size floor template`
- 人體工學文章：`Design around your height`
- 材質文章：`Request acrylic + solid surface samples`
- freestanding vs built-in：`Check which tub fits your bathroom`

這樣文章不只是導流，而是精準收集 lead。

### 7. 分離 B2C 與 B2B 訊息

建議首頁、材質頁、流程頁以 B2C 屋主為主。設計師內容集中在 `designers.html`，並在導覽列保留 `For designers` 即可。

B2C 文案重點：

- 我的浴室適不適合？
- 我的身高泡起來舒不舒服？
- 多少錢？
- 多久到？
- 會不會很難安裝？
- 如果尺寸錯了怎麼辦？

B2B 文案重點：

- CAD-to-production。
- Trade pricing。
- White-label。
- Sample priority。
- Client presentation render。
- Installation photo credit。

兩者不要在同一段 Hero 裡混說。

## 建議的新首頁內容順序

1. Hero：B2C 主張 + 3D 浴缸 + 兩個 CTA。
2. Quick proof bar：起價、48h render、澳洲配送、無 MOQ。
3. How it works：3 步簡化版。
4. Design Studio preview：引導開始設計。
5. Materials：Acrylic vs Solid Surface，用消費者語言說明差異。
6. Price / timeline：給出清楚區間。
7. Trust：真實工廠、製程、安裝、保固。
8. Sample kit：免費樣品包與 life-size template。
9. FAQ：價格、交期、運費、安裝、保固、退貨。
10. Final CTA：開始設計 / 索取樣品包。

## 建議的短期執行順序

1. 先把首頁文案改成 B2C 屋主語言。
2. 全站 CTA 統一為 `Design my bathtub` 與 `Get free sample kit`。
3. 在首頁與流程頁補上價格區間、交期、付款節點、保固與配送說明。
4. 修改 Design Studio 最後一步，加入 estimate / consultation / sample kit 三種出口。
5. 補真實信任素材：工廠、製程、樣品、安裝、公司資訊。
6. 每篇 SEO guide 加上對應的 lead magnet CTA。
7. 之後再做 structured data、AI search friendly content、產品資料格式化。

## 結論

這個網站的視覺與互動基礎已經很好，真正要優化的是「商業轉換架構」。目前它看起來像高端品牌展示頁；下一步應該把它變成一個完整的 B2C 客製浴缸銷售漏斗。

最重要的方向是：

- 首頁只對屋主說清楚價值。
- 把設計師內容獨立出去。
- 提早回答價格、交期、保固、配送。
- 用 Design Studio 收 lead，而不只是展示互動。
- 用免費樣品包降低第一次行動門檻。
- 用 $399 3D consultation 承接高意圖客戶。

