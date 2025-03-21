# Azure 電腦視覺 OCR 文字辨識專案

這個專案示範如何使用 Azure 認知服務中的電腦視覺 API 來執行光學字元辨識 (OCR) 和文字讀取功能。

## 專案設定

### 必要條件
- .NET 8.0 SDK
- Azure 訂閱
- Azure 認知服務資源

### 設定步驟
1. 在 Azure 入口網站建立認知服務資源
2. 複製端點 URL 和金鑰
3. 更新 `appsettings.json` 檔案中的設定：
   - CognitiveServicesEndpoint
   - CognitiveServiceKey

## 主要功能

本專案提供三種文字辨識模式：

### 1. OCR API (選項 1)
- 使用 `GetTextOcr()` 方法
- 適用於印刷文字的快速辨識
- 會在辨識的文字周圍繪製矩形框
- 輸出結果儲存為 `ocr_results.jpg`

### 2. Read API (選項 2)
- 使用 `GetTextRead()` 方法
- 支援更複雜的文字版面配置
- 可處理 PDF 文件
- 範例使用 `Rome.pdf` 檔案

### 3. 手寫文字辨識 (選項 3)
- 同樣使用 `GetTextRead()` 方法
- 特別優化於手寫文字辨識
- 範例使用 `Note.jpg` 檔案

## 程式碼結構說明

### 主要元件
- **ComputerVisionClient**: Azure 視覺服務的主要客戶端
- **認證處理**: 使用 ApiKeyServiceClientCredentials 進行驗證
- **非同步操作**: 使用 async/await 模式處理 API 請求

### 核心方法
1. `GetTextOcr()`
   - 使用傳統 OCR API
   - 支援即時文字位置標記
   - 輸出視覺化結果

2. `GetTextRead()`
   - 使用新版 Read API
   - 支援非同步操作流程
   - 適用於複雜文件處理

## 使用方式

1. 執行程式後，選擇功能選項（1-3）
2. 程式會處理對應的範例圖片：
   - 選項 1: Lincoln.jpg
   - 選項 2: Rome.pdf
   - 選項 3: Note.jpg

## 注意事項

- 確保所有圖片檔案都放在 `images` 資料夾中
- API 呼叫可能需要幾秒鐘才能完成
- 請確保有足夠的 Azure 服務配額
