1. col <->  content(card) 사이에 `div.swiper.xxxxSwiper` > `div.swiper-wrapper` > 개별 card마다 `div.swiper-slide` 씌우기

2. col에 있던 flex설정들을 삭제하고, 좌측에 col-7 / 우측col-5 을 둔다음, 우측 col-5에 배치한다.
- row에 align-items-center를 추가해서 한 row의 col들이 수직가운데 정렬되게 한다
3. .xxxSwiper 선택자로 swiper 객체 만들고 설정하기
    - pagination없이 1개만 보이도록 일단 설정
    - spacebetween: 0이 핵심 중 하나
    - autoplay로 지정해서, eventlistener로 focusin 되게 할 예정

```js
<!-- 의료진 소개 swiper-->
<script>
    var doctorSwiper = new Swiper(".doctorSwiper", {
    slidesPerView: 1,
    // slidesPerView: 'auto',
    spaceBetween: 0,
    grabCursor: true,
    loop: true,
    autoplay: {
    delay: 4500,
    disableOnInteraction: false,
},
    // pagination: {
    //     el: ".swiper-pagination",
    //     clickable: true,
    // },
});
</script>
```

4. **이제 `active slide`가 돌아가면, 해당 card에 focusin이 작동하도록 `swiper객체에 on`을 걸어준다.**

```js
doctorSwiper.on("slideChangeTransitionEnd", function () {
    var activeSlide = doctorSwiper.slides[doctorSwiper.activeIndex];
    $(activeSlide).find('div.card').focusin();
});
```
![img.png](../ui/의료진소개21.png)

5. **이제 slider에 여러개가 같이나오도록 설정한다.**
   - spaceBetween이 0이라도, 1.5개 등으로 하면, 주인공을 가운데로 못보낸다?!
   1. .xxxSwiper 선택자에서 max-width를 1.5개분량(150px + @)보다 약간 더준다.
      - **이미 끝에까지 나오게 되면, 더이상 안굴러가고, 회전되 안되게 된다.**
   2. .swiper-warpper 선택자에서는 slide를 수직정렬해준다.
   3. .swiper-slide 크기를 이미지에 맞게 조절한다.
   4. swiperjs에서는 `slidesPerView`를 1 -> `auto`로 수정한다 + `centeredSlides: true` 를 추가한다


6. 이제 슬라이드가 지나간 것에 focusout도 따로 해줘야한다
7. 
