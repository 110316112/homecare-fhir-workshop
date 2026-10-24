教學範例（第二堂）

檔案
- 01_upload_documentreference.html：Q3，上傳 detail 規格檔為 DocumentReference（資源種類 radio、micro-ig 種類與版本寫入 masterIdentifier 與 identifier、格式下拉、說明欄位、PUT、調閱網址）
- 02_observation_entry.html：Q4，讀取 DocumentReference 內的 CSV，勾選項目、radio 單選值，產生並 POST Observation
- pain_detail.csv：疼痛範例（取自老師的 patientProblem 儲存庫）
- oral_ulcer_detail.csv：口腔潰瘍範例
- 學員提示詞.md：Q1、Free-style、完整規格版提示詞與驗收清單

使用順序
1. 用 01 選 CSV，按鈕 1 產生 JSON，按鈕 2 上傳，複製調閱網址
2. 開啟 02，貼上該網址，按「讀取規格」
3. 勾選與選擇，按鈕 1 產生 JSON，按鈕 2 上傳，複製 Observation 網址

注意
- 教學原型，只用虛構資料。HAPI 是公開測試伺服器，資料可能被清除。
- 這兩個程式依老師 Q3 的需求與 DR-JSON-Template 撰寫，尚未在你的網路環境做完整上傳測試。請先自己跑一次。
- 02 的編碼系統網址是範例，正式使用需由醫護與 FHIR 專業人員確認。
- 若 Failed to fetch，請檢查網路、網址與 CORS；可嘗試用本機 HTTP 伺服器開啟。
