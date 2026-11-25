# 公開證據｜Bohr

查閱日期：2026-11-25。以下是本輪直接核讀的公開資料與必要限制；部分來源為主串內作者回覆。代號供本案例對照。證據分類依 [方法](../../METHOD.md#證據邊界)。核讀原文只確認公開說法存在，並不獨立驗證作者的履歷、經歷、內心狀態或工程成效。

## 人物與人生故事

| 代號 | 來源 | 觀察 | 證據與限制 |
|---|---|---|---|
| B01 | [Threads 帳號](https://www.threads.com/@bohr_cc) | 公開自介為 Bohr，稱 Bay Area 打工仔。 | B／自述；未核現職。 |
| B02 | [置頂 AMA](https://www.threads.com/@bohr_cc/post/De0PIFemULd)・2026-10-23 | 自述矽谷 13 年以上經歷，由 new grad 至 staff，列六家科技公司，曾裸辭休息一年。 | B／自述；公司順序、時段未核。 |
| B03 | [人生價值與裸辭](https://www.threads.com/@bohr_cc/post/De0oErnmwuX)・2026-10-23 | 被問拿掉公司光環及職稱後的價值，坦言曾因類似迷惘裸辭，仍未找到答案。 | B／自述；裸辭細節及完整時序未知。 |
| B04 | [五家公司文化速寫](https://www.threads.com/@bohr_cc/post/De0gDbQG7EK)・2026-10-23 | 比較 Google、Meta、Stripe、Vercel、OpenAI 的工作文化。 | C／個人觀察；非公司普遍定論。 |
| B05 | [工作以外的目標](https://www.threads.com/@bohr_cc/post/De2vnSlj2st)・2026-10-24 | 被問下一步職涯規劃，回答高爾夫單差點、網球 3.5、日文程度與英文同等。 | B／目標自述；未確認達成。 |
| B06 | [青春回憶](https://www.threads.com/@bohr_cc/post/DZI07N1khF2)・2026-06-04（台灣時間） | 回憶小福樓前的迷惘、單車環島、舞社謝幕及擎天岡。 | B／自述；原文 datetime 為 2026-06-03T20:55:56Z；回憶發生年份、學校科系未知。 |
| B07 | [面試近一年](https://www.threads.com/@bohr_cc/post/C56wTDIyzmq)・2024-04-19 | 回顧過去一年幾乎都在面試，多為 staff 職位；強調經驗匹配、技術與軟實力。 | B／自述；面試及 offer 數、最後任職公司未知。 |
| B08 | [Agentic work 與職業倦怠](https://www.threads.com/@bohr_cc/post/DWTDVMclZpt)・2026-03-25 | 表示兩年前加入 OpenAI 做 applied work 並未特別興奮，agentic work 讓職業倦怠似乎大幅改善；偏好整體系統設計。 | B／自述；不推定離職原因、現職或倦怠已完全消失。 |
| B09 | [高爾夫球場的反思](https://www.threads.com/@bohr_cc/post/DevQojnG79M)・2026-10-21 | 觀察球友悠閒聊天、更在意啤酒，反省不必將競爭心態帶進球場。 | B／個人反思；未核生活或球技的實際改變。 |
| B10 | [返台時的望春風](https://www.threads.com/@bohr_cc/post/C64XDZdyfYr)・2024-05-13（台灣時間） | 自述久居國外後，返台落地聽到這首歌常熱淚盈眶。 | B／公開自述；不推測家庭組成、返台計畫或定居狀態。 |

## 工程與共筆研究（補充）

| 代號 | 來源 | 觀察 | 證據與限制 |
|---|---|---|---|
| B11 | [資安審查案例](https://www.threads.com/@bohr_cc/post/DfL2RgbG3R6)・2026-11-01 | 原估四週以上搬遷，釐清跨 app secrets 隔離風險後改提只拆 tool layer，作者稱不到一週完成 review。 | B／自述；審查不等於已驗證部署或長期安全成效。 |
| B12 | [告警 Agent](https://www.threads.com/@bohr_cc/post/DdsqAHUlBl6)・2026-09-25 | 固定檢查與已知參數交程式，模型解讀 metrics/logs，人審系統變更。 | B／架構自述；未核量化可靠性。 |
| B13 | [告警 Agent 的驗收缺口](https://www.threads.com/@bohr_cc/post/DeOMc6sFAr6)・2026-10-08 | 參數可以確定性驗證，但建議的證據是否充分仍需將人工回饋整理成 eval 案例。 | B／自述；留言者 owntheblueprint 建議檢查 evidence set 及反證訊號，非 Bohr 已實作。 |
| B14 | [參數化工具與驗收](https://www.threads.com/@bohr_cc/post/DfHo-HZj1Rc)・2026-10-30 | 固定 query 工具有助縮小權限及工具呼叫 eval 的範圍。 | B／設計觀點；無量化成效。 |
| B15 | [Orchestration 的取捨](https://www.threads.com/@bohr_cc/post/De-zcqxm6oi)・2026-10-27 | 確定性分工、模型獨立、路由及維護成本；現成 harness 對簡單任務可能足夠。 | B／原文及作者回覆；不宣稱必須自建。 |
| B16 | [安全風險](https://www.threads.com/@bohr_cc/post/Df8q86BEXjL)・2026-11-20 ｜ [共筆自串](https://www.threads.com/@bohr_cc/post/Df8q9WAkfv0) | 通用 SQL 與固定工具權限差異；介紹課堂 CaMeL。自述共筆有 140+ 志願者及 40+ field notes，課後公開 LLM Wiki 為計畫。 | B／自述與課程內容；CaMeL 非其已驗證實作，數字與 Wiki 完成狀態未獨立核實。 |
| B17 | [Eval 與終態](https://www.threads.com/@bohr_cc/post/DfqWt9DEWw7)・2026-11-13 | 課堂整理：查實際終態、區分至少一次成功與連續成功。 | B／課程摘要，非本人量化成果。 |

以上不是完整公開貼文清單。赴美背景、任職先後、裸辭期間經歷及實際工程部署效果尚未確認。未核讀的其他故事線索不列入公開案例。
