# BMI 計算機自然語言 E2E 測試

這是一個針對 BMI 計算機 Web 應用程式的端對端 (E2E) 測試專案，使用自然語言描述的測試案例來進行自動化測試。

## 測試目標應用

- **應用程式**: BMI 計算機
- **部署位置**: https://bmi-calculator-mu-ten.vercel.app/
- **功能**: 計算身體質量指數 (BMI) 並提供健康狀態分類

## 測試案例

測試案例詳細記錄在 [`TestCases.md`](TestCases.md) 中，包含以下三個主要測試場景：

1. **不會計算 BMI** - 驗證在沒有輸入數值的情況下，點擊計算按鈕不會顯示任何結果
2. **BMI 數值正確** - 驗證 BMI 計算公式的正確性（身高 170cm、體重 70kg 應得到 24.2）
3. **BMI 狀態正確** - 驗證根據 BMI 數值正確顯示健康狀態分類（身高 170cm、體重 80kg 應顯示「肥胖」）

測試結果記錄在 [`TestResults.md`](TestResults.md) 中。

## 技術架構

### 工具與技術

- **瀏覽器**: Google Chrome
- **測試控制**: Chrome DevTools MCP (Model Context Protocol)
- **AI 助手**: GitHub Copilot Agent Mode / Gemini CLI
- **測試描述**: 自然語言測試案例

### 設定檔案

- **`.vscode/mcp.json`**: MCP 伺服器設定，使用 `chrome-devtools-mcp` 來控制 Chrome 瀏覽器進行自動化測試
- **`prompt.md`**: 測試執行指令提示（支援 GitHub Copilot 和 Gemini CLI）
- **`TestCases.md`**: 詳細測試案例步驟
- **`TestResults.md`**: 測試結果記錄檔案

## 快速開始

### 先決條件

- 安裝 Google Chrome 瀏覽器
- 安裝 Visual Studio Code
- 確保已安裝 Node.js 和 npm（用於運行 `chrome-devtools-mcp`）

### 執行測試

1. **克隆專案**

   ```bash
   git clone https://github.com/cdcd72/bmi-calculator-natural-language-e2e.git
   cd bmi-calculator-natural-language-e2e
   ```

2. **開啟 VS Code**

   ```bash
   code .
   ```

3. **執行測試**

   使用 AI 助手（GitHub Copilot Agent Mode 或 Gemini CLI），參考 `prompt.md` 中的提示詞：

   > 使用 Chrome，依照 #file:TestCases.md 進行測試，並且把結果更新在 #file:TestResults.md 中，填寫結果欄位就好

4. **查看結果**

   測試完成後，檢查 `TestResults.md` 中的測試結果

## 專案結構

```
bmi-calculator-natural-language-e2e/
├── .vscode/
│   └── mcp.json              # MCP 伺服器設定
├── LICENSE                   # MIT 授權條款
├── README.md                 # 專案說明文件
├── prompt.md                 # 測試執行提示詞
├── TestCases.md              # 測試案例步驟
└── TestResults.md            # 測試結果記錄
```

## 測試案例詳情

### 測試 1: 不會計算 BMI

- **目的**: 確保在沒有輸入身高體重的情況下，系統不會進行計算
- **步驟**:
  1. 開啟 https://bmi-calculator-mu-ten.vercel.app/
  2. 點擊計算鈕
  3. 確認不會顯示任何結果
- **期望結果**: 點擊計算按鈕後不顯示任何計算結果

### 測試 2: BMI 數值正確

- **輸入**: 身高 170cm, 體重 70kg
- **步驟**:
  1. 開啟 https://bmi-calculator-mu-ten.vercel.app/
  2. 輸入身高 170cm
  3. 輸入體重 70kg
  4. 點擊計算鈕
  5. 確認結果是否為 24.2
- **期望結果**: BMI = 24.2
- **計算公式**: BMI = 體重(kg) ÷ 身高 ²(m²) = 70 ÷ (1.7)² ≈ 24.2

### 測試 3: BMI 狀態正確

- **輸入**: 身高 170cm, 體重 80kg
- **步驟**:
  1. 開啟 https://bmi-calculator-mu-ten.vercel.app/
  2. 輸入身高 170cm
  3. 輸入體重 80kg
  4. 點擊計算鈕
  5. 確認結果是否為 肥胖
- **期望結果**: 顯示 "肥胖" 狀態
- **BMI 分類標準**:
  - 過輕: BMI < 18.5
  - 正常: 18.5 ≤ BMI < 24
  - 過重: 24 ≤ BMI < 27
  - 肥胖: BMI ≥ 27

## 運作原理

這個專案使用 **Model Context Protocol (MCP)** 來實現自然語言驅動的端對端測試：

1. **MCP 設定**: `.vscode/mcp.json` 配置了 `chrome-devtools-mcp` 伺服器
2. **AI 助手**: 使用 GitHub Copilot 或 Gemini CLI 解析自然語言測試案例
3. **自動化執行**: MCP 將測試指令轉換為實際的瀏覽器操作
4. **結果記錄**: 測試結果自動寫入 `TestResults.md`

> **注意**: 這是一個創新的測試方法示範，展示如何使用 AI 和 MCP 來執行由自然語言描述的測試案例，無需編寫傳統的測試腳本。
