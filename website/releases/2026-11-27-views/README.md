# 人物誌｜累計瀏覽次數正式站封存

2026-11-27 20:50:25（Asia/Taipei）。Owner 核准公開計數功能及封存；不是下一次部署授權。

- 正式頁：https://people.lulumifish.com/tanjiro
- Worker：`people-and-ideas-public`
- Version：`6326c580-20dc-4493-92ac-0b3a58b0b835`，查核時 100% 流量。
- Deployment：`ad364ddc-77b1-4b33-a9da-04f904027d90`
- 上一版：[品牌基線](../2026-11-27-brand/README.md)（`c8f27199-b4ee-4e04-b6d9-583915a68000`）。
- [worker.js](worker.js)：正式運行原始碼，924624 UTF-8 bytes；SHA-256 `c19d0b6fe5f096ad698a2888a5e59a2d7f3926fbdcbc6560d13149ed1091cc6d`；Git blob `45d9b04e1be0c9deacab0071c7dc77136c009263`。
- 原始碼 commit `9442be56c82adb2b3794be3a1f976dc98873e6d6`，從 GitHub 指定 commit 讀回全文，與正式 Worker 原始碼逐字一致。

## 計數定義與接續方式

顯示「累計瀏覽 X 次」，置於人物名稱、帳號下方。不是不重複訪客人數。歷史基線是可取得的 Cloudflare Web Analytics 已入帳快照；後續使用 D1 獨立累計。不要把兩種計數方式說成完全相同，也不要承諾精確完整歷史總量。

Worker module，compatibility_date `2026-11-27`。新增 D1 binding `PAGE_VIEWS`，資料庫名稱 `people-and-ideas-views`，帳號內實際資源身分需在授權 runtime 重新核對，不在公開 repo 放帳號識別碼或管理憑證。

既有 schema（供參考；不可無條件重建正式表）：

```sql
CREATE TABLE page_views (
  slug TEXT PRIMARY KEY,
  historical INTEGER NOT NULL CHECK(historical>=0),
  tracked INTEGER NOT NULL DEFAULT 0 CHECK(tracked>=0),
  baseline_at TEXT NOT NULL
);
```

目前炭治郎列的 historical=69，baseline_at=2026-11-27T12:50:06Z；tracked 由 runtime 持續更新，封存不代表目前數字。歷史查詢窗口 2026-11-26T00:00:00Z 至 2026-11-27T23:59:59Z，Web Analytics `rumPageloadEventsAdaptiveGroups` 返回 /tanjiro count=69、avg.sampleInterval=1。遲到數據或漏計可能存在；不得將已知基線重設。

- GET /api/views/tanjiro 只讀，POST 原子累加 `UPDATE page_views SET tracked=tracked+1 WHERE slug=? RETURNING historical+tracked AS views`。
- 頁面可見時每份 document 送一次請求；重新整理可增加。拒絕缺少同源 Origin、Sec-Fetch-Site 或 JSON 的 POST；這不是完整防作弊措施。
- 不收集個人識別資訊；不承諾過濾全部機器人。讀取失敗顯示破折號，不填造數字。
- CSP connect-src 增加 self；修正既有 Analytics script 標籤的殘留文字，保留原網站分析標記。品牌字型、OG 圖、Favicon 與正文維持。

## 新增人物的檢查清單

1. 先讀本版與品牌基線，確認當前正式 Worker、D1 表及既有計數；不得用舊封存覆蓋持續變動的正式狀態。
2. 新人物採獨立 slug、獨立資料列、獨立 API 路徑或嚴格 allowlist；查明該頁歷史基線。無歷史資料的首次上線頁從零開始，若已有歷史而無法取得則標示起算日，不假稱完整累計。
3. 只新增該人物資料列，不覆蓋炭治郎；目前程式路由固定 tanjiro，須實作新路由才能接續。
4. 待審頁不發正式累計請求；公開部署仍須 Owner 核准。新增內容重新檢查字型字元覆蓋、獨立 OG 圖及共用 favicon。
5. 正式網址驗收：GET/HEAD 和純計數查詢不累加；同源實際瀏覽加一、畫面與 API 一致；外部 POST 拒絕；跨人物互不影響；手機版字型及排版正常；既有 OG 與內容不退化。記錄測試瀏覽與可能的並行流量。
6. 封存新版本及驗收結果，更新網站索引，不覆蓋舊版本。

## 實際驗收

- 375px Edge：兩套原始品牌 Web Font 載入；頁面無水平溢出。
- 69 → GET/HEAD、爬蟲 UA、缺同源標頭的 POST（403）後仍 69 → 實際瀏覽 POST 200 顯示 70 → 後續 GET 70。含一次測試瀏覽。
- OG 圖 SHA-256 `66148d02e86d2497468c9c45a0a9dc8e918b778c1fc80aa53d65727d82bf9f2c` 不變；favicon HTTP 200。
- Analytics beacon HTTP 200；新 RUM 事件是否入帳未核，Android 真機及高併發未獨立測試。
- 私人研究桌、原始擷取、未出版內容、管理憑證及資料庫實際 ID 均不封存至公開 repo。不備份持續變動的正式計數資料，不購買或升級方案；D1 依現有帳號方案及用量計價。
