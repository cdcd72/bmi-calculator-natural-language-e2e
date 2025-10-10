# BMI 計算機自然語言 E2E 測試

這是一個針對 BMI 計算機 Web 應用程式的端對端 (E2E) 測試專案，使用自然語言描述的測試案例來進行自動化測試。

## 測試目標應用

- **應用程式**: BMI 計算機
- **部署位置**: https://bmi-calculator-mu-ten.vercel.app/
- **功能**: 計算身體質量指數 (BMI) 並提供健康狀態分類

## 測試案例

測試案例詳細記錄在 [`TestCases.md`](TestCases.md) 中，包含以下三個主要測試場景：

1. **無效輸入測試** - 驗證在沒有輸入數值的情況下，點擊計算按鈕不會顯示任何結果
2. **BMI 數值計算正確性測試** - 驗證 BMI 計算公式的正確性 (體重 ÷ 身高 ²)
3. **BMI 狀態分類測試** - 驗證根據 BMI 數值正確顯示健康狀態分類

## 技術架構

### 工具與技術

- **瀏覽器**: Google Chrome
- **測試控制**: Chrome DevTools MCP (Model Context Protocol)
- **測試描述**: 自然語言測試案例

### 設定檔案

- **`.vscode/mcp.json`**: MCP 伺服器設定，用於控制 Chrome 瀏覽器進行自動化測試
- **`prompt.md`**: 測試執行指令提示
- **`TestCases.md`**: 詳細測試案例與結果記錄

## 快速開始

### 先決條件

- 安裝 Google Chrome 瀏覽器
- 確保 Chrome 安裝在標準路徑: `C:\Program Files\Google\Chrome\Application\chrome.exe`
- 安裝 Node.js 和 npm

### 執行測試

1. **克隆專案**

   ```bash
   git clone https://github.com/cdcd72/bmi-calculator-natural-language-e2e.git
   cd bmi-calculator-natural-language-e2e
   ```

2. **執行測試**
   根據 `prompt.md` 中的指示，使用 Chrome 依照 `TestCases.md` 進行測試

3. **記錄結果**
   測試完成後，將結果更新在 `TestCases.md` 中對應的結果欄位

## 專案結構

```
bmi-calculator-natural-language-e2e/
├── .vscode/
│   └── mcp.json              # MCP 伺服器設定
├── LICENSE                   # MIT 授權條款
├── README.md                 # 專案說明文件
├── prompt.md                 # 測試執行提示
└── TestCases.md             # 測試案例與結果記錄
```

## 測試案例詳情

### 測試 1: 無效輸入驗證

- **目的**: 確保在沒有輸入身高體重的情況下，系統不會進行計算
- **期望結果**: 點擊計算按鈕後不顯示任何計算結果

### 測試 2: BMI 數值計算驗證

- **輸入**: 身高 170cm, 體重 70kg
- **期望結果**: BMI = 24.2
- **計算公式**: BMI = 體重(kg) ÷ 身高 ²(m²)

### 測試 3: BMI 狀態分類驗證

- **輸入**: 身高 170cm, 體重 80kg
- **期望結果**: 顯示 "肥胖" 狀態
- **BMI 分類標準**:
  - 過輕: BMI < 18.5
  - 正常: 18.5 ≤ BMI < 24
  - 過重: 24 ≤ BMI < 27
  - 肥胖: BMI ≥ 27

> **注意**: 這是一個測試專案，主要用於演示如何使用自然語言描述進行 E2E 測試。實際的測試執行可能需要額外的自動化工具或框架。
