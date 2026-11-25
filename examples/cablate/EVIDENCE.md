# 公開證據｜CabLate

以下為 2026-11-24～25 研究選取的代表性來源及本輪查核紀錄。代號僅用於本案例內部對照 [INSIGHTS.md](INSIGHTS.md)，不代表私人研究桌的原始 ID。A/B/C 為證據類型，不是人物評價。Threads 相對日期為當時顯示，未換算為精確發文時間。

## 官網：背景與工作方法

| 代號 | 來源 | 摘要 | 證據邊界 |
|---|---|---|---|
| C01 | [個人介紹](https://cablate.com/about/) | 從全端工程、系統設計與產品實作轉向 AI；本人稱 2025-06 起全職經營 CabLate。 | B／本人官網自述，已核讀；不代表獨立履歷或商業成效驗證。 |
| C02 | [派子代理之前，先想清楚要換回甚麼](https://cablate.com/articles/subagent-what-to-get-back/)・2026-10-30 | 分工的成本包含重複讀取、摘要交接、驗收及返工；作者自述記錄每次對話 token，並以委派預期回報判斷是否需要子代理。 | B／本輪取得文章搜尋索引的完整正文，直開頁面未成功；文章中的用量及經驗是作者自述，未核原始紀錄、帳單或比較實驗。 |
| C03 | [子代理模型守門](https://cablate.com/articles/subagent-model-hook-guard/)・2026-11-01 | 在呼叫子代理時檢查模型選擇，將一部分規則由文字提醒移至 Hook。 | B／本輪核讀索引摘錄，未完整核讀腳本或實際效果。 |

## Threads：自己發文與回覆別人的判斷

| 代號 | 來源 | 摘要 | 證據邊界 |
|---|---|---|---|
| C04 | [Agent 與 Skills](https://www.threads.com/@cab_late/post/DgJTvZrH8II) | 回覆單一通用 Agent 的論點，強調分工作區的價值在於容易管理及隔離適用的 Skills，不是單純能力特化。 | B／本輪瀏覽器核讀本人回覆及上文；觀點非比較效能實驗。 |
| C05 | [語言檢查 Stop Hook](https://www.threads.com/@cab_late/post/DgCruLZGC_7) | 作者稱 Claude Code 回覆混用語言時，自己寫 Hook 檢查非繁中比例，超過門檻要求再出中文版。 | B／核讀回覆，自述；沒有公開該 Hook 的原碼、日誌或改善量。 |
| C06 | [上下文與文件管理](https://www.threads.com/@cab_late/post/DgCgEEYGJwO) | 主張按需要提供脈絡，重視文件架構及把對話所得落成文件。 | B／核讀回覆；未核其所回應論文的實驗數字，不當成作者本人的實驗。 |
| C07 | [AI 使用健檢](https://www.threads.com/@cab_late/post/DgCV26YmA-n) | 與黑貓老師交流，澄清想幫人檢視怎麼使用 AI。 | B／核讀本人回覆及上文；此回覆是服務意向，不能證明交付或付費成果。 |
| C08 | [農會職員的 AI 實作](https://www.threads.com/@cab_late/post/DgCRqchGNKs) | 作者分享帶有實務經驗的職員入門後開始討論部門流程調整。 | B／核讀回覆，自述；所稱效率改善未取得學員、工作量或獨立結果證明。 |
| C09 | [不必重寫 Slack](https://www.threads.com/@cab_late/post/DgCRPd7GBho) | 對以 AI 重寫既有企業工具的主張，指出 Slack 已經能與 AI 配合。 | B／核讀簡短回覆；不是完整自建／採購評估。 |
| C10 | [從對話到能離開電腦](https://www.threads.com/@cab_late/post/DgCStxTmJWa) | 初期可能需要長時間與 AI 互動，之後希望讓它自行運作，自己去做其他事。 | B／核讀回覆，自述；不證明實際已節省多少時間。 |

## GitHub：可直接檢視的工程實作

以下三項以固定 commit `117a3c21e1e17e6d883cb15af99b7b347a6f78e7` 的原碼為依據，本輪已重新讀取指定行；不是即時部署證據。

| 代號 | 來源 | 可確認的範圍 | 仍未知 |
|---|---|---|---|
| C11 | [資訊 ACK service L160–186](https://github.com/cablate/cabai/blob/117a3c21e1e17e6d883cb15af99b7b347a6f78e7/src/lib/services/user-information-service.ts#L160-L186) | B／原碼：資訊 ID 去重、數量與可見性檢查；以資料庫交易記錄使用者 ACK，重複插入忽略。 | ACK 只代表確認讀取，不代表完成工作；未驗證正式環境。 |
| C12 | [備份 service](https://github.com/cablate/cabai/blob/117a3c21e1e17e6d883cb15af99b7b347a6f78e7/src/lib/database-backup/service.ts#L105-L122)（另見 L36–54） | B／原碼：先檢查備份完整性再提交；保留數量先驗證再列舉及移除備份。 | 未核所有呼叫端、排序或實際復原；有檢查不等於復原成功。 |
| C13 | [資訊整合測試 L131–173](https://github.com/cablate/cabai/blob/117a3c21e1e17e6d883cb15af99b7b347a6f78e7/src/lib/__tests__/information-service.integration.test.ts#L131-L173) | B／原碼：測試摘要與全文邊界、使用者 ACK、重複 ACK、無權限拒絕。 | 本輪未執行測試；測試存在不能證明目前運行成功或使用成效。 |

以上是有限選樣，不是完整履歷或工程評鑑。引用作者精確措辭前，請重新開啟原始來源；不把自述、程式碼、實際運行與成效混為一談。
