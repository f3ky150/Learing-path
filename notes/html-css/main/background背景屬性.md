# background背景屬性

背景圖是依附在標籤容器(盒子)底下  所以會先給標籤製作一個盒子 再將圖片放進去作為背景圖

***baclgorund-image: url:()***  指定路徑圖片

*background-repeat: no repeat*(不平鋪)/repeat(平舖[預設])/repeat-x(向x方向平鋪)/repeat-y(向y方向平鋪)

*background-position:* 數字+px or 英文 top bottom  left right 其中一個屬性沒有書寫 預設是居中 

                                     可以改成定義座標 或是百分比(xxxpx xxxpx/  xx%)

*background-size: cover:*(等比縮放完全覆蓋盒子)/contain(等比縮放到碰到盒子邊

 cover因為和盒子一起縮放 所以盒子如果有動畫放大 裡面的圖片也可以看到更多

如果是用contain 盒子被放大 圖片會被拉伸

background-attachment: fixed(背景固定不動)/local(背景隨滾輪移動[預設])

*background[複合屬性]:*  背景色 背景圖 背景圖平鋪方式 背景圖位置/背景圖縮放 背景圖固定

                                       pink url(.//images/1.png) no-repeat right center/cover fixed

- 背景圖位置/背景圖縮放要一起寫 否則其中一個無法生效