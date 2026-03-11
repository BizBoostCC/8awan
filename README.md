# 八丫旺實業 官網改版 (8awan)

> 🔄 模擬改版 [bayawang.com.tw](https://www.bayawang.com.tw/) — 冷凍空調專家 × 政府採購供應商

## 專案概述

八丫旺實業有限公司（BAYAWANG CO., LTD.）成立於 2004 年，專營冷凍空調工程及冷氣家電產品，為台灣銀行政府採購指定供應商。本專案為其官方網站的視覺與結構改版設計。

## 技術架構

- **架構**：靜態 HTML + CSS + Vanilla JS（零依賴、零建構）
- **字型**：Google Fonts（Noto Serif TC、Bebas Neue、Noto Sans TC）
- **設計**：深海軍藍主色 + 橙色強調色，現代企業風格
- **部署**：Cloudflare Pages（自動部署 main 分支）

## 色彩系統

| Token | 色碼 | 用途 |
|-------|------|------|
| `--navy` | `#0a1628` | 主背景 |
| `--navy-mid` | `#132040` | 次背景（交替區塊） |
| `--steel` | `#1e3a5f` | Hover 狀態 |
| `--orange` | `#e8600a` | 品牌強調色 |
| `--orange-light` | `#ff7820` | Hover 強調色 |
| `--silver` | `#c5cdd8` | 主要文字 |
| `--muted` | `#7a8fa8` | 次要文字 |

## 頁面清單與進度

| 頁面 | 檔案 | 對應原站 | 狀態 |
|------|------|---------|------|
| 首頁 | `index.html` | `/` | ✅ 完成 |
| 關於我們 | `intro.html` | `/intro` | ⬜ 待開始 |
| 政府台銀採購 | `product_list.html` | `/product_list` | ⬜ 待開始 |
| 中央空調 | `service_list.html` | `/service_list` | ⬜ 待開始 |
| 品牌專區 | `link.html` | `/link` | ⬜ 待開始 |
| 實績案例 | `album_list.html` | `/album_list` | ⬜ 待開始 |
| 最新消息 | `news_list.html` | `/news_list` | ⬜ 待開始 |
| 工班招募 | `join.html` | `/join` | ⬜ 待開始 |

## 原站各頁面內容摘要

### `/intro` 關於我們
- 公司簡介與成立背景（2004 年）
- 三大特色：產品把關、專業服務、直接詢價
- 企業沿革時間軸
- 經營理念六宮格（品行、觀念、個人、公司、營運、技術）

### `/product_list` 政府台銀採購
- 7 大產品分類卡片：冷氣機、洗衣機、電冰箱、電視機、LED 燈具、飲水機、冷氣清洗保養
- 各含契約編號與終止日期
- 備註：價格僅供公家單位參考

### `/service_list` 中央空調
- 4 大服務項目：冰水主機系統、VRV 商用多聯變頻空調、箱型冷氣機、工程快速報價
- 卡片式佈局展示

### `/link` 品牌專區
- 15+ 合作品牌 Logo 展示（Panasonic、Hitachi、Sharp、LG、Sampo、Heran 等）
- 強調合作提升品質、縮短週期、降低成本

### `/album_list` 實績案例
- 分類篩選：中央空調工程、分離式冷氣機、機台遷移
- 案例卡片含工程照片（如高雄市農糧署、臺灣銀行新興分行）

### `/news_list` 最新消息
- 左側分類篩選（企業公告、促銷商品）+ 搜尋
- 熱門點閱排序
- 分頁導覽

### `/join` 工班招募
- 三階段申請流程：履歷審核 → 上傳案例 → 錄取通知
- Google 表單整合
- 誠徵冷凍空調工班技術人才

## 快速開始

```bash
# 本地預覽（任選一種）
npx serve .
python3 -m http.server 8080
open index.html
```

## 部署

推送至 `main` 分支即自動部署至 Cloudflare Pages。

## 授權

本專案為八丫旺實業有限公司委託之網站改版設計，所有權歸屬委託方。
