### 1 container + row + col
1. sense) row는 `border:dashed 1px red;`, col은 **boostrap col외 모든 col-xx에 적용되도록 `ca`클래스를 만들고** `border: solid 1px blue;background: #EFEFEF;`로 영역 공부하기
   - sense) 여러 컨테이너 공통css인 `row`에 `m10|0`을 주면, 모든 row들이 상하에만 줄간격이 생겨서 2개이상의 row가 구분된다.
2. `col-sm`으로 시작하면, sm사이즈부터 col이 적용되고, **그전에는 적용안되는 일반 block -> 1줄(row)씩 쓰이게 된다.**
    - col-sm 3개 == col-sm-4 3개는 동일하다.
    - **col들이 특정크기 이하에서는 한줄로 쓰고 싶다면, `col-특정크기-x`로 시작하면 된다. 그전에는 col적용이 없는 1row들이 된다.**
3. container 대신 `container-fluid`를 쓰면, `양쪽 margin 0이며 화면width를 100%`로 꽉 채운다.
4. col-x들 총합이 12가 안되게 주면, `가장 오른쪽col 우측`에 나머지 공간이 `margin도 아닌 빈 공간`이 된다.
5. col-x들 총합이 12가 넘어가게 주면, `합쳐질시 12를 넘는 우측col은 다음줄로` 넘어가고, 다음줄에서 나머지놈외 공간은 margin도 아닌 빈 공간`이 된다.


### 2 합12초과로 줄넘김 + div.w-100으로 강제줄넘김.
1. 12를 넘어가면, 다음줄로 가는 것을 이용해서 **작을땐 총합 12 -> 마지막을 다음줄로 넘길 때 -> 합12+ 12 = 총합 24(2줄) -> 전부 한줄로 각 12**
2. **대박) col들 중간에 `div.w-100`으로 width를 꽉 찬 것을 중간에 넣으면, `다음col합이 12을 안넘겨도 줄바꿈할 수 있다`**

### 3 작을 땐 안보이게 / 클 때 안보이게
1. `.d-none.d-md-block` : 작을 때 안보이게
2. `.d-md-none` : 클 때 안보이게
3. 2개를 같은size로 하면, 작을 때 <-> 클 때를 change시키도록 보일 수도 있다?!
3. 마지막 col들에게도 적용할 수 있다.


### 4 수직/수평 정렬
1. sense) 수직정렬 test시에는 .row에 100 height를 .ca에 30 height를 주고, row와 col들 사이에 공간을 만들어 정렬테스트한다.
    ```html
    <style>
    .row {
          border:dashed 1px red;
          margin: 10px 0;
          height: 100px;
        }
        .ca
        {
          border: solid 1px blue;
          background: #EFEFEF;
          height: 30px;
        }
    ```
2. sense) 수평정렬 test시에는 col들을 12를 안채운체 테스트한다
   ```html
   <div class="container">
     col-12안채운 row(flex)에 justify-content-center(jcc) col들 가운데정렬
     <div class="row justify-content-center">
       <div class="ca col-sm-3 ">3</div>
       <div class="ca col-sm-3 ">3</div>
       <div class="ca col-sm-3 ">3</div>
     </div>
   </div>
   ```
3. **수직정렬(start, center, end)의 종류**
   1. row에 `align-items-xxx`
   2. col에 `align-self-xxx`

4. **수평정렬의 종류**
   1. row에 `justify-content-xxx`
      - start, center, end, around, evenly, between

### 5 order, offset, margin
1. order-숫자는 no order들보다 뒤쪽에서, 순서정렬한다
2. order-first, last는 no order들보다 앞쪽에서, 순서정렬한다.
3. **col-12못채울 때, `offset-x`는 `col-x`만큼 왼쪽에 여백을 준다.**
4. **col-12못채울 때, `ms-x, me-x`는 `col보다 작은 margin값`으로 왼쪽/오른쪽 여백을 준다.**
5. **col-12못채울 때, `ms-auto, me-auto`는 `col못채운 공간`을 `왼쪽, 오른쪽`에 쏟아부어서, 서로 밀리게 한다**

### 6 각종 태그
1. sense) text값은 `{}`로 입력. 연달아 숫자는 `$`로 표시후 `*숫자`
   - 예시> h${jswork$}*6
   ```html
   <h1>jswork1</h1>
   <h2>jswork2</h2>
   <h3>jswork3</h3>
   <h4>jswork4</h4>
   <h5>jswork5</h5>
   <h6>jswork6</h6>
   ```


### title, text(lead,mark,del+s,blockquote), list.list-unstyled, dl.row와 dt.col+dd.col+.text_truncate
1. h1보다 더 크게하고 싶으면 `display-x`
2. p.lead태그는 특정단락 강조, mark or .mark로 음영, del태그s태그로취소선, abbr, 
3. **인용문은 `blockquote.blockquote.text-xxxx정렬 > p태그+footer.blockquote-footer`**
4. **list는 거의 `ul.list-unstyled`와 `ul.list-inline>li.list-inline-item`**
5. 용어모음집list는 `div.container`안에서 `dl.row>(dt.col-size-x + dd.col-size-y)*총합12씩 여러개`


### code
1. 언어에 code태그 < pre태그(공백, 들여쓰기) + width,height, overflow-y-scroll을 준다.

### img + picture(택1) + figure(with figcaption)
1. img는 inline이며, 크기가 클 경우, container를 뚫고 나가기 때문에, 기본적으로 `.img-fluid`를 써서, max-width:100%, height:auto를 줘야한다.
2. `.img-thumbnail`은  `.img-fluid` + border+padding이다.
3. 부유속성은 마치 inline-block처럼 행동하며, 텍스트들이 감싼다. 끝내려면 `div.clearifx`를 마지막에 추가한다
   - [참고 블로그](https://webclub.tistory.com/606)
4. **inline인 img태그를 부모에 대해 자신을 가운데 정렬하려면, `.d-blcok.mx-auto`를 써야한다.**
   ```html
   <img src="images/qrcode.png" class="d-block mx-auto" alt="">
   ```
5. 부모에서 자식img태그(inline)을 가운데 정렬하려면, **부모의 `inline자식`정렬용 `.text-center`를 쓰면 된다.**
   ```html
   <div class="text-center">
     <img src="images/qrcode.png" class="" alt="">```html
   </div> 
   ```
