# CSS3-動畫時間線animation-timeline

### 動畫時間線是讓開發者能將動畫進度與特定事件(如滾動，視窗可見性)綁定，從而實現更複雜的交互效果.0

## 滾動時間線:scroll

聲明timeline後 動畫不再自動執行，而是跟滾輪綁定執行

```css
.scrollbar {
	width:0%;
	height: 3px;
	background:linear-gradient(90deg,
	animation: move 2s;
	/*綁定時間線*/
	animation-timeline: scroll();
	}
	
	@keyframe move {
		0% {
			width: 0;
		}
		100% {
			width: 100%
		}
	}
```

## 視窗時間線:view

動畫進度與元素進入/離開視窗的可見性有關聯

```css
.scrollbar {
	opacity: 0.2;
	animation: scale 1s linear forwards;
	/*綁定時間線*/
	animation-timeline: view();
	}
	
	@keyframe scale {
		0% {
			transform: scale(1);
			opacity: 0.2;
		}
		100% {
			transform: scale(1.5);
			opacity: 1;
		}
	}
```