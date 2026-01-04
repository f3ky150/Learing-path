# 變換transform

![image.png](%E8%AE%8A%E6%8F%9Btransform/image.png)

- 通過hover製作交互動畫，使用transform比定位position來的節省資源
- 如果使用的是百分比，數值是相對於元素自身尺寸，而不是父容器

ex.transform: translateX(50%) ; 這個是根據自身X軸一半的尺寸移動

### *Transition寫在要過渡的屬性前 滑鼠移開後會倒放過渡回去

                        寫在hover上則是會直接回復成原本的樣式

## *旋轉無法給行內元素使用

## *放大效果和直接修改寬高實現放大最大區別在於transform放大不會影響原本的文件流(不會推開附近的元素)

## Tranform-複合寫法

語法:

### transform: a() b() c()

執行順序為 c>b>a

```css
transform: rotate(360deg) translate(600px) scale(1.5)
/執行順序為scale>translate>rotate/
```

## 3d選轉

![image.png](%E8%AE%8A%E6%8F%9Btransform/image%201.png)

### 需要配合透視屬性perspective使用

```css
transform:perspective(1000px) rotateY(360deg) /*透視效果(子級)*/
```

數值越小 透視效果越強

父元素添加 ，所有子元素都會添加效果

子元素添加，當前元素添加效果

perspective()必須作為transform屬性的第一個函數(否則無效)

## 3d位移

![image.png](%E8%AE%8A%E6%8F%9Btransform/image%202.png)

![image.png](%E8%AE%8A%E6%8F%9Btransform/image%203.png)

![image.png](%E8%AE%8A%E6%8F%9Btransform/image%204.png)