6. `picture>source:media+img.img-fluid`는 해당media 사이즈별 img를 지정하고, 아니면 img태그를 택1해서 보여준다.
7. `figure.figure>img.figure-img.img-thumbnail+figcaption.figure-caption.text-center`는
   - .figure를 통해, block인 figure를 img태그처럼, 부모를 inline으로 만들고
   - .figure-img를 통해, img태그와 caption사이 여백을 주고
   - .figure-caption을 통해, block은 유지되지만, 글자크기+색을 caption용으로 변경하며
   - .text-center로 figcaption자체는 block이지만, inline자식용(content, text) 가운데 정렬을 시킨다.
   ```html
   <figure class="figure">
    <img src="images/qrcode.png" alt="" class="figure-img img-thumbnail">
    <figcaption class="figure-caption text-center">QR코드</figcaption>
   </figure>
   ```

### table
1. 기본 태그는 `table.table>(thead>tr>th*4)+(tbody>tr>td*4)` 이다
2. 부모에 `.table-responsive`를 주면, 원본크기 + x-scroll이 생긴다. 보통은 `.table-responsive-sm`부터는 더 작아지면서, scroll을 만들게 한다.
3. 전반적인 테마는 .table.table-dark / .table.table-light 로 주고, head에만 줄거면, thead.table-dark, thead.table-light로 준다.
4. 간격을 줄이려면 table.table-sm을 준다.
5. 색은 tr, td태그에 .table-primary로 준다.
6. hover는 table태그에 .table-hover을 준다.
7. border는 주는데 안쓸 듯. table.table-bordered or table.table-borderless로 준다.
   `div.table-reponsive-sm>table.table.table-sm.table-hover>(thead.table-dark>tr>th*4)+(tbody>tr>td*4)`

