### mobile banner - bootstrap carousel + 951x370 px 
1. bootstrap caption잇는 예제를 들고온다
2. 추가해서 6개의 배너로 미리 만든다
    - data-bs-slide-to="5" 숫자 0부터 수정
3. div.carousel에 `data-bs-ride="carousel"` 옵션을 줘야 자동으로 autoplay된다.
4. div.carouse.slide에 `.carousel-fade`를 추가하면 애니메이션으로 사라진다
5. **이미지는 `951x370 px`을 맞춰야 높이변화가 없을 것이다.**
5. section의 mt-4를 mt-1로 줄이자
6. **lg부터는 안보여야하는 모바일전용이므로 `section태그에 d-lg-none`을 추가한다**


### PC banner by swiper js?
