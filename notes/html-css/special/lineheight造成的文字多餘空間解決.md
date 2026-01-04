# lineheight造成的文字多餘空間解決

你觀察到的現象是正確的：因為 line-height 所產生的空間（Leading）是均分在文字的上方與下方的。但問題在於，字體本身的構造並非對稱的（大寫字母、小寫字母的 ascender 和 descender 高度不同），這會導致即使 CSS 邏輯上置中了，視覺上看起來還是會偏移幾個像素。
這確實是「二擇一」的困境，但我們可以透過以下三個層次來「破解」這個問題：

1. 為什麼 Flex + line-height 無法完美置中？
當你設定 line-height: 1.2 時，瀏覽器會計算：(1.2 - 1.0) \div 2 = 0.1。
它會在文字上方加 0.1em 的空間，下方也加 0.1em。
然而，多數動態字體的基線 (Baseline) 並不在幾何中心。例如，大寫字母通常偏上，導致視覺重心看起來比實際的幾何中心高。
2. 解決方案 A：調整垂直對齊的「微調補償法」
在響應式設計中，我們通常會接受 1.2 的行高，但為了視覺置中，我們會手動進行「體感補償」。
- 使用 relative 定位微調：
這不會破壞 Flexbox 佈局，但能解決那 1-2 像素的視覺偏差。
.text-element {
position: relative;
top: -1px; /* 根據字體特性向上微調 */
}
- 調整 Padding 不對稱：
手動讓 padding-bottom 比 padding-top 多 1px，來抵銷字體重心偏高的問題。
1. 解決方案 B：Cap Size 對齊（最先進的做法）
如果你追求的是 Pixel Perfect 且不希望隨便用負邊距微調，現在的趨勢是使用 Cap Height 的概念。這意味著我們只針對「大寫字母的高度」進行置中，忽略掉行高產生的多餘空間。
在現代 CSS 中，你可以利用 calc 或是新的 text-box-trim（如前所述）來實現：
.button {
display: flex;
align-items: center;
line-height: 1.2;
/* 現代瀏覽器屬性：修剪掉行高多出的空白 */
text-box-trim: both;
text-box-edge: cap alphabetic;
}
2. 解決方案 C：針對單行元件（如按鈕）的特例處理
如果是一個單行的元件（按鈕、標籤），而你非常在意對齊：
- 放棄 line-height 的限制：將 line-height 設為 1 或 normal。
- 靠垂直 Padding 撐開高度：這能讓你更精準地控制上下間距。
- 加上 min-height：確保在不同語系下（如泰文、韓文有較大的上下延伸）容器高度穩定。
總結：如何選擇？
這不是「二擇一」，而是根據元件性質做優先權排序：
- 如果是內文/段落：優先選 line-height: 1.5。視覺上稍微不置中沒關係，因為閱讀舒適度（多行不重疊）才是重點。
- 如果是 UI 元件（按鈕、標題）：優先選 Flex 置中 + 微調。你可以稍微降低 line-height（例如 1.1），然後用 padding 或 top: -1px 來達成視覺上的完美。
通常在設計系統（Design System）中，我們會針對特定的字體定義一個 vertical-offset 變數，專門用來修正這種視覺偏差。你想知道如何在 CSS 變數中統一管理這種「微調值」嗎？