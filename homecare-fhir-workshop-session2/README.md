# 居家照護 FHIR 工作坊｜第二堂程式包

本資料夾供教學示範使用，包含 Q3、Q4、Q5 三個獨立 HTML 網頁，以及 CSV 範例。

## 建議操作順序

1. 用瀏覽器開啟 `session-2/01_upload_documentreference.html`。
2. 選擇 `pain_detail.csv` 或 `oral_ulcer_detail.csv`，確認 micro-IG 種類與版本。
3. 按「產生 DocumentReference JSON」，再按「PUT 上傳」。複製頁面顯示的 DocumentReference URL。
4. 開啟 `session-2/02_observation_entry.html`，貼上剛才的 DocumentReference URL，按「讀取規格」。
5. 勾選要記錄的細項，按「產生 Observation JSON」，再按「POST 上傳」。記下成功產生的 Observation URL。
6. 開啟 `session-2/03_observation_query.html`，確認 Patient ID 與 Q4 一致，貼上同一份 DocumentReference URL，按「讀取規格並產生查詢 URL」，再按「調閱 Observation」。

## 欄位設計重點

- CSV 的 `problemCode` 是問題代碼，例如 `pain`、`oral-ulcer`。
- Q3 的 `kind` 是 Micro-IG 規格種類識別值，存於 `DocumentReference.identifier`；它不等於 `problemCode`，不要混用。
- Q4 的 `Observation.code.coding.code` 使用 CSV 的 `problemCode`。
- Q4 的 `Observation.component.code.coding.code` 使用 CSV 的 `detailCode`。
- Q5 從 DocumentReference 附件內的 CSV 讀取 `problemCode`，再依 Patient ID 與問題代碼查詢 Observation。

## 重要提醒

- 這是教學原型，僅使用虛構資料。不要輸入真實病人個資或醫療紀錄。
- `https://hapi.fhir.org/baseR4` 是公開測試伺服器，資料可能被清除，也可能被他人看到；請勿存放正式資料。
- `https://example.org/fhir/CodeSystem/...` 是示範用識別系統 URI，不是正式部署的 CodeSystem。正式使用前應由醫療資訊與 FHIR 專業人員確認。
- 這些網頁需要瀏覽器能連線至 HAPI 測試伺服器；若出現 `Failed to fetch`，可能是網路、CORS 或伺服器狀況。可嘗試用本機 HTTP 伺服器開啟，而非直接雙擊 HTML。
- Q3、Q4 的欄位設計以本工作坊 CSV 規格為基礎；這是教學示範，不等同完整的正式 FHIR Implementation Guide。
