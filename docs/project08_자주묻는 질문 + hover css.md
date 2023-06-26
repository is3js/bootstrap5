1. row 속에 `col-4 col-md-4 col-lg`를 이용하여 작은화면3, 큰화면 auto로 다들어가게 하며, **style로 height를 미리 fix한다**
    - **이 때, `높이가 정해진 no flex(col) 텍스트 수직 가운데 정렬`은 `높이와 동일한 line-height`를 주면 된다.**
```html
<div class="row">
    <div class="col-4 col-md-4 col-lg " style="height: 60px;line-height: 60px;">
    </div>
</div>
```
![img_1.png](../ui/height_with_line-height.png)
2. 내부 text를 쓸 땐 `빈div`안에서 > `a.text-decoration-none.글자색` > `h태그`로 쓴다.
```html
<div class="col-4 col-md-4 col-lg " style="height: 60px;line-height: 60px;">
   <div>
      <a href="#" class="text-decoration-none text-white">
         <h4>허리디스크</h4>
      </a>
   </div>
</div>
```
3. **`빈div`에다가 style=로  `배경을 삽입`한다.**
```html
 <div style="background-color: #E7B277;">
     <a href="#" class="text-decoration-none text-white">
         <h4>허리디스크</h4>
     </a>
 </div>
```
![img_1.png](../ui/empty_div_with_bg.png)
4. **inline인 `a태그`를, `높이 및 width가 정해진 부모 내부에서 꽉 차지하게하려면`, `d-inline-block`을 주면, 한줄표시 + width를 다 먹게되고, 부모의 width를 쫓아간다**
```html
<div class="col-4 col-md-4 col-lg " style="height: 60px;line-height: 60px;">
    <div style="background-color: #E7B277;">
        <a href="#" class="d-inline-block text-decoration-none text-white">
            <h4>허리디스크</h4>
        </a>
    </div>
</div>
```
![img_1.png](../ui/a_with_inline_block.png)

5. 이제 a를감싸는 div를 **`높이/너비가 정해진 col`에 가득채우기 위해, `w-100, h-100`을** 주고, `text-center`까지 준다
```html

<div class="w-100 h-100 text-center"
     style="background-color: #E7B277;">
    <a href="#" class="d-inline-block text-decoration-none text-white">
        <h4>허리디스크</h4>
    </a>
</div>
```
![img_1.png](../ui/a부모div의%20w-100h-100.png)

6. 이제 가로길이는 신경안써도 되는, col 높이 120px의 패턴그림을 배경으로 지정한다. rounded 까지 div에 추가한다
   - 높이만 맞추고, 반복 position size는 신경안쓴다
```html
<div class="w-100 h-100 text-center rounded"
     style="background: url('images/patterns/001.png');">
   <a href="#" class="d-inline-block text-decoration-none text-white">
      <h4>치료기간?</h4>
   </a>
</div>
```

7. 이제 6개를 복붙한 다음, 레이아웃을 보고 **w-100, h-100중인 div말고 `col에서 p`를 줘서 `내부요소 크기를 조절`한다**
```html
<div class="col-4 col-md-4 col-lg p-1 " style="height: 120px;line-height: 120px;">
```
