# PayLonSon 作品集 ProjectHomePage 規格書

| 項目 | 內容 |
|---|---|
| 產品名稱 | PayLonSon 作品集（ProjectHomePage） |
| 文件版本 | v1.0 |
| 對應程式版本 | `main` 分支 `index.html` |
| 部署位置 | GitHub Pages（`https://paylonson.github.io/ProjectHomePage/`） |
| 原始碼 | `https://github.com/PayLonSon/ProjectHomePage` |
| 文件日期 | 2026-11-17 |

## 目錄

1. [目的](#1-目的)
2. [交付項目](#2-交付項目)
3. [功能要求](#3-功能要求)
4. [非功能要求](#4-非功能要求)
5. [輸出要求](#5-輸出要求)
6. [介面要求](#6-介面要求)
7. [安全要求／交易授權](#7-安全要求交易授權)
8. [其他要求](#8-其他要求)
9. [參考資料附錄](#9-參考資料附錄)

---

## 1. 目的

### 1.1 背景

作者在 GitHub Pages 上發布了多個網頁作品（遊戲與小工具），每個作品各有獨立的 repo 和網址，訪客不容易一次看到全部作品，也不知道每個作品是做什麼的。

### 1.2 目標

建立一個**單一入口的作品集網站**：

1. 集中介紹作者所有已發布與開發中的網頁作品。
2. 依內容**分類**（遊戲、小工具），可切換只看某一類。
3. 每個作品提供一句話說明、詳細介紹、特色標籤、遊玩／開啟連結與原始碼連結。
4. 新增作品只需修改一份資料清單，不需改版面程式。

### 1.3 適用範圍

| 範圍內 | 範圍外 |
|---|---|
| 作品介紹、分類瀏覽、外部連結 | 作品本身的功能（各自獨立 repo） |
| 手機與桌機瀏覽器 | 後台管理介面、CMS |
| 靜態網頁、手動編輯資料清單 | 自動從 GitHub API 抓取 repo 清單 |
| 繁體中文 | 多語系切換 |

### 1.4 名詞定義

| 名詞 | 說明 |
|---|---|
| 作品（Work） | 一個獨立發布的網頁遊戲或工具，對應 `works` 清單中的一筆 |
| 分類（Category） | 作品的類別，對應 `categories` 清單中的一筆，目前有 `game`、`tool` |
| 狀態（Status） | `live` 已上線（有可用連結）、`dev` 開發中 |
| 分類頁籤（Tab） | 頁面上切換顯示分類的按鈕：全部／遊戲／小工具 |
| 作品卡片（Card） | 顯示單一作品的區塊：封面、標題、說明、標籤、按鈕 |

### 1.5 收錄作品（v1.0）

| 分類 | 作品 | Repo | 狀態 |
|---|---|---|---|
| 遊戲 | 三扇門｜惡夢（DoorVault） | `PayLonSon/DoorVault` | 已上線 |
| 遊戲 | 大富翁 | `PayLonSon/Monopoly` | 已上線 |
| 小工具 | 分帳房 SplitRoom | `PayLonSon/SplitRoom` | 已上線 |

---

## 2. 交付項目

| 編號 | 項目 | 檔案／位置 | 說明 |
|---|---|---|---|
| D-1 | 網頁 | `index.html` | 單一檔案，含 HTML、CSS、JavaScript 與作品資料，無需建置 |
| D-2 | 圖片資源 | `images/` | 作品封面圖（目前 `doorvault.png`） |
| D-3 | Jekyll 停用檔 | `.nojekyll` | 讓 GitHub Pages 直接提供原始檔 |
| D-4 | 說明文件 | `README.md` | 作品列表、網站網址、新增作品方式 |
| D-5 | 規格書 | `SPEC.md` | 本文件 |
| D-6 | 原始碼庫 | GitHub `PayLonSon/ProjectHomePage` | `main` 分支 |
| D-7 | 線上服務 | GitHub Pages | `main` 分支根目錄部署 |

**驗收條件**

- 以手機與桌機瀏覽器開啟線上網址，可看到 §1.5 全部作品。
- 點擊分類頁籤只顯示該分類作品；「全部」顯示所有分類。
- 每個「已上線」作品的遊玩／開啟按鈕與原始碼按鈕都能開啟正確網址。
- 在 `works` 清單新增一筆後重新整理，新作品出現在對應分類，計數同步更新。

---

## 3. 功能要求

### 3.1 功能總覽

| 編號 | 模組 | 功能 |
|---|---|---|
| F-1 | 首屏 | 標語、簡介、看看作品／GitHub 按鈕 |
| F-2 | 分類頁籤 | 全部／各分類切換、作品數量、固定於頂端 |
| F-3 | 作品列表 | 依分類分組、狀態排序、空狀態 |
| F-4 | 作品卡片 | 封面、狀態標籤、標題、說明、標籤、按鈕 |
| F-5 | 網址分類 | 以網址 `#分類ID` 直接開啟某分類 |
| F-6 | 製作原則 | 四項理念說明 |
| F-7 | 頁尾 | 版權年份、回報方式 |

### 3.2 F-1 首屏

| 編號 | 規則 |
|---|---|
| F-1.1 | 顯示標籤「PORTFOLIO」、主標「打開瀏覽器，馬上就能用。」、一段簡介 |
| F-1.2 | 「看看作品 ↓」捲動到作品區（`#works`） |
| F-1.3 | 「GitHub」以新分頁開啟 `https://github.com/PayLonSon` |

### 3.3 F-2 分類頁籤

| 編號 | 規則 |
|---|---|
| F-2.1 | 第一個頁籤固定為「✨ 全部」，其後依 `categories` 順序產生 |
| F-2.2 | 每個頁籤顯示作品數量：「全部」為 `works` 總數，其他為該分類筆數 |
| F-2.3 | 目前選取的頁籤以主色底白字標示 |
| F-2.4 | 點擊頁籤立即重繪列表，不重新載入頁面 |
| F-2.5 | 頁籤列於捲動時固定在畫面頂端（`position: sticky`） |

### 3.4 F-3 作品列表

| 編號 | 規則 |
|---|---|
| F-3.1 | 「全部」時依 `categories` 順序逐一顯示每個分類區塊；選某分類時只顯示該區塊 |
| F-3.2 | 每個分類區塊顯示圖示、名稱與一句說明 |
| F-3.3 | 區塊內作品排序：`live` 在前、`dev` 在後；同狀態維持清單原順序 |
| F-3.4 | 分類下沒有作品時顯示「還沒有作品，敬請期待。」 |

### 3.5 F-4 作品卡片

| 欄位 | 規則 |
|---|---|
| 封面 | `cover` 有值時顯示圖片（預設為置中圓角圖示樣式）；無值時以 `coverColor` 漸層底加 `coverText` 大字 |
| 狀態標籤 | 封面左上角：`● 已上線`（綠）／`◐ 開發中`（黃） |
| 標題 | `title` |
| 副標 | `tagline`，強調色 |
| 介紹 | `desc` |
| 特色標籤 | `features` 逐一顯示為膠囊標籤 |
| 主按鈕 | `link` 有值：遊戲顯示「▶ 立即遊玩」、小工具顯示「↗ 開啟工具」，新分頁開啟；無值：顯示不可點的「即將推出」 |
| 原始碼按鈕 | `repo` 有值才顯示「原始碼」，新分頁開啟 |
| 卡片尺寸 | 遊戲為大卡（封面寬 300px）；小工具為小卡（封面寬 200px） |

### 3.6 F-5 網址分類

| 編號 | 規則 |
|---|---|
| F-5.1 | 載入時若網址 hash 等於某分類 ID（如 `#tool`），預設選取該分類；否則選「全部」 |
| F-5.2 | 切換頁籤時以 `history.replaceState` 更新網址：選分類為 `#分類ID`，選全部則移除 hash |
| F-5.3 | 更新網址不新增瀏覽紀錄，按返回鍵不會在頁籤間來回 |

### 3.7 F-6 製作原則

固定顯示四張說明卡：⚡ 免安裝、📱 手機優先、⏱ 輕量快速、🔄 持續更新。

### 3.8 F-7 頁尾

| 編號 | 規則 |
|---|---|
| F-7.1 | 左側「© {今年} PayLonSon」，年份以瀏覽器時間自動帶入 |
| F-7.2 | 右側「有建議或發現 bug？歡迎到 GitHub 開 Issue。」 |

### 3.9 例外處理

| 情境 | 處理 |
|---|---|
| 作品 `category` 不在 `categories` 中 | 不顯示於任何分類區塊，但計入「全部」數量（維護時應避免） |
| 封面圖片載入失敗 | 顯示瀏覽器預設破圖，`alt` 為「{作品名} 截圖」 |
| `features` 為空陣列 | 不顯示標籤 |
| 外部作品網址失效 | 本站不偵測，由維護者手動更新 |
| JavaScript 停用 | 作品區不顯示；首屏、製作原則、頁尾仍可閱讀 |

---

## 4. 非功能要求

| 類別 | 要求 |
|---|---|
| 可用性 | 開啟網址即可瀏覽，無需登入、無彈窗 |
| 相容性 | iOS Safari 15+、Android Chrome 100+、桌機 Chrome／Edge／Firefox／Safari 近兩版 |
| 效能 | 首頁 HTML 約 20 KB，無外部 CSS／JS／字型相依；4G 網路下首次載入 ≤ 2 秒 |
| 響應式 | 寬度 ≤ 720px 時卡片改為上下排列；內容最大寬度 1040px 置中 |
| 可維護性 | 版面與資料分離：新增作品只改 `works`，新增分類只改 `categories` |
| 可攜性 | 純靜態檔案，可部署於任何靜態主機 |
| SEO／分享 | 設定 `description`、`og:title`、`og:description` |
| 成本 | 不使用付費服務，營運成本 0 元 |

---

## 5. 輸出要求

### 5.1 畫面輸出

| 輸出 | 格式 |
|---|---|
| 頁籤 | `{圖示} {分類名}{數量}`，例：`🎮 遊戲 2` |
| 狀態 | `● 已上線`／`◐ 開發中` |
| 主按鈕 | `▶ 立即遊玩`／`↗ 開啟工具`／`即將推出` |
| 頁尾 | `© 2026 PayLonSon` |

### 5.2 網址輸出

| 情境 | 網址 |
|---|---|
| 全部 | `https://paylonson.github.io/ProjectHomePage/` |
| 只看遊戲 | `https://paylonson.github.io/ProjectHomePage/#game` |
| 只看小工具 | `https://paylonson.github.io/ProjectHomePage/#tool` |

### 5.3 作品資料格式（`works`）

```js
{
  category: "game",          // 必填，對應 categories 的 id
  title: "三扇門｜惡夢",      // 必填
  tagline: "一句話說明",       // 必填
  status: "live",            // 必填，live | dev
  cover: "images/xxx.png",   // 選填，空字串則用色塊
  coverText: "門",           // cover 為空時顯示的字或 emoji
  coverColor: "linear-gradient(135deg,#3a0d12,#120607)", // 封面底色（CSS background）
  desc: "詳細介紹",           // 必填
  features: ["標籤1", "標籤2"], // 特色標籤，可為空陣列
  link: "https://...",       // 選填，空字串顯示「即將推出」
  repo: "https://github.com/..." // 選填，空字串不顯示原始碼按鈕
}
```

### 5.4 分類資料格式（`categories`）

```js
{ id: "game", name: "遊戲", icon: "🎮", sub: "一局幾分鐘的網頁遊戲，手機就能玩。" }
```

---

## 6. 介面要求

### 6.1 使用者介面（UI）

**畫面結構**

```
首屏（Hero）
 ├─ PORTFOLIO／主標／簡介
 └─ [看看作品 ↓] [GitHub]
作品區（#works）
 ├─ 分類頁籤：✨全部｜🎮遊戲｜🛠小工具（捲動時固定頂端）
 └─ 分類區塊 × N
       └─ 作品卡片 × N：封面＋狀態｜標題／副標／介紹／標籤／[主按鈕][原始碼]
製作原則（4 張卡）
頁尾
```

**設計規範**

| 項目 | 規範 |
|---|---|
| 主題 | 深色 |
| 背景 | `#0d0f14`；卡片 `#161a22`；框線 `#262c38` |
| 文字 | 主文字 `#e8e6e1`；次要 `#9097a3` |
| 強調色 | 主色 `#e5484d`（紅）；副色 `#f5b544`（黃） |
| 狀態色 | 已上線 `#5be49b`（綠）；開發中 `#f5b544`（黃） |
| 字型 | 系統字型（Noto Sans TC／PingFang TC／微軟正黑體） |
| 圓角 | 卡片 16px；按鈕 10px；頁籤與標籤全圓角 |
| 點擊區 | 按鈕與頁籤高度 ≥ 40px |
| 互動回饋 | 按鈕滑過上移 2px |
| 斷點 | 720px：卡片由左右改為上下排列 |

### 6.2 系統介面

| 介面 | 用途 | 說明 |
|---|---|---|
| GitHub Pages | 網站託管 | `main` 分支根目錄，HTTPS |
| 各作品 GitHub Pages | 外部連結 | `https://paylonson.github.io/{Repo}/` |
| 各作品 GitHub repo | 外部連結 | `https://github.com/PayLonSon/{Repo}` |
| `history.replaceState` | 更新網址 hash | 不新增瀏覽紀錄 |
| `location.hash` | 讀取預設分類 | 載入時一次 |

本站不呼叫任何 API、不載入第三方腳本。

---

## 7. 安全要求／交易授權

### 7.1 交易性質聲明

本網站**只做作品介紹，不含任何交易**：無購買、無付款、無廣告、無會員、無表單，不保存任何金融或個人資料。

### 7.2 操作授權

| 項目 | 規則 |
|---|---|
| 瀏覽 | 公開，任何人都可瀏覽，不需身分驗證 |
| 內容修改 | 只有對 `PayLonSon/ProjectHomePage` 有寫入權限的人能透過 Git 推送修改 |
| 發布 | 推送到 `main` 即自動發布；建議重大修改先在分支確認再合併 |

### 7.3 資料安全

| 項目 | 措施 |
|---|---|
| 資料蒐集 | 不使用 Cookie、localStorage、追蹤碼或分析服務 |
| 傳輸 | 全站經 GitHub Pages HTTPS 提供 |
| 輸出跳脫 | 作品資料寫入畫面前一律做 HTML 跳脫（`& < > "`），防止資料內容造成 XSS |
| 外部連結 | 一律 `target="_blank"` 並加 `rel="noopener"`，避免新分頁操控原頁面 |
| 第三方相依 | 無外部 CDN 腳本、樣式或字型 |

### 7.4 已知安全限制

- `coverColor` 直接寫入 `style` 屬性未做跳脫，僅限維護者填寫可信值。
- 外部作品網址的內容與安全性由各作品自行負責，本站不檢查。

---

## 8. 其他要求

### 8.1 部署

1. 將 `index.html`、`images/`、`.nojekyll`、`README.md`、`SPEC.md` 推到 `main` 分支根目錄。
2. GitHub repo → Settings → Pages → Deploy from a branch → `main` / `(root)`。
3. 部署後網址：`https://paylonson.github.io/ProjectHomePage/`。
4. 各作品 repo 也需各自開啟 Pages，作品連結才能使用。

### 8.2 新增作品流程

1. 作品 repo 開啟 GitHub Pages，確認網址可用。
2. 有截圖或圖示時放入 `images/`。
3. 在 `index.html` 的 `works` 清單加一筆（格式見 §5.3）。
4. 若需要新分類，在 `categories` 加一筆（格式見 §5.4）。
5. 同步更新 `README.md` 作品表格與本文件 §1.5。
6. 推送到 `main`，等待 1–2 分鐘後確認線上版本。

### 8.3 測試要求

| 類別 | 測試項目 |
|---|---|
| 分類 | 三個頁籤切換正確；數量正確；`#game`、`#tool` 直接開啟正確；無效 hash 回到全部 |
| 排序 | 同分類中 `live` 排在 `dev` 前 |
| 卡片 | 有／無封面圖、有／無 `link`、有／無 `repo` 四種組合顯示正確 |
| 連結 | 所有外部連結以新分頁開啟且網址正確 |
| 響應式 | 375px（手機）、768px（平板）、1280px（桌機）版面正常 |
| 跳脫 | 在測試資料中放入 `<b>` 等字元，畫面顯示為文字而非 HTML |
| 相容 | iOS Safari、Android Chrome 實機瀏覽 |

### 8.4 已知限制

- 作品清單需手動維護，不會自動同步 GitHub repo。
- 作品網址失效時不會自動偵測或隱藏。
- 只有繁體中文。
- 大富翁、分帳房尚無截圖，以色塊加 emoji 作為封面。

### 8.5 後續擴充方向

| 優先 | 項目 |
|---|---|
| 高 | 為每個作品補上截圖或示範 GIF |
| 高 | 新作品上線後加入列表（如規劃中的「火柴人地城 StickDungeon」） |
| 中 | 作品詳細頁（更多截圖、更新紀錄） |
| 中 | 搜尋或標籤篩選 |
| 低 | 英文版 |
| 低 | 從 GitHub API 自動帶入最後更新時間 |

### 8.6 版本紀錄

| 版本 | 日期 | 內容 |
|---|---|---|
| v1.0 | 2026-11-17 | 初版：分類頁籤、作品卡片、網址分類；收錄 DoorVault、大富翁、分帳房 |

---

## 9. 參考資料附錄

### 9.1 收錄作品連結

| 作品 | 線上網址 | 原始碼 |
|---|---|---|
| 三扇門｜惡夢 | https://paylonson.github.io/DoorVault/ | https://github.com/PayLonSon/DoorVault |
| 大富翁 | https://paylonson.github.io/Monopoly/ | https://github.com/PayLonSon/Monopoly |
| 分帳房 SplitRoom | https://paylonson.github.io/SplitRoom/ | https://github.com/PayLonSon/SplitRoom |

### 9.2 技術文件

| 資料 | 網址 |
|---|---|
| GitHub Pages 文件 | https://docs.github.com/pages |
| MDN History.replaceState() | https://developer.mozilla.org/zh-TW/docs/Web/API/History/replaceState |
| MDN position: sticky | https://developer.mozilla.org/zh-TW/docs/Web/CSS/position |
| MDN rel="noopener" | https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes/rel/noopener |
| Open Graph 協定 | https://ogp.me/ |

### 9.3 各作品規格書

| 作品 | 規格書 |
|---|---|
| 分帳房 SplitRoom | `SplitRoom` 規格書 v1.2 |
| 火柴人地城 StickDungeon（規劃中） | `StickDungeon` 規格書 v0.2 |

### 9.4 新增作品範例

```js
,{
  category: "tool",
  title: "工具名稱",
  tagline: "一句話說明",
  status: "live",
  cover: "",
  coverText: "工",
  coverColor: "linear-gradient(135deg,#3a2f12,#141007)",
  desc: "這個工具能幫你做什麼。",
  features: ["標籤1", "標籤2"],
  link: "https://paylonson.github.io/你的repo/",
  repo: "https://github.com/PayLonSon/你的repo"
}
```
