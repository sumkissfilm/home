# CSS 檔案合併說明

## 📋 合併概述

**合併檔案**: `css/social-icons.css` → `css/header-navigation.css`

**合併原因**: 
- 兩個檔案控制相同的元素 (`.social-icons`)
- 存在大量重複的 CSS 樣式
- 功能相關性高，都屬於導航列相關樣式

---

## 🔄 合併過程

### 1. **分析重複樣式**
發現以下重複的選擇器：
- `.social-icons a i, .social-icons a .fab, .social-icons a .fas, .social-icons a .far`
- `.social-icons a .fab`
- `.social-icons a:focus`

### 2. **整合樣式到 header-navigation.css**
將 `social-icons.css` 中的通用樣式整合到 `header-navigation.css` 中：
- Font Awesome 圖示顯示設定
- 品牌圖示特定字重設定
- 無障礙功能樣式

### 3. **移除重複樣式**
刪除 `header-navigation.css` 中重複的樣式定義，保留整合後的版本。

### 4. **更新 HTML 檔案**
- 從 `index.html` 移除 `social-icons.css` 的引入
- 從 `header-component.html` 移除 `social-icons.css` 的引入

### 5. **刪除舊檔案**
刪除不再需要的 `css/social-icons.css` 檔案

---

## 📁 合併後的檔案結構

```
SK_page/
├── css/
│   ├── header-navigation.css    # 包含所有導航和社交圖示樣式
│   ├── style.css               # 主要樣式
│   ├── footer.css              # 頁尾樣式
│   └── (social-icons.css 已刪除)
├── index.html                  # 已更新 CSS 引入
└── header-component.html       # 已更新 CSS 引入
```

---

## ✅ 合併效益

### 1. **效能提升**
- 減少一個 HTTP 請求
- 降低檔案載入時間

### 2. **維護便利性**
- 只需維護一個檔案
- 避免樣式衝突和重複

### 3. **程式碼組織**
- 相關功能集中在同一檔案
- 提高程式碼可讀性

---

## 🔍 合併後的樣式結構

### header-navigation.css 中的社交圖示樣式：

```css
/* ===== SOCIAL ICONS ===== */
/* 社群媒體圖示容器樣式 */
.social-icons { ... }

/* 選單展開時的社群圖示樣式 */
.navbar-collapse.show .social-icons { ... }

/* 社群圖示連結樣式 */
.social-icons a { ... }

/* 社群圖示懸停效果 */
.social-icons a:hover { ... }

/* ========================================
   SOCIAL MEDIA ICONS - GENERAL STYLES
   ======================================== */

/* ===== FONT AWESOME ICON DISPLAY ===== */
/* Font Awesome 圖示顯示設定 - 通用樣式 */
.social-icons a i,
.social-icons a .fab,
.social-icons a .fas,
.social-icons a .far { ... }

/* 品牌圖示特定字重設定 */
.social-icons a .fab { ... }

/* ===== ACCESSIBILITY ===== */
/* 無障礙功能 - 焦點樣式 */
.social-icons a:focus { ... }

/* 響應式設計中的社交圖示樣式 */
@media (min-width: 992px) {
    .social-icons { ... }
    .social-icons a { ... }
    .social-icons a:hover { ... }
}

@media (max-width: 576px) {
    .social-icons { ... }
    .social-icons a { ... }
}
```

---

## ⚠️ 注意事項

### 1. **樣式優先級**
- 合併後所有樣式都在同一檔案中
- 使用 `!important` 確保圖示樣式優先級

### 2. **維護建議**
- 未來修改社交圖示樣式時，直接在 `header-navigation.css` 中修改
- 保持樣式的組織結構和註解

### 3. **測試確認**
- 確認桌面版和行動版的社交圖示顯示正常
- 確認無障礙功能（焦點樣式）正常運作
- 確認 Font Awesome 圖示正確顯示

---

## 📝 更新記錄

- **日期**: 2024年
- **操作**: 合併 `social-icons.css` 到 `header-navigation.css`
- **影響檔案**: 
  - `css/header-navigation.css` (新增樣式)
  - `index.html` (移除 CSS 引入)
  - `header-component.html` (移除 CSS 引入)
  - `css/social-icons.css` (已刪除) 