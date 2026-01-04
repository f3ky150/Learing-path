# 動畫animation

優點:

- 性能高效:支持gpu加速渲染，避免javascipt計算開銷
- 代碼簡潔:解決css過度(transtion)只能定義兩偵狀態的侷限性
- 交互性強:支持用戶操作(懸停,點擊)結合，提升網頁表現力與用戶體驗

### 動畫使用:先定義動畫，然後才使用動畫

### 1.定義動畫:製作一個動畫模式並定義名稱

```css
@keyframes move/*動畫名稱定義*/
{
	0%
	{
		transform: translaxeX(0px);
	}
	20%
	{
		transform: translateX(50px);
	}
	100%
	{
		transform: trnaslateX(100px);
	}
}
/* 如果動畫只有2個狀態 頭跟尾 0%/100% 可以改成使用from/to */
```

### 2.使用動畫:找到要使用的元素使用定義好的動畫

```css
   .box
    {
        width: 100px;
        height: 100px;
        background-color: pink;
        animation: move 1s; /*使用上面定義的move動畫*/
    }
```

### 3.目標元素的animation動畫屬性完整寫法(複合屬性)

animation:動畫名稱 動畫時長 速度曲線 延遲時間 播放次數 播放方向 執行完畢狀態

![image.png](%E5%8B%95%E7%95%ABanimation/image.png)

前兩個必寫，其餘可以省略，但要保證順序

動畫屬性要寫到目標元素上

```css
animation: move 1s 
```

### 4.關於執行完畢狀態:forwards,backwards

## 1. `forwards`（向前保留）

**作用：動畫結束後，元素將停留在最後一個關鍵影格（100%）的樣式。**

通常動畫結束後會立即跳回原本的初始樣式，這在視覺上會顯得很突兀。加上 `forwards` 可以讓元素保持在動畫結束時的樣子。

- **範例**：一個淡入動畫（從透明到不透明），如果不加 `forwards`，透明度會瞬間變回 0；加了之後，元素就會維持在透明度 1。

---

## 2. `backwards`（向後延伸）

**作用：在動畫「延遲期間（delay）」，元素會提前套用第一個關鍵影格（0%）的樣式。**

這個設定只有在你有設定 `animation-delay`（延遲）時才看得出效果。

- **沒設定時**：在延遲的 2 秒內，元素會顯示其**初始狀態**，直到動畫開始那一刻才突然跳到 `0%`。
- **設定 `backwards` 後**：在延遲的 2 秒內，元素會提前「預演」並停在 `0%` 的狀態，讓動畫銜接更流暢。

## Step逐幀動畫

[steps逐帧動畫](%E5%8B%95%E7%95%ABanimation/steps%E9%80%90%E5%B8%A7%E5%8B%95%E7%95%AB%202cb52da3bb9c8061a362f5f412a6bcac.md)