# Grid布局

display:grid   塊級（常用

display:inline-grid 行內

Grid定義之後 由於沒有定義列的數量 故布局還是保持不變

# grid track

決定了網格布局的結構

## grid-template-columns/rows：定義列/行

值 ：本身是複合屬性 有幾個屬性=有幾個列/行

數值為px 代表每列/行 有多少像素的長度

ex:

grid-template-colums:200px 200px 200px

/有三列 每列的長度為200像素/

![1000013536.png](Grid%E5%B8%83%E5%B1%80/1000013536.png)

### 響應式布局設定:

頁面隨視窗縮放改變行列數量

### repeat(次數 , 軌道尺寸) or repeat(自動填充,軌道尺寸)

值：

auto-fill:竟可能多的創建列

auto-fit ：盡可能拉伸容器

ex:grid-template-columns:repeat(3 , 1fr) 

grid-template-columns:repeat(auto-fill , 1fr) 

![image.png](Grid%E5%B8%83%E5%B1%80/image.png)

### minmax(最小值,最大值)

限制縮小頁面後的容器最小列寬

ex: grid-template-columns:minmax(100px , 1fr)

## 與flex共通/類似的屬性

colunm-gap

row-gap

justfy-content

align-content

## grid line

實現單一元素跨過多個網格 以網格的列行（線）為依據

grid-column: 1/3  表示從第一列三列

grid-row :1/3 表示從第一行到第三行

grid-column: 1/span 2  表示從第一線跨兩個單元格

grid-row :1/span 2 表示從第一線跨兩個單元格

## grid-auto-flow

row:(預設)子元素按先行後列順序填充

colum;子元素按先列後行排序

## 項目對齊方式

項目在大型容器當中調整項目要對齊容器的哪個方向

justfy-items 水平對齊方式

align-items 垂直對齊方式

值：

start :

水平方向效果：左對齊

垂直方向效果：頂部對齊

end:

水平方向效果：右對齊

垂直方向效果：底部對齊

center:

水平居中對齊

## 多列布局

不先分配容器每行每列寬高多少 而是指定有幾行幾列 放入內容讓容器自動適應

![image.png](Grid%E5%B8%83%E5%B1%80/image%201.png)

![image.png](Grid%E5%B8%83%E5%B1%80/image%202.png)