### 10 color(text-x, bg-x, border-x, rounded-x)
1. sense) div.wh(block 정사각형)을 flex or row 속 col아닌데 수평배치 하는 방법은 `float:left`가 달린 cls로 만들어서 바로 사용하는 것
   - border 색 등 알아볼 때 사용함
   ```html
   <style>
     .wh {
         width: 100px;
         height: 100px;
         background: #EFEFEF;
         float: left;
         margin: 10px;
     }
   </style>
    <div class="wh"></div>
    <div class="wh"></div>
    <div class="wh"></div>
   ```
   
2. text-x로 텍스트색을 줄 수 있다. 특이한 것은 `text-white-50`
3. bg-x로 배경색을 줄 수 있다. 특이한 것은 `text-transparent`
4. border색은 `border-색`으로 줄수 있다. `border or border-방향`이 뚤려있어야한다.
5. `.border.border-방향-0` 조합으로 특정방향 뚤리게 만들 수 있다.
6. rounded or rounded-방향으로 둥글게 만드는데, 1방향 지정시 2꼭지점을 둥글게 만든다.
7. rounded-pill, rounded-circle 도 있다.


### 11 btn-close, float, overflow
1. button태그는 `inline-block`이다. `&times;`의 text는 x버튼의 x를 나타낸다.
   - bootstrap4에서는 button.close + &times;(x)로 float:right된 닫기 버튼을 만들었다.
   - **지금은 `button.btn-close.float-end`로 만들 수 있다.**
2. float는 `하고나서 div.clearfix` 또는 `부모div.clearfix 안에서` 수행할 수 있다.
3. br을 포함한 텍스트들로 정해진 width, height를 넘치는 경우, 뚫고나오는데, `overflow-auto`는 scroll을, `overflow-hidden`은 숨긴다.


### 12 align-xxx(수직정렬) for inline, inline-block, table-cell(td)
1. flex의 align-self-xxx 버전으로서, 부모에 대해 자신을 정렬한다
   1. inline: 한줄에 `컨텐츠의 크기 만큼`만 공간을 차지, 주의할 점은, `width와 height 속성을 지정해도 무시` + `상하간격 반영안됨`.
   2. block: `전후 줄바꿈`이 들어가 다른 엘리먼트들을 다른 줄로 밀어내고 `혼자 한 줄을 차지`합니다. 
      - 대표적인 block 엘리먼트로 div이나 p, h1
   3. inline-block: inline 엘리먼트처럼 전후 줄바꿈 없이 한 줄에 배치되지만, block 엘리먼트처럼 `width와 height 속성 지정` 및 margin과 padding 속성의 `상하 간격 지정`이 가능. 
      - inline과 달리, 여러 개의 엘리먼트를 `한 줄`에 정확히 `원하는 너비`만큼 배치할 수 있기 때문에 레이아웃에 활용
      - button이나 input, select 태그
      - 참고 : https://mygumi.tistory.com/368
      - img와 텍스트를 같은 요소에서 중간으로 배치하기 위해 많이 사용
         - text에 line-height 를 주고 img 태그에 vertical-align: top 주고 쓰면 웬만한 경우에서는 원하는 결과를 낸다.
      - 예시: https://dkrnfls.tistory.com/246
