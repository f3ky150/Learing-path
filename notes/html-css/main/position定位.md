# position定位

## 相對定位

Position : relative;

top :_px/0 :距離頂端多少距離 0=置頂

bottom :_px

left :_px

right :_px

## 相對定位 (`position: relative;`) 的真正作用

很多人會誤解相對定位，因為單獨使用它時，看起來只是用 `top/right/bottom/left` 輕微移動了元素，而這種移動效果確實可以透過 `margin` 來實現。

但這兩者的**本質和副作用**是完全不同的。 

### 相對定位的兩個主要作用：

### 1. 建立「定位上下文」(Positioning Context) (最重要)

這是相對定位最主要的任務，也是我們前面討論的核心：它提供了一個**錨點**，讓絕對定位的子元素有參考對象。

- **行為：** 子元素 B 設為 `absolute` 時，它會參考設有 A `relative` 的父元素 A。

### 2. 進行「有空間佔位」的位移

`position: relative;` 允許您使用 `top`, `left` 等屬性來移動元素，但與 `margin` 相比，它們有兩點**根本區別**：

| 屬性 | 位移是否影響周圍元素？ | 位移是否仍在原處佔位？ | 改變空間屬性？ |
| --- | --- | --- | --- |
| **`position: relative;`** | **否** (位移後的元素會**遮蓋**其他內容) | **是** (原有的空間**仍被佔用**，不會塌陷) | 僅移動視覺位置 |
| **`margin`** | **是** (它會**推開**周圍元素) | **否** (它在原處**增加空間**，元素本身位置沒變) | 改變周圍的間距 |

---

## 為什麼不能用 `margin` 替代相對定位？

儘管您可以用 `margin` 來移動元素，但 `margin` **無法**實現相對定位最重要的功能：**為絕對定位的子元素提供參考點**。

### 比較範例：

假設您要製作一個帶有右上角角標的卡片：

| 元素 | 父級 A (`Card`) | 子級 B (`Badge`) | 備註 |
| --- | --- | --- | --- |
| **使用 `position` (正確做法)** | `position: relative;` | `position: absolute;` + `top: 0; right: 0;` | 徽章 B 緊貼卡片 A 的右上角，**脫離文檔流**，不佔用空間。 |
| **僅使用 `margin` (錯誤做法)** | 無 (`static`) | `position: absolute;` | 徽章 B 會參考 <html> 頁面，跑到瀏覽器視窗的右上角。 |

匯出到試算表

**總結來說：**

- `margin` 是一種**推擠 (Pushing)** 行為，用來在元素之間創造間隔。
- `position: relative;` 的核心價值是**錨定 (Anchoring)**，它給予絕對定位元素一個安全的**參照容器**。

所以，在**父子絕對定位**的結構中，`position: relative;` 的作用是**不可替代**的。

# 絕對定位

Position : absolute;

使用場景 : 子級絕對定位 父級相對定位

---

## 絕對定位 (`position: absolute;`) 的核心用意

**絕對定位**的核心用意就是為了讓元素**跳脫 (脫離) 原有的文檔流（Normal Flow）**，讓它可以像一個**獨立的圖層 (Layer)** 一樣進行堆疊或精確放置。

### 絕對定位的關鍵特性：

1. **脫離文檔流 (Out of Flow):** 一旦元素設定為 `position: absolute;`，它就不再佔用空間。後續的元素會像它不存在一樣向上移動，這就是它能實現圖層堆疊的基礎。
2. **圖層堆疊 (Layering):** 它允許您使用 `z-index` 屬性來控制元素在 Z 軸上的堆疊順序，非常適合用於：
    - **浮層/氣泡 (Tooltip)**
    - **角標/徽章 (Badge)**
    - **模態視窗 (Modal)**
    - **複雜的遮罩 (Overlay)**

# 定位居中

1.絕對定位

2.水平,垂直邊篇疑為50%

3.子級向左,上移動自身尺寸的一半

```css
.center-box {
	position: absolute;
	top: 50%;
	left: 50%;
	transform: translate(-50%, -50%);
}
```

- `position: absolute;` + 無錨點 → **內容居中**，會隨滾動**移動**。
- `position: fixed;` + 居中程式碼 → **視窗居中**，會隨滾動**固定**。(顯示模式特點為inline-block)

# 固定定位

Position : fixed;

元素脫離正常流 

以視窗為定位

通過top/bottom/left/right定位

優先級：若同時設定top/bottom left/right  top/left覆蓋bottom/right

# 黏性定位

Position : sticky;

結合相對定位與固定定位

元素滾到指定位置前 為相對定位 滾到指定位置後 變更為絕對定位

由於依賴於父級容器 父級的overflow:不可為hidden

**通過top/bottom/left/right定位**

**須有top/bottom/left/right 其中之一才可生效**

# 堆叠顺序

```css
  /* 取值是整数，默认是0，取值越大显示顺序越靠上 */
      z-index: 1;
```