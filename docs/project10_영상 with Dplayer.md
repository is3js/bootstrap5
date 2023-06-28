1. col안에 영상을 뿌려줄 파트를 작성한다.
   - **기존 잡아둔 col높이 349px를 삭제하고, 내부에서 컨텐츠로 채울 준비를 한다**
    - `.film_focus>.film_focus_imgs_wrap.main-content>ul.film_focus_imgs.w-85` 안에 여러 li태그를 만든다
    - li들은 div#dplayer1공간에 style="w100;h컬럼높이;"로 줘서 4개를 만든다
    - 이제 **자리 잡기를 위해 div#dplayer들 대신 img로 채워넣는다**
```html
<!--<div class="col-12 col-lg-8" style="height: 349px;">-->
<div class="col-12 col-lg-8" >
   <div class="film_focus">
      <!-- 영상 파트 -->
      <div class="film_focus_imgs_wrap main-content">
         <ul class="film_focus_imgs w-85">
            <li>
               <!--                                <div id="dplayer1" style="width: 100%;height:349px;"></div>-->
               <img src="https://i3.ytimg.com/vi/jlUAviuAuGk/hqdefault.jpg" style="width: 100%;height:349px;"></img>
            </li>
            <li>
               <!--                                <div id="dplayer2" style="width: 100%;height:349px;"></div>-->
               <img src="https://i3.ytimg.com/vi/FoiRAZSHKUI/hqdefault.jpg" style="width: 100%;height:349px;"></img>
            </li>
            <li>
               <!--                                <div id="dplayer3" style="width: 100%;height:349px;"></div>-->
               <img src="https://i1.ytimg.com/vi/P_06Nvmunrk/hqdefault.jpg" style="width: 100%;height:349px;"></img>
            </li>
            <li>
               <!--                                <div id="dplayer4" style="width: 100%;height:100%;"></div>-->
               <img src="https://i4.ytimg.com/vi/7NER1ikd8AU/hqdefault.jpg" style="width: 100%;height:349px;"></img>
            </li>
         </ul>
      </div>
</div>
```

![img.png](../ui/유튜브%20초기형태.png)
2. thumbnail이 들어갈 공간을 div.film_focus 안에 넣어준다
   - .film_focus_desc.d-none.d-md-block>ul#film.film_focus_nav 으로 작은화면에서는 안나온다
   - li들은 현재일 경우 `cur` 선택자를 갖는다.
   - li내부에는 img태그를 width 100px, height 79px로 준다?!
```html
 <!-- thumbnail 파트 -->
<div class="film_focus_desc d-none d-md-block">
    <!--제목?-->
    <h3>우아한 한의원 유튜브입니다.</h3>
    <ul id="film" class="film_focus_nav">
        <li class="cur">
            <img width="100" height="79" src="https://i3.ytimg.com/vi/jlUAviuAuGk/hqdefault.jpg" alt="">
        </li>
        <li>
            <img width="100" height="79" src="https://i3.ytimg.com/vi/FoiRAZSHKUI/hqdefault.jpg" alt="">
        </li>
        <li>
            <img width="100" height="79" src="https://i1.ytimg.com/vi/P_06Nvmunrk/hqdefault.jpg" alt="">
        </li>
        <li>
            <img width="100" height="79" src="https://i4.ytimg.com/vi/7NER1ikd8AU/hqdefault.jpg" alt="">
        </li>
    </ul>
</div>
```
![img.png](../ui/유튜브%20초기형태2.png)


3. 이제 각 css 선택자별 css를 생성해준다
- 참고 이미지 github: https://github.com/bylu/js-css-/tree/85354c52b625b87a33bf7afa1a2dd90c4d52afb8/banner%E8%BD%AE%E6%92%AD/images
- 참고 css
   ![img.png](../ui/youtube%20css%20참고.png)

```html
<style>

Kiln focus.fils focur_ins_wrap lwidth 100% height: 349px;background url (images/116WJqXaXeXXXXXXXX-32-32.gif) no-repeat center center.) fila focus ul.filn focurings(width 100% height: 9999en position: abrolute;left: 0; top: 0:1 fils focur lwidth: 100% height: 349px; overflow. hidden position relative;

fila focus ul (padding: 0px;margin: 0px; list-style: none:]: .fils focus ul.fils focur inge li theight: 349px;overflow:hidden:1

film focur.fils foeur desc h31

height: 45px.line-height 45px.overflow:hidden position: absolute;left:0;top:0;background: rgba(0, 0.0..5).color #fff width: 100%;padding-left: 24px:-index: 99, font-size: 10px; filter progid:DXImageTransform. Microsoft. gradient (enabled='true',startColorstr='#7F000000, endColorstr="#7F000000"); 1

film focus ul.file_focus navfwidth 10% height: 349px;background: #424242;position: absolute;right: 0px; top: 0;z-index: 100:1

.fila focus ul. fila forur nav 11 height: 85px;background: url(imager/T1WiB5Xf0EXXXXXXXX-1-75.png) repeat-x;margin: 1px 1px 1px 0 padding 5px file focus ul.fila focus nav li.eur [background url (inager/T1089XmDEXXXXXXXX-398-70.png) no-repeat 0 2px width 130px; left:-10px,andex

.file focus ul.fils focus nav is ang (position absolute;left:5px;top: 5px;}

.fils focus ul.fila foeur nav 11. cur ing (left 19px:width 110px height: 79px;margin-top:-1px:1

fil focus ul.fils focus nav 11 b4lcolor #ttt:]

fila forur alfils toour nav li plcolor 999;line-height: 1. Den:)

knowcon right (width 100% height: 249px border-top: 2px #8eb solid.background #FIFUFD box-shadow: 0px 5px 10px rgba(0, 0.0, 0.53)

140

-pulsing before. pulsing after festent parition abrelute.) .main-content Idisplay: grid width: 100%:1

media (max-width: 767px) [

65 (width: 100% portant]

dis (min-width: 760px) [ 65 vidth es aportant]

</style>

alt-"EduWorkF

, 100

0 5px postion relative:)

본 자료

X 40

100%
```
