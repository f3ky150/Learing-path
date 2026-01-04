# steps逐帧動畫

動畫複合屬性當中的速度曲線 包含了steps()函數，可以用來實現撥放類似gif的效果

```css
@keyframes sprite{
	0% {
	   background-position: 0 0;
	 }
  100% {
	    background-position: -13700px 0;
   }
 }
.box {
  width: 548px;
  height: 513px;
  background-color: pink;
  margin: 200px;
  background: url(../../img/360ani.png) no-repeat left/13700px 513px;
  
  
  animation: sprite 1s steps(25) infinite;
  /*經常配合sprite精靈圖來實現動畫效果*/
}
```