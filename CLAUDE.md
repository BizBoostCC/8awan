# CLAUDE.md — 八丫旺實業官網改版 (8awan)

## 專案定位

模擬改版 [bayawang.com.tw](https://www.bayawang.com.tw/) 的前端設計。目標是以現代深色企業風格重新設計所有頁面，展示冷凍空調專業形象。

## 技術架構

- **靜態 HTML + CSS + Vanilla JS**（零依賴、零建構）
- 每一頁是獨立的 HTML 檔案，CSS 內嵌在 `<style>` 標籤中
- 圖片使用 Unsplash（開發階段），正式版替換為客戶實拍照片
- 部署平台：Cloudflare Pages（push main 自動部署）

## 檔案結構

```
8awan/
├── index.html          ← 首頁（已完成）
├── intro.html          ← 關於我們（待做）
├── product_list.html   ← 政府台銀採購（待做）
├── service_list.html   ← 中央空調（待做）
├── link.html           ← 品牌專區（待做）
├── album_list.html     ← 實績案例（待做）
├── news_list.html      ← 最新消息（待做）
├── join.html           ← 工班招募（待做）
├── README.md
└── CLAUDE.md
```

## 設計系統（Design Tokens）

所有頁面必須遵循統一的 CSS 變數：

```css
:root {
  --navy: #0a1628;        /* 主背景 */
  --navy-mid: #132040;    /* 次背景（交替區塊） */
  --steel: #1e3a5f;       /* Hover 背景 */
  --orange: #e8600a;      /* 品牌強調色（CTA、標題重點） */
  --orange-light: #ff7820;/* Hover 強調色 */
  --silver: #c5cdd8;      /* 主文字色 */
  --white: #ffffff;       /* 標題文字 */
  --muted: #7a8fa8;       /* 次要文字、標籤 */
  --border: rgba(197,205,216,0.15); /* 分隔線 */
}
```

### 字型

- **標題**：`'Noto Serif TC', serif`（font-weight: 900）
- **數字/英文裝飾**：`'Bebas Neue', sans-serif`
- **內文**：`'Noto Sans TC', sans-serif`（font-weight: 300/400/500）

### 共用元件規範

每一頁都必須包含以下共用結構（從 index.html 複製）：

1. **`<nav>`**：固定頂部導航列，含 logo、導航連結、CTA 按鈕
2. **`<footer>`**：四欄式頁腳，含品牌、服務、關於、聯絡
3. **Section 標頭**：`.section-label` + `<h2>` 的固定格式
4. **CTA Strip**：橙底白字的報價呼籲區塊（可選，放在 footer 前）
5. **滾動動畫**：IntersectionObserver 驅動的 fadeUp 進場動畫

### 響應式斷點

- 桌面：預設樣式
- 平板/手機：`@media(max-width: 900px)` — 單欄佈局、隱藏導航連結

## 建立新頁面 SOP

當建立任何新頁面時，請嚴格遵循以下步驟：

### Step 1：複製骨架
從 `index.html` 複製完整的 `<head>`、`<nav>`、`<footer>`、`<script>` 區塊。

### Step 2：更新頁面專屬內容
- 修改 `<title>` 為該頁標題，格式：`頁面名稱｜八丫旺實業`
- 移除首頁的 `<section class="hero">` 區塊
- 新增頁面專屬的頂部 Banner（頁面標題 + 麵包屑導航）

### Step 3：參考原站內容
根據 README.md 中的「原站各頁面內容摘要」來規劃區塊。必要時用 WebFetch 抓取原站頁面獲取最新內容。

### Step 4：設計原則
- 保持深色企業風格的一致性
- 卡片式佈局用於列表頁（產品、服務、案例）
- Grid 佈局優先（`display: grid`），Flexbox 做對齊
- 圖片全部加 `filter: brightness(.65) saturate(.6)` 暗化處理
- Hover 效果：底部橙色線條滑入 + 背景亮化

### Step 5：頁面頂部 Banner 模板
每個子頁面都應有統一的頂部 Banner：

```html
<section class="page-banner">
  <div class="page-banner-bg"></div>
  <div class="page-banner-content">
    <div class="section-label">ABOUT US</div>
    <h1>關於我們</h1>
    <div class="breadcrumb">
      <a href="index.html">首頁</a> / <span>關於我們</span>
    </div>
  </div>
</section>
```

## 原站頁面資訊

### 公司基本資料
- **公司名**：八丫旺實業有限公司（BAYAWANG CO., LTD.）
- **成立年份**：2004 年
- **主營業務**：冷凍空調工程、冷氣家電產品
- **定位**：台灣銀行政府採購指定供應商
- **服務對象**：公家機關、軍公教單位、國營事業
- **Email**：bayawang1688@gmail.com
- **LINE**：https://lin.ee/rkTSbr4p

### 三大據點
| 據點 | 角色 | 地址 | 電話 | 傳真 |
|------|------|------|------|------|
| 高雄 | 總公司 | 鼓山區河西一路329巷12號 | 07-5327999 | 07-5320716 |
| 台中 | 中部據點 | 烏日區光日路5號、7號 | 04-23377810 | 04-23377820 |
| 台南 | 南部據點 | 永康區中山南路762巷2號 | 06-2029965 | — |

### 政府採購產品線（7 項）
1. 冷氣機（契約終止 115.3.31）
2. 洗衣機（契約終止 115/06/30）
3. 電冰箱（契約終止 115/06/30）
4. 電視機（契約終止 114/8/31）
5. 室內 LED 燈具（契約終止 114.12.31）
6. 飲水機（契約終止 114.8.31）
7. 冷氣機清洗保養

### 中央空調服務（4 項）
1. 冰水主機系統
2. VRV 商用多聯變頻空調
3. 箱型冷氣機
4. 工程快速報價

### 合作品牌
Panasonic、Hitachi、Sharp、LG、Sampo、Heran、Hotai、Hawrin、Tecohome 等 15+ 品牌

### 實績案例分類
- 中央空調工程（冰水主機系統、VRV、箱型冷氣機）
- 分離式冷氣機
- 機台遷移（含維護保養作業）
- 已知案例：高雄市農糧署、臺灣銀行新興分行

### 經營理念（六宮格）
品行、觀念、個人、公司、營運、技術

### 招募流程
1. 履歷審核（Google 表單 → 3 工作日內聯繫）
2. 上傳案例檔案（工程照片 + 文字敘述）
3. 錄取通知

## 導航連結對應

子頁面之間的導航連結應使用相對路徑：

```html
<a href="index.html">首頁</a>
<a href="intro.html">關於我們</a>
<a href="product_list.html">政府台銀採購</a>
<a href="service_list.html">中央空調</a>
<a href="link.html">品牌專區</a>
<a href="album_list.html">實績案例</a>
<a href="news_list.html">最新消息</a>
<a href="join.html">工班招募</a>
```

## 品質檢查清單

每完成一個頁面，確認以下項目：

- [ ] CSS 變數一致（使用 `:root` 定義的 token）
- [ ] 導航列連結完整且當前頁面有高亮
- [ ] 頁腳結構與首頁一致
- [ ] `@media(max-width: 900px)` 響應式正常
- [ ] IntersectionObserver 動畫套用
- [ ] 圖片有 alt 描述
- [ ] `<title>` 和 `<meta>` 正確
- [ ] 所有連結正確（相對路徑）
- [ ] CTA Strip 存在（footer 前）
- [ ] 滾動至頂部正常

## 禁止事項

- ❌ 不要使用任何 npm 套件或建構工具
- ❌ 不要引入 jQuery 或任何 JS 框架
- ❌ 不要使用 Tailwind CSS（保持手寫 CSS 的一致性）
- ❌ 不要使用簡體中文（全部使用繁體中文 zh-TW）
- ❌ 不要使用 emoji 在正式內容中（僅限 service-icon 裝飾用）
- ❌ 不要硬編碼真實客戶個資（Email、電話等已在本文件中列出的除外）

## Git 規範

- **Commit 格式**：`feat: 新增關於我們頁面` / `fix: 修正導航列 hover 效果`
- **語言**：中文 commit message
- **Co-author**：所有 AI 輔助的 commit 加上 `Co-Authored-By: Claude Opus 4.6 <noreply@anthropic.com>`
- **分支策略**：直接推送 `main`（Cloudflare Pages 自動部署）

## 版本紀錄

- **v0.1.0** (2026-03-11)：首頁改版完成，建立專案結構與文件
