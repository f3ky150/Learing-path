# has選擇器

在 `:has()` 出現之前，CSS 只能影響**後代**或**後方的兄弟節點**；但有了 `:has()` 之後，你可以透過「先抓到共同的父級，再往下找」的方式，實現「跨組件」的聯動。

我們通常稱這種技巧為 **「狀態管理（State Management）」**。

---

### 1. 核心邏輯：藉助「共同祖先」

如果你想在懸停 `<li>` 時，改變頁面另一處的 `<div>`，邏輯如下：

1. 找到這兩個元素的**共同父層**。
2. 在父層使用 `:has()` 來檢查 `<li>` 是否被懸停。
3. 如果條件成立，選中目標 `<div>`。

### 2. 實戰範例：側邊欄連動顯示

假設你有一個清單，滑鼠指到不同項目時，右邊的描述框會跟著變色：

**HTML 結構：**

HTML

```html
<div class="container">
  <ul>
    <li class="item-1">產品 A</li>
    <li class="item-2">產品 B</li>
  </ul>

  <div class="display-box">對應的產品說明</div>
</div>
```

**CSS 實現方式：**

CSS

```css
/* 當 .container 裡面「含有」正在被 hover 的 .item-1 時 */
/* 改變 .display-box 的樣式 */
.container:has(.item-1:hover) .display-box {
  background-color: lightblue;
  content: "正在看產品 A";
}

/* 當 .item-2 被 hover 時 */
.container:has(.item-2:hover) .display-box {
  background-color: lightcoral;
}
```

---

### 3. 與傳統方式的差異

在沒有 `:has()` 的年代，你只能用 **相鄰兄弟選擇器 (`+`)** 或 **通用兄弟選擇器 (`~`)**，但這有非常嚴格的限制：

- **舊方法（兄弟選擇器）：** `li:hover ~ .display-box`
    - **限制：** `.display-box` 必須在 `<li>` 的**後面**，且必須是同級（兄弟）。你不能往回找，也不能找「遠房親戚」。
- **新方法（`:has()`）：**
    - **優勢：** 無論 `.display-box` 在哪裡（前面、後面、嵌套在別的層級裡），只要它們有一個共同的祖先，就能連動。

### 總結

你可以把 `:has()` 想像成一個**「感應器」**：

- 它裝在父層身上。
- 它感應子層的狀態（如 `:hover`, `:focus`, `:checked`）。
- 一旦感應到，它可以控制該父層下方的**任何**元素。

**你想嘗試做一個「導覽列滑過時，下方背景大圖跟著切換」的效果嗎？我可以幫你寫一個簡潔的示範代碼。**