# 動畫特效類+transition

## 過渡 transition

屬性值:過渡的屬性 花費時間(s) 

- 過渡的屬性可以是具體的css屬性
- 也可以為all(兩個元素狀態屬性值不同的，都產生過渡效果)
- transition設置給元素本身(轉換前)

```css
.box1 {
        width: 200px;
        height: 200px;
        background-color: pink;
        transition: transform .3s;
        }
.box1:hover {
            transform: translateY(50px);
            }
```

### transition是複合屬性，包含了

**transition-property :指定過渡的屬性 可以是all或是任意屬性**

**transition-duration:過渡的持續時間 可以是s/ms**

**transition-timing-function:過渡方式 linear/ease-in/ease-out/ease-in-out**

**transition-delay:延遲啟動 可以設定時間 預設是0s**
 ****

![image.png](%E5%8B%95%E7%95%AB%E7%89%B9%E6%95%88%E9%A1%9E+transition/image.png)

[https://cubic-bezier.com/](https://cubic-bezier.com/) 配合貝賽爾曲線使用的網站

## 光標類型 cursor

屬性值:

default 默認(箭頭)

pointer: 小手(提示可以點擊)

text:工字型(提示可以打字)

move:十字光標(提示可以移動)

平滑滾動

**scroll-behavior : smooth** 

## 陰影 box-shadow

屬性值:

X 軸偏移量、Y 軸偏移量、模糊半徑、擴散半徑(不常用可略過)和顏色

```css
box-shadow: 12px 12px 2px 1px rgba(0, 0, 255, 0.2);
```