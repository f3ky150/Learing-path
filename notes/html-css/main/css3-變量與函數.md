# css3-變量與函數

## 作用域:變量的作用範圍，哪個區域有效

### 定義變量:

```css
:root { /*全局變量*/
	--color: #000
}
.box{ /*局部變量*/
	--color: pink
}
```

全局變量:通過 :root 定義，作用於整個網頁

局部變量:在特定選擇器中定義，影響該元素與其使用變量:

### 使用變量:

```css
.nav {
	color: var(--color);
	backgroundcolor: var(--bgcolor)
}
```

通過 var(- -變量名)使用變量