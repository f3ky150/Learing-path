# select選擇器

## 通配選擇器

一次選取所有樣式

```html
<style>
        *{
            color: red;
        }
</style>
```

## 類選擇器

class 不同元素可重複使用 作為組別同時賦予元素 class後可以給多個值 

呼叫時為 .+值

```html
<head>
	<style>
    .speak { /*類選擇器 class分類 .+類呼叫*/
        color: red;
    }
    .answer {
        color: blue;
    }
    .big {
            font-size: 70px;
        }
    
	</style>
</head>
	<body>
		<p class="speak big" >我對你說,萬水千山總是錯,愛我多點行不行</p> <!--一個class屬性可以寫很多值,但須空格分開-->
    <p class="answer">你回答我,一寸光陰一寸金，勸你死了這條心</p>
	</body>		
		
```

## id選擇器

id  不同元素有各自的id 作為個別賦予元素

呼叫時為 #+值     id不能為數字開頭

```html
<style>
        #earthy {
            color: red;
        }
        #turn-earthy {
            color: blue;
        }
        .u2 {
            font-size: 60px;
        }
    </style>
</head>
<body>
    <h1>還迎來到土味官網,土的味道我知道</h1>
    <h2 id="earthy" class="u2">土味情話</h2>
```

## 交集選擇器

a and b才可以 a且b 

```html
<head>
    <meta charset="UTF-8">
    <title>01_交集選擇器</title>
    <style>
        p.beauty{  /*如果有元素選擇器 需要放在第一個*/
            color: green;
        }
        .rich.beauty {
            color: blue;
        }
    </style>
</head>
<body>
    <h2 class="rich">土豪張三</h2>
    <h2 class="beauty">明星李四</h2>
    <h2 class="rich beauty">土豪明星王五</h2>
    <hr>
    <p class="beauty">小狗旺財</p>
    <p class="beauty">小豬佩奇</p>
</body>
```

## 並集選擇器

a or b 都可以 a或b

```html
 <style>
        .rich,
        .beauty,
        .dog,
        #sheep {
            color: gold;
            font-size: 40px;
            background-color: gray;
            width: 180px;
        }
</style>
</head>
<body>
    <h2 class="rich">土豪張三</h2>
    <h2 class="beauty">明星李四</h2>
    <h2>破產王五(不加任何樣式)</h2>
    <hr>
    <p class="dog">小狗旺財</p>
    <p class="pig">小豬佩奇</p>
    <p id="sheep">小羊蘇西</p>
</body>
```

## 後代選擇器

```
<head>
    <meta charset="UTF-8">
    <title>03_後代選擇器.html</title>
    <style>
        ul li {    /**空格代表ul的後代li且後代選擇器會選取所有後代(包含div)元素**/
            color: red;
        }

        ul li a {/**單獨指定a後代**/
            color: blue;
        }
        .subject li.fe { /**後代選擇與交集選擇器一起使用**/
            color: violet;
        }
        .subject div.fe {
            color: aqua;
        }
    </style>
</head>
<body>
    <ul>
        <li>抽菸</li>
        <li>喝酒</li>
        <li>燙頭</li>
        <li>
            <a href="#">燙頭</a>
        </li>
    </ul>
    <hr>
    <ol>
        <li>張三</li>
        <li>李四</li>
        <li>王五</li>
        <li>
            <a href="#">你好</a>
        </li>
    </ol>
    <hr>
    <ol class="subject">
        <li class="fe">前端</li>
        <div class="fe">學科介紹</div>
        <li>大數據</li>
        <li>UI</li>
    </ol>
</body>
```

## 子代選擇器

```html
<head>
    <meta charset="UTF-8">
    <title>04_子代選擇器</title>
    <style>
        div>a { /**子代選擇器 > 只選自己的子級**/
            color: red;
        }
        div>p>a {
            color: blue;
        }
        .foot>a {
            color: brown;
        }
    </style>
</head>
<body>
    <div>
        <a href="#">張三</a>
        <a href="#">李四</a>
        <a href="#">老五</a>
        <p>
            <a href="#">照六</a>
            <span class="foot">
                <a href="#">孫7</a>
            </span>
        </p>
    </div>
</body>
```

## 兄弟選擇器

```html
<head>
    <meta charset="UTF-8">
    <title>05_兄弟選擇器</title>
    <style>
        div+p {   /**+號代表單一緊緊相鄰的元素 且是元素下的元素**/
            color: red;
        }
        div~p {   /**~號代表所有緊緊相鄰的元素 且是元素下的元素**/
            color: red;
        }
    </style>
</head>
<body>
    <div>尚硅谷</div>
    <p>前端</p> 
    <p>java</p>
    <p>大數據</p>
    <p>UI</p>
</body>
```

## 偽類選擇器

選中當前狀態

屬性 :偽類選擇器    ex: a:hover 

| 超鏈接 | 超連接未點擊(訪問前 | :link | 連結未點擊前的設定樣式 | 如果要給連接設置四種狀態 需要lhva順序寫 |
| --- | --- | --- | --- | --- |
| 超鏈接 | 滑鼠懸停狀態 | :hover | 滑鼠懸停到這段超連結時，變更樣式 | 如果要給連接設置四種狀態 需要lhva順序寫 |
| 超鏈接 | 超連接點擊(訪問後 | :visited | 滑鼠點擊超連結後，變更樣式 | 如果要給連接設置四種狀態 需要lhva順序寫 |
| 超鏈接 | 超連接點擊時(訪問當下 | :active | 滑鼠點擊超連結時，變更樣式 | 如果要給連接設置四種狀態 需要lhva順序寫 |
|  |  |  |  |  |

## 結構偽類選擇器

根據元素的結構關係查找元素

| E:first-child | 查找第一個E元素 |
| --- | --- |
| E:last-child | 查找最後一個E元素 |
| E:nth-child(N) | 查找第N個E元素(第一個元素N值為1) |

nth-child(公式) 根據元素結構關係查找多個元素

| 偶數標籤 | nth-child(2n) |
| --- | --- |
| 奇數標籤 | nth-child(2n+1;2n-1) |
| 找到5的倍數標籤 | nth-child(5n) |
| 找到第5個以後的標籤 | nth-child(n+5) |
| 找到第5個以前的標籤 | nth_child(-n+5) |

## 偽元素選擇器

創建虛擬元素，用於擺放裝飾性的內容

| E::before | 在E元素裡面最前面添加一個偽元素 |
| --- | --- |
| E::after | 在E元素裡面最後面添加一個偽元素 |

必須設定content” ”屬性，用於設定偽元素內容，如果沒有內容，引號內留白就可以

偽元素預設是行內元素

權重和標籤選擇器相同