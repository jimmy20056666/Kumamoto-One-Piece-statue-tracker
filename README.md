<!-- STREAMING_CHUNK:Writing header and overview section... -->
# 🏴‍☠️ 熊本 ONE PIECE 銅像收集記錄 (Kumamoto ONE PIECE Statue Collector)

一個專為熊本 ONE PIECE 銅像巡禮打造的響應式網頁應用程式（PWA 友善）。結合互動式地圖、GPS 實時定位與自動近距離觸發提示，幫您在熊本旅遊期間輕鬆記錄草帽一伙 10 座銅像的收集進度！

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![HTML5](https://img.shields.io/badge/HTML5-Single--File-orange)
![TailwindCSS](https://img.shields.io/badge/TailwindCSS-v3-38bdf8)
![Leaflet](https://img.shields.io/badge/Leaflet-1.9.4-green)

---

<!-- STREAMING_CHUNK:Writing key features section... -->
## ✨ 功能特點

1. **🗺️ 明亮模式互動地圖**
   - 使用 CartoDB Voyager 圖層，清晰標示熊本 10 座 ONE PIECE 銅像位置。
   - 地圖設有自訂標記：未收集（灰色）與已收集（金色發光）。

2. **📍 GPS 實時定位與自動解鎖**
   - 實時追蹤使用者目前位置（藍色動態發光點）。
   - 地圖右上角設有「📍 定位」按鈕，點擊即可一鍵對焦至當前位置。
   - 當靠近未收集銅像 **100 公尺之內** 時，自動播放網頁合成和弦提示音，跳出慶祝彈窗並記錄解鎖！

3. **📊 收集清單與底部抽屜 (Bottom Sheet)**
   - 支援點擊標題列或**上下滑動**展開/收合清單。
   - 自動將未收集銅像排在前面，點擊任意項目地圖會自動平移並開啟資訊彈窗。
   - 即時顯示當前收集進度與百分比進度條。

4. **🗺️ Google Maps 導航整合**
   - 每座銅像的彈窗均包含一鍵開啟 Google Maps 導航的連結。

5. **🧪 測試與調適功能**
   - 彈窗提供「模擬到達」與「取消到達」按鈕，方便隨時測試與手動調整記錄。

6. **💾 本地進度儲存 (LocalStorage)**
   - 打卡進度自動儲存於手機瀏覽器，重新開啟網頁不會遺失記錄。

---

<!-- STREAMING_CHUNK:Writing statue list table... -->
## 🗺️ 銅像座標與清單

| 角色 | 職位 | 圖標 | 精確位置 | 座標 (Lat, Lng) |
| :--- | :--- | :---: | :--- | :--- |
| **魯夫 (Luffy)** | 船長 | 🍖 | 熊本縣廳 | `32.789025, 130.741307` |
| **喬巴 (Chopper)** | 船醫 | 🦌 | 熊本市動植物園 | `32.776130, 130.750413` |
| **布魯克 (Brook)** | 音樂家 | 💀 | 御船町恐龍博物館 | `32.714007, 130.805105` |
| **香吉士 (Sanji)** | 廚師 | 🍳 | 益城町交流資訊中心 | `32.786966, 130.823471` |
| **索隆 (Zoro)** | 劍士 | ⚔️ | 大津中央公園 | `32.877096, 130.871162` |
| **娜美 (Nami)** | 航海士 | 🍊 | 西原村 萌之里 | `32.842915, 130.939042` |
| **羅賓 (Robin)** | 考古學家 | 📖 | 東海大學阿蘇校區 | `32.891230, 130.995796` |
| **騙人布 (Usopp)** | 狙擊手 | 🎯 | 阿蘇車站 | `32.937003, 131.080303` |
| **佛朗基 (Franky)** | 船匠 | 🤖 | 高森車站 | `32.819227, 131.122628` |
| **吉貝爾 (Jinbe)** | 掌舵手 | 🦈 | 住吉海岸公園 | `32.704116, 130.581335` |

---

<!-- STREAMING_CHUNK:Writing setup and HTTPS warnings... -->
## 🚀 部署與手機使用說明 (重要)

⚠️ **為什麼手機無法取得 GPS 定位？**
現代手機瀏覽器（iOS Safari / Android Chrome）出於安全性考慮，**強制規定 Geolocation (GPS) API 必須在安全連線 (`https://`) 下才能運作**。
若直接將 `.html` 檔案下載到手機本機開啟 (`file:///...`)，手機會自動封鎖定位功能。

### 建議部署方式 (免費且快速)：

1. **GitHub Pages (推薦)**
   - 將 `index.html` 上傳至 GitHub 儲存庫 (Repository)。
   - 在 Settings -> Pages 開啟 GitHub Pages，幾秒後即可獲得免費的 `https://your-name.github.io/repository-name` 網址。

2. **Vercel / Netlify**
   - 將檔案拖曳上傳至 [Vercel](https://vercel.com/) 或 [Netlify](https://www.netlify.com/)，即可獲得 HTTPS 網址。

---

<!-- STREAMING_CHUNK:Writing tech stack and architecture section... -->
## 🛠️ 技術棧 (Tech Stack)

- **前端框架/樣式**: HTML5, [Tailwind CSS](https://tailwindcss.com/) (via CDN)
- **地圖渲染**: [Leaflet.js](https://leafletjs.com/) + CartoDB Voyager 瓦片
- **音效處理**: Web Audio API（無需加載任何外部 `.mp3` 音訊檔，由瀏覽器即時合成和弦）
- **數據持久化**: LocalStorage (`visitedOnePieceStatues`)
- **架構設計**: 單一 HTML 檔案獨立運行（Single-file Web App）

---

<!-- STREAMING_CHUNK:Writing troubleshooting and notes... -->
## ❓ 常見問題與解答 (FAQ)

- **Q: 抵達銅像附近時沒有聲音？**
  - 請確定進入網頁時有點擊「開始尋寶旅程」按鈕（這能解除瀏覽器的自動播放音效限制）。
  - 請確認手機未處於靜音模式或開啟主音量。

- **Q: 如何清除我的打卡進度？**
  - 您可以逐一在點擊銅像後按「取消到達」，或者清除手機瀏覽器的站點資料 (LocalStorage)。

- **Q: 距離銅像多近會自動解鎖？**
  - 系統內定預設為 **100 公尺 (0.1 km)**。

---

## 📄 授權條款 (License)

本專案採用 [MIT License](LICENSE) 授權。ONE PIECE 相關著作權與角色商標歸尾田榮一郎／集英社・富士電視台・東映動畫所有。