2. **table의 cell에 해당하는 `td`에 class=로 주면 수직정렬된다.**
3. `align-baseline`은, 부모`text`의 baseline과 내text의 baseline을 맞춘다
4. `align-top`은, 부모top에 내top을 맞춘다.
5. `align-text-top`은, 부모`text-top`에 내top을 맞춘다.
6. `align-middle`은, 부모`text-baseline + text(x)의 높이1/2`에 내 middle을 맞추는 듯
7. `align-bottom`은, 부모bottom에 내 bottom을 맞춘다.
8. `align-text-bottom`은, 부모`text`의 bottom에 내 bottom을 맞추는 듯
9. **큰요소(이미지)를 align-top으로 걸어놓고, 내 text의 line-height를 큰요소의 height로 줘서 내text의 중간이 큰요소의 중간에 오게 한다**

 
### 13 m-x, p-x, w-x, mw-100, mh-100, vw-100, vh-100
1. m-x 은 `방향이 같지 않으면` 중복해서 줄 수 있다. `방향이 같`으면, `더 큰값으로 대체`된 듯. m-0 ~ m-5까지다.
   - p-x도 마찬가지다.
2. p-x가 영역을 넘어서는 경우, top, left를 우선 띄우고 나머지를 띄운다.
3. `w-x`는 left시작, 내부content가 있어야 작동, 한줄차지 block의 영역을 줄인다. %로 작동한다
4. `h-x`는 부모에 충분한 height를 준상태에서, 1줄에 나열시 자식들을 inline-block으로 주고 테스트한다. %로 작동한다
   - `h-auto`는 `w-auto`와 달리, content만큼 차지한다.
5. mw-100, mh-100은 max-width: 100%를 대신한다. 1가지만 존재함.
6. vw-100, vh-100은, 자신으 시작위치에서, 화면크기만큼 차지하게 된다.
   - container안이라면, 시작은 자식위치이지만, 뚫고 나올 것이다.

### 14 shadow, ratio + iframe, width내 text-x, fw-x, fst-italic,
1. shadow는 shadow-none, shadow, shadow-sm, shadow-lg 로 존재한다
2. iframe은 inline 300px 고정인데, ratio.ratio-비율 을 통해 큰화면의 반응형을 만들 수 있다.
3. width가 정해진 div(block)에서는 text-x로 줄바꿈을 다룰 수 있다.
   1. `text-nowrap`이 기본인데
   2. `text-wrap`을 하는 순간 width를 넘어가면 height로 넘어간다
   3. `text-break`는 공백/하이픈이 아닌 곳에서 height로 넘긴다
   4. 그외 -truncate, -lowercase, -uppercase, -capitalize가 있다.
4. **`text-reset`은 글자색만 원본을 무시하고 부모색을 받는다. -> a태그에 사용**
5. **`text-decoration-none`은 글자색이 아닌, 글자스타일을 원본을 무시하고 부모색을 받는다. -> a태그에 사용**
6. `fw-x`로 font-weight를 조정한다. bold, normal, light 등
7. `fst-italic`은 이탤릭체로 바꾼다.


### 15 flex1_row,column방향 및 수평, 수직정렬
1. sense) flex를 테스트할 땐 div.d-flex.border.border-dark 안에, div.p-2.border.border-success로 box를 만들어 text
   ```html
    <div class="d-flex border border-dark">
        <d class="p-2 border border-success">flex-item1</d>
        <d class="p-2 border border-success">flex-item2</d>
        <d class="p-2 border border-success">flex-item3</d>
    </div>
   ```
### 16 flex-fill, grow, shrink, 밀기를 위한 margin-auto

### 17 flex-wrap(d-flex), order(flex-item), align-content-x(for multi row)

### 18 alert

### 19 badge breadcrumb

### 20 button

### 21 button group

### 22 card

### 23 list-group

### 24 nav and tab

### 25 pagination and progress


### 26 spinner

### 27 carousel

### 28 carousel custom 1(외부버튼, line-gradient, sidebar용)
### 29 vertical carousel by splidejs
- 참고1: https://www.youtube.com/watch?v=wy1LERGE7Qs (17분 기초)
- 참고2: 대박) https://www.youtube.com/watch?v=dmi1v4OZveI

