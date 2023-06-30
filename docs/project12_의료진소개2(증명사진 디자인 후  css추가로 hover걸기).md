### 증명사진 디자인

1. 각 인물영상은 정해진 col크기에서 `div.card>div.card-img+.card-body+.card-footer`로 구성될 것이다.
2. 영상대신 div.card-img에 `img.img-fluid`를 정해진 사각크기에 맞게 입력한다
3. `div.card-body`에 들어갈 텍스트들의 가운데 정렬은 `div.card`에서 전체요소들에게 가운데 정렬시키자. text-center
    - 개별 세로 나열은 `ul.list-unstyled>li`를 활용한다
    - 여차하면 br태그로 줄바꿈해준다.
4. `div.card-footer`에 들어갈 단어는 h6>strong 을 활용한다
5. **커스텀을 시행함**
   - card에 border-0을 추가한다
   - card-body에 border-top만 줘서, 이미지 밑에 줄이 생기게 한다
   - card-body에 py-1을 줘서 위아래 간격을 고정시킨다
   - footer는 border-0을 주고, p-0을 주고, 배경을 bg-transparent를 준다
   
6. **추가 커스텀 for swiper**
   1. **`img태그의 부모div`의 `height`를 150px `고정`**하고, **img태그의 img-fluid를 삭제하고 , `h-100 w-auto`를 줘서, `이미지를 고정된 부모높이`에 맞춘다**
   2. **card자체를 `width:fit-content`로 줘서, 사진 너비에 꽉맞춰, border도 사진크기에 맞춘다**
   3. card-footer는 주석처리한다
```html
<div class="card text-center border-0 m-0" style="width: fit-content;">
    <div class="card-img overflow-hidden" style="height: 150px; ">
        <img src="images/doctors/card001.png" alt="" class="h-100 w-auto">
    </div>
    <div class="card-body border-top py-1 ">
        <span class="fw-bold fs-index" style="letter-spacing: 1.5px">조재성 <small class="fw-light">원장</small></span>
    </div>
</div>
```
![img.png](../ui/의료진소개15.png)
7. div.card-img의  height를 md이상시 150px md미만시 120px로 반응형 `.h-120to150`을 정의해준다.
```css
    @media (max-width: 767px) {
   .w-35to25 {
      width: 35% !important;
   }
   .w-65to75 {
      width: 65% !important;
   }
   .h-120to150 {
      height: 120px !important;
   }
}

@media (min-width: 768px) {
   .w-35to25 {
      width: 33%!important;
   }
   .w-65to75 {
      width: 67% !important;
   }
   .h-120to150 {
      height: 150px !important;
   }
}

```
```html
<!--<div class="card-img overflow-hidden" style="height: 150px;">-->
<div class="card-img overflow-hidden h-120to150">
```
![img.png](../ui/의료진소개16.png)

8. 이제 col안에서, 여러개의 card를 붙혀 배치하기 위해 col에 d-flex flex-row justify-content-center를 주자
```html
<div class="row justify-content-center">
   <div class="col d-flex flex-row justify-content-center" >
```
9. 사진들끼리 너무 붙어있는 것 같아서, border는 유지하도록 `div.card-img`에 `px-3`을 준다. ****
```html
<div class="card-img overflow-hidden h-120to150 px-3">
   <img src="images/doctors/card001.png" alt="" class="h-100 w-auto">
</div>
```
![img.png](../ui/의료진소개18.png)


### 증명사진 <-> 인물 자세히 간에 css선택자로 hover걸고 + data-i=""로 순서 넘겨받기
1. 증명사진 card마다 (원래는 col마다) `.doctor-hover` 선택자와 `data-i="1"` 1부터 데이터를 심어놓는다.
```html
<div class="card text-center border-0 m-0 doctor"
     style="width: fit-content;"
     data-i="1"
>
```

2. 원래는 col.css -> `.children('.card').addClass('shadow')`로 **직접적인 자식은 .find()ㅇ벗이 바로 .children()선택자로 선택하여 card의 shadow를 줘서 hover를 확인**시킨다
   - **여기서는 card.css에서 `.find('.card-img>img')`로 img태그를 찾아, addClass가 아닌 `.css(속성, 값)`으로 transform, scale()을 준다**
   - hover는 항상 하고 나서, function을 연결하여 복구하는 것을 동시에 처리해준다
