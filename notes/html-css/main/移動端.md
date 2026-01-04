# 移動端

![image.png](%E7%A7%BB%E5%8B%95%E7%AB%AF/image.png)

移動端用的通常是縮放過後的像素 跟web端的1:1像素有所區別 

正常情況下 手機的web像素實際會是css設定的2~3倍

# Vw/Vh單位適配:

vw(Viewport Width)是一種基於視窗寬度的相對單位,用於移動端適配

vw單位定義:

1vw = 視窗寬度的1%

如果視窗寬度是375px,則 1vw=3.75px

100vw = 視窗完整寬度

vh: 視窗高度的1%

vw的%的區別, %是相對於父容器 父容器沒有寬高數值的話不會生效

 網頁主要是對屏幕寬度去做適配，所以通常用vw就可以，vh少用

![image.png](%E7%A7%BB%E5%8B%95%E7%AB%AF/image%201.png)

## vw適配方法

方式1:使用 calc()函數

```css
.nav {
	width:calc(106/375 * 100px)
	height: calc(106/375 * 100px)
}
/*書寫繁瑣*/
```

方式2:使用css預處理器

使用less或是sass

方式3:使用插件轉換 px to rem

# vmin與vmax:

當設備旋轉時，視窗的寬高會發生變化，vmin會始終取當前寬高的最小值，而vmax取最大值，讓元件根據畫面旋轉自動轉換寬高值

 

# vmin/vw區別:

![image.png](%E7%A7%BB%E5%8B%95%E7%AB%AF/image%202.png)

# Rem方案:

取決於根元素(html)的font-size，使夜面基於rem的布局適應不同螢幕尺寸，當html的font-size增加減少時，頁面的元素大小也跟著縮放

font-size動態增減方法:

1.媒體查詢

```css
html {
	font-size: 20px;
	font-size: 5.33333vw
	}
@media screen and (max-width: 320px){
	html{
		font-size:17.06667px
	}
	
@media screen and (min-width: 540px){
	html{
		font-size:28.8px
	}
}
```

2.js方式引入

![image.png](%E7%A7%BB%E5%8B%95%E7%AB%AF/image%203.png)

### Rem單位適配

rem值=設計稿元素尺寸/html的font-size(基準值)

適配方法1

1.使用postCSS插件

2less/sass直接寫px

3.使用post-css-pxtorem插件 打包發布的時候自動轉換為rem

是配方法2

1.使用flexble.js讓html的rem根據網頁寬度/10動態更改html的font-size大小

2.使用px to rem& rpx & vw轉換px成rem

## 特殊程式碼

-webkit-tap-hightlight-color: rgba(0, 0, 0, 0) 移除手機端點擊反白高亮