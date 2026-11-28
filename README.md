# Threads 人物誌｜AI 人物研究實驗 v0.1

看到一個有趣的人，用 AI 幫你讀原文、理解一個概念，連結自己的經驗，形成自己的觀點。這不是人物排名，也不是已驗證有效的學習方法。

## 開始玩

1. 選一個真正感興趣的人，交給一個能讀公開來源的 AI，使用[研究提示詞](METHOD.md#研究提示詞)。
2. 讀回原始來源，挑一個想理解或想用在自己身上的概念；有重要疑問才找另一個 AI 補證。
3. 說出自己的想法，請 AI 有限度整理成文章；核對來源後，由本人決定是否發布。

可以先在一個對話中完成。想持續累積、比較人物或讓多個 AI 接續，再[下載空白研究桌](TEMPLATE.xlsx)，匯入 Google Sheets；在[方法與提示詞](METHOD.md)找到記錄方式。

不需要指定 AI、API、排程、資料庫、爬蟲或自行部署。AI 讀不到來源或無法寫表時，可以手動複製貼上，不能假裝已讀或已寫入。

**隱私：**只蒐集必要公開資料；私人研究桌、評分、私人對話及非公開帳號不公開。

## 研究案例

- [水球潘｜先有可修改的 SOP，再學習](examples/waterball/README.md)
- [CabLate｜先想清楚每次委派要換回什麼](examples/cablate/README.md)
- [黑貓老師｜先回答別人的問題，再發現可以提供的服務](examples/black-cat-teacher/README.md)
- [Bohr｜矽谷工程師的職涯與人生故事（未發布）](examples/bohr/README.md)
- [夏木 KRIS｜把舊文章重新組裝成新的爆文](examples/viregeek/README.md)
- [潘奕兆｜從設計教學走到 AI 一人公司](examples/pan-0709/README.md)
- [Vincent｜一個讓我願意讀完長文的創作者](examples/vincentyucw/README.md)
- [世豐老師｜三軍策略與經營 Threads 的目的](examples/richsong112/README.md)

- [炭治郎醫生｜歷史研究的保存](examples/tanjiro-doctor/README.md)
- [安迪｜知識型海巡回覆](examples/andyoo66/README.md)
- [Leon Lu｜人生經歷與創業試錯](examples/leon-lu/README.md)

案例保留研究觀察、公開證據及文章狀態；不代表已驗證方法成效。

## 人物誌公開網站｜維護接續

網站是獨立的作品典藏交付，不是進行人物研究的必要前提。維護或新增人物頁前，先核對正式 runtime 與以下架構遷移基線；發布由 Owner 決定。

### Static Assets 架構遷移基線（2026-11-28）

- 正式域名與既有文章不變。Cloudflare Worker `people-and-ideas-public` 於 2026-11-28 遷移至 asset-first Static Assets（`run_worker_first: false`）；HTML、字型、favicon、OG、robots、sitemap 由靜態層供應，既有計數 API 使用 Worker 與原 D1 `PAGE_VIEWS`，撤下路由仍採 fail-closed。不得以舊版內嵌資產 Worker 作為新部署基線或直接回滾。
- 遷移查核時 deployment `3769127d-4781-473c-946b-eedbadf57644`、version `0395e013-e77a-4740-9aef-b2f8ebea7c62` 100%；原網域與 D1 綁定保留，workers.dev / preview URLs 關閉。這是歷史驗收收據，不是持續有效的 runtime 狀態。
- 實際驗收：39 個 manifest 路徑，36 項直接檢驗的非 HTML 靜態資源逐位元一致；正式 HTML SHA-256 `a8cd82d3df0f97583d0e4f1d0b0cb6fc7b863546677bfc86445ede30593553bb`。當 Worker 額度仍耗盡（HTTP 429）時，正式頁及根網址、舊別名跟隨轉址均為 200；計數及撤下路由仍為 429。候選版撤下說明 410 已通過本機測試；正式 410 與計數恢復待額度重置後確認，不重設資料庫。
- 維護來源：Owner 私有工作區 `static-assets-migration-20261128` 的 `DEPLOYMENT-RECEIPT.md`、`wrangler.json`、`worker.mjs`、`public/`、`asset-manifest.json`、`live-verification.json`。以核對 runtime 後的候選版接續；不得整包公開私有工作區、資源識別碼、撤下路由識別資訊或部署憑證。公開封存不是部署授權。
- 此前的故障是所有路由消耗 Worker 額度，觀察到 Cloudflare 1027/429；確切流量組成與早期架構選擇原因未知。新增資產、計費依賴或變更託管架構時，使用 [Home 共用架構檢查](https://github.com/guoyutw/lulumi-home/blob/main/skills/deploy-architecture-check/SKILL.md)：核心功能隔離、資源/規模、權宜方案與退場。純內容或樣式小修不新增流程；不新增付費方案或重新部署，只為驗證。
- 歷史參考（不可當成現行部署來源）：[炭治郎脈絡修訂](website/releases/2026-11-28-tanjiro-context/README.md)、[瀏覽計數規格](website/releases/2026-11-27-views/README.md)、[共用品牌設計基線](website/releases/2026-11-27-brand/README.md)。新增頁面仍須保留既有計數及文章，遵守撤回原則。