1. css, js(body 끝나기 전)를 입력시킨다
2. div.splide.bg-transparent로 표시용 컨테이너를 만들고
3. div.splide__slider>div.splide__track>ul.splide__list>(li.splide__slide>img.fluid)를 여러개 만든다.
4. script에서, .slide(표시용 css)를 선택자로서 Splide 객체를 초기화한다
   ```js
    var splide;
   
    window.document.addEventListener('DOMContentLoaded', () => {
        splide = new Splide('.splide').mount();
    });
   ```
   
5. 옵션은 객체 생성시 2번재 인자로 준다
   ```html
   <script>
       var splide;
   
       window.document.addEventListener('DOMContentLoaded', () => {
           splide = new Splide('.splide', {
               // vertical
               arrows             : false,
               direction: 'ttb', // 슬라이드방향 -> height or heightRatio필수
               heightRatio : 0.27, // direction 바뀔 때 height or heightRatio필수
               paginationDirection: 'ttb', // 페지네이션 방향
               // 기본설정 'loop' 무한반복, 'slide' 1회석
               type: 'loop',
               perPage: 1,
               perMove:2,
               start: 0,
               wheel: true,
               autoplay: true,
               interval: 2000,
               // speed: 100,
           }).mount();
       });
   </script>
   ```
   6. img를 css로 height를 맞춘다.
      1. 왼쪽상단배너로서 `600x160` / `300x80` px을 맞춘다.
      2. div.row > div.`col-4` 에 splide를 넣되, `d-none d-md-block bg-transparent`으로 md부터 나오게 한다.
      3. `img.img-fluid`는 width 100% x height auto를 차지하고 있으니 `부모의 witdh`를 잡아주면 -> height도 알아서 잡힌다.
         - **이 때, col이 커진다고 width가 한없이 커진다면, height가 그만큼 커지니, Splide객체의 공간인 `splide__slider`에 `max-width: 400px;`에 제한을 둬서 -> height 제한을둔다.**
      4. Splide에 수직옵션인 `direction: 'ttb'`를 위해 반응형 width에 대해 `heightRatio : 0.27`옵션을 추가한다.
         - 수직일 때는 `arrows: false`, `paginationDirection: 'ttb'`를 추가한다.
      5. 이제 pagination옵션을 수정한다. 오른쪽 끝에 몰고, 점3개가 md에 세로방향으로 잘 설 수 있도록
         1. pagination 뭉치의 상하여백을 줄인다.
            ```css
               .splide .splide__pagination {
               /* 기존 상하패딩 1em -> 상하 여백을 줄임*/
               padding: 0.2em 0;
               }
            ```
         2. 수직일 때 pagination-ttb 뭉치의 위치를 좀 더 오른쪽으로 보낸다.   
            ```css
            .splide .splide__pagination--ttb {
                /* 기존 left:auto; right:0.5em -> right 0으로  */
                right: 0;
            }
            ```
         3. pagination 개별 li들의 간격을 행간으로서 좀 더 줄인다.   
            ```css
            .splide .splide__pagination li {
                /*  flex-column의 li들의 행간으로 indicator간격 조절  */
                /*  기존 행간 1 -> 0.1 */
                line-height: 0.1;
            }
            ```
### 30 splide + horizontal card


### 31 accodian(예제위주) + icon 커스텀
1. 부트스트랩 아이콘은 따로 css를 추가해줘야한다. icons페이지 -> install cdn
   - cdn없이 svg -> urlencode for svg 복붙 후 css용으로 변경(background-image)로 사용

### 32 dropdown

### 33 navbar

### 34 scrollpy로 만드는 cotents

### 35 Toast

### 36 Modal

### 37 form

### 38 login form dark
- https://www.youtube.com/watch?v=QxQLzn0H9C0&list=PLEGWy2sQ80Yvpl034sE6zYAPQM3dpzDon&index=3

### 39 floating login form + select
- https://www.youtube.com/watch?v=QxQLzn0H9C0&list=PLEGWy2sQ80Yvpl034sE6zYAPQM3dpzDon&index=3

### 40 login form with sns button
- https://www.youtube.com/watch?v=H_eFkSf7s3c
