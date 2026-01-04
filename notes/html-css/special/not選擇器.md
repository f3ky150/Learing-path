# not選擇器

CSS 中的 `:not()` 偽類選擇器（Negation Pseudo-class）是一個非常強大且實用的工具。簡單來說，它被稱為**「否定選擇器」**，用來選取「不符合」括號內條件的所有元素。

這在你想要排除特定對象，而不是逐一列出符合對象時非常有用。

---

## 1. 基本語法

其語法結構如下：

CSS

`selector:not(exclusion) {
  /* 樣式規則 */
}`

- **selector**：你想套用樣式的基礎對象。
- **exclusion**：你想排除掉的元素、類別、ID 或其他選擇器。

---

## 2. 常見使用場景

### A. 排除特定 Class

假設你有一個列表，你想讓所有項目都有底線，但「最後一個」或「標記為無底線」的項目除外。

CSS

`/* 選取所有 li，但排除掉 class 為 "special" 的元素 */
li:not(.special) {
  color: blue;
}`

### B. 表單輸入框（排除特定類型）

你可能想設定所有文字輸入框的樣式，但不想影響到 `submit` 按鈕。

CSS

`/* 選取所有 input，但排除 type 為 submit 的 */
input:not([type="submit"]) {
  border: 1px solid #ccc;
  padding: 5px;
}`

### C. 列表間距（實用技巧）

這是我最常用的場景：給列表項加上間距，但最後一項不需要。

CSS

`/* 除了最後一項以外，所有 li 都加上下方間距 */
li:not(:last-child) {
  margin-bottom: 10px;
}`

---

## 3. 重要特性與限制

在使用 `:not()` 時，有幾個細節需要注意：

- **權重（Specificity）**：`:not()` 本身不增加權重，但**括號內的選擇器會增加權重**。
- **不可嵌套**：在舊規範中，你不能寫 `:not(:not(...))`，但在現代瀏覽器（CSS4 級別）中，這個限制已經放寬。
- **複數選擇器**：現在你可以一次排除多個條件，只要用逗號隔開即可：CSS
    
    `/* 排除類別為 .header 和 .footer 的所有 div */
    div:not(.header, .footer) {
      padding: 20px;
    }`
    
- **不能排除偽元素**：例如你不能寫 `:not(::before)`。