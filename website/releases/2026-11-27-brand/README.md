# People & Ideas｜正式公開站封存 2026-11-27

本目錄是 Owner 核准的**既有公開站**封存，不是新的發布、部署或自動化授權。

- 正式站：https://people.lulumifish.com/tanjiro
- Worker：`people-and-ideas-public`
- 部署時間：2026-11-27 20:12:06（Asia/Taipei）
- Deployment：`7207ff92-5335-425e-9dd5-8bc3e7181cc2`
- Version：`c8f27199-b4ee-4e04-b6d9-583915a68000`（查核時 100% 流量）
- 前一版本：`4d792bd0-8b43-4a99-a0cb-673d8d5d8e6e`
- 原始碼封存 commit：`c8fe983050daa83947d47d82c4cc17592c72a859`
- [worker.js](worker.js)：直接從正式 Worker 下載的 module 原始碼，922376 UTF-8 bytes。
- SHA-256：`0a2d6b04e41931e546d67c71b243c0713e38f539cf9db11e680e898682628b17`。
- Git blob SHA：`f61a6c82d5ef7619280a4eb4a87c14dff5f26c22`。
- 封存驗證：以 commit 指定 GitHub 讀回全文，與 Cloudflare 正式 Worker 原始碼逐字一致。

## 共用設計基線

| 項目 | 目前正式站 |
|---|---|
| 標題與品牌字 | 獅尾四季春加糖 Swei Spring Sugar CJK TC SemiBold 600 |
| 正文、引文及一般介面 | 宙黑體 ZevHeiTC-F Web |
| 配色 | 米白 #f6f2e9、深藍 #1d3550；保留現有深色模式 |
| Favicon | 原始四季春「人」字形、深藍底米白字；SVG、PNG、ICO |
| OG 封面 | 炭治郎專屬 1200×630 JPEG |
| 字型供應 | 同源 WOFF2 分割子集、unicode-range，保留 OFL 授權與來源聲明 |

Worker 內嵌目前公開頁面、分享封面及 33 個品牌資產（580155 bytes）；可由同源路由提供。字型子集針對此頁內容製作，不等於全字庫，新增人物時須重新核對字元覆蓋。OFL 授權及來源說明由 `/brand/fonts/NOTICE.txt`、兩字型目錄的 `LICENSE.txt` 提供。

## 執行設定與驗收

Cloudflare module Worker；入口 `worker.js`，compatibility_date `2026-11-27`，無額外 bindings，未使用獨立靜態資產 binding。封存本身不建立 CI/CD，也不攜帶部署憑證。

- 正式頁 HTML 與核准本機候選逐字一致；33/33 新增資產公開 HTTP、MIME、SHA-256 通過。
- Chromium CDP 實際渲染檢查：375px、1440px 兩種尺寸均無水平溢出；header/h1/h2/h3 實際使用 Swei Spring Sugar CJK TC，段落與引文使用 ZevHeiTC-F。原有特殊符號 ↗、🤣 使用系統備援。
- 原 OG 圖 SHA-256 未變：`66148d02e86d2497468c9c45a0a9dc8e918b778c1fc80aa53d65727d82bf9f2c`。
- 原文章、canonical、analytics markup 保留。驗證時分析請求被隔離，實際 analytics 入帳未測。
- Threads 舊貼文 Favicon 快取與 Android 真機尚未獨立驗證。

## 封存邊界

只收錄已核准公開的正式 Worker 和此部署說明；不收私人研究桌、原始擷取、私有對話、未出版人物內容、API 憑證或帳號資料。原始碼內公開網站分析標記原樣保存，不新增管理憑證。後續發布需依原專案證據與 Owner 核准，不從本封存自動部署。
