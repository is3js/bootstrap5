1. 검색엔진을 위해 blind css를 만든다

```css
.blind {
    position: absolute;
    overflow: hidden;
    clip: rect(0 0 0 0);
    margin: -1px;
    width: 1px;
    height: 1px;
}
```

2. 틀을 잡는다.

```html
<!-- cast 메뉴 시작-->
<style>

</style>
<nav>
    <div class="container">
        <h3 class="blind">탭 메뉴</h3>
        <div>
            <!-- 전체 | 구역 | 왼쪽 | 오른쪽-->
            <button>
                <span class="blind">전체 메뉴</span>
            </button>
            <div>

            </div>
            <button>
                <span class="blind">이전 메뉴</span>
            </button>
            <button>
                <span class="blind">다음 메뉴</span>
            </button>
        </div>
    </div>
</nav>
<!-- cast 메뉴 끝-->
```

2. 버튼은 inline-block이 될 건데, inline-block끼리 붙으면 이상한 공간이 생기므로 `float-left`를 활용한다
    - **css + click기능을 위해 button에 `id`를 각각 배정해준다.**

```html

<div>
    <!-- 전체 | 구역 | 왼쪽 | 오른쪽-->
    <button id="toggle-all">
        <span class="blind">전체 메뉴</span>
    </button>
    <div id="toggle-list">

    </div>
    <button id="toggle-prev">
        <span class="blind">이전 메뉴</span>
    </button>
    <button id="toggle-next">
        <span class="blind">다음 메뉴</span>
    </button>
</div>
```

- 이제 각 id로 선택자를 잡아서, inline-block 대신 float: left로 배치한다.
- bootstrap으로서 class로 `float-start`를 배정했다.

```html
<!-- 전체 | 구역 | 왼쪽 | 오른쪽-->
<button id="toggle-all" class="float-start">
    <span class="blind">전체 메뉴</span>
</button>
<div id="toggle-list" class="float-start">

</div>
<button id="toggle-prev" class="float-start">
    <span class="blind">이전 메뉴</span>
</button>
<button id="toggle-next" class="float-start">
    <span class="blind">다음 메뉴</span>
</button>
```

3. float-start 요소들을 받아줄 부모의 빈div에는 `inline-block` 및 `w-100`을 준다.
    - block format context를 생성한다고 한다. 그래야 다음 것들과 연결될 수 있다?

```html
<!-- tab 메뉴 -->
<div class="d-inline-block w-100">
    <!-- 전체 | 구역 | 왼쪽 | 오른쪽-->
    <button id="toggle-all" class="float-start">
```

- 전체영역의 bottom에 보더를 추가해준다

```html

<div class="d-inline-block w-100 border-bottom">
```

4. 버튼들과 scroll공간 의 높이들을 css로 정해준다. (공통이라서 inline style안함.)

```html

<style>
    #toggle-all, #toggle-list, #toggle-prev, #toggle-next {
        height: 45px;
    }
</style>
```

- 4개를 묶었으니, float-start class도 그냥 css로 준다.

```css
 #toggle-all, #toggle-list, #toggle-prev, #toggle-next {
    height: 45px;
    float: left;
}
```

5. 공간빼고 버튼들만 width를 height와 동일하게 준다.
    - 이 때, 버튼들의 border를 강제로 제거하고, border-left만 준다.
    - 버튼들의 배경은 white로 준다

```css
/* 버튼들 */
#toggle-all, #toggle-prev, #toggle-next {
    width: 45px;
    border: none;
    border-left: 1px solid #dbeef3;
    background: white;
}
```

6. **이 때, float-left 정렬item들에, `width 정해진 버튼들을 제외한 공간`을 list가 다 차지하려면 `부모에 flex, 해당자식에는 flex-grow:1`을 줘야한다**
    - d-inline-block을 `d-inline-flex`로 변경한 뒤, #toggle-list에 `flex-grow-1`을 선택자로 준다

```html
<!-- tab 메뉴 -->
<div class="d-inline-flex w-100 border-bottom">
    <!-- 전체 | 구역 | 왼쪽 | 오른쪽-->
    <button id="toggle-all">
        <span class="blind">전체 메뉴</span>
    </button>
    <!-- scroll 공간-->
    <div id="toggle-list" class="flex-grow-1">
        ddd
    </div>
```

![img.png](../ui/탭메뉴1.png)

7. 이제 각 버튼에 img들을 `span태그`의 background로 공통으로 넣어주는 선택자 `tab-icon`을 만들어 입력해주고, **부모button id를 다르게 각각 준다**
    - span은 `absolute`, top + left 50% + transform: translate(-50%, -50%) 조합으로 가운데 위치시킨 뒤 에서 bg이미지 + cover로 준다.
    - 이 때, w,h를 부모에 대해 50%로 줬다. 직접 픽셀을 정해도 된다.
    - **그러려면 부모인 button들 자체가 `relative`여야한다**
    - **버튼들은 padding도 삭제해준다**

```css
/* 버튼들 */
#toggle-all, #toggle-prev, #toggle-next {
    width: 45px;
    padding: 0;

    border: none;
    border-left: 1px solid #dbeef3;
    background: white;

    position: relative;

}
```

```html

<button id="toggle-all">
    <span class="blind">전체 메뉴</span>
    <span class="tab-icon"></span>
</button>
<button id="toggle-prev">
    <span class="blind">이전 메뉴</span>
    <span class="tab-icon"></span>
</button>
<button id="toggle-next">
    <span class="blind">다음 메뉴</span>
    <span class="tab-icon"></span>
</button>
```

- 이제 각 버튼의 id를 잡고, 그 하위 .tab-icon의 span에 배경을 준다.

```css
    /* 버튼 icon 그림 삽입 */
#toggle-all .tab-icon {
    position: absolute;

    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);

    width: 40%;
    height: 40%;

    background-image: url("images/tabmenu/menu.svg");
    background-size: cover;
}
```

![img.png](../ui/탭메뉴2.png)

- 화살표 좌우측이미지는 width 30% / 40%로 맞춰준다


8. 이제 scroll공간에 ul>li태그로 데이터들을 집어넣는다

```html
<!-- scroll 공간-->
<div id="toggle-list" class="flex-grow-1">
    <ul>
        <li>한의원소개</li>
        <li>의료진소개</li>
        <li>길찾기</li>
        <li>자가진단</li>
        <li>연구실적</li>
        <li>비급여진료비</li>
    </ul>
</div>
```

9. 이제 ul태그에 list-style을 제거 + m0p0 을 지정한 뒤, 각 li태그에는 `float:left`를 걸어준다

```css
    /* scroll 공간 스타일 */
#toggle-list ul {
    list-style: none;
    margin: 0;
    padding: 0;
}

#toggle-list li {
    float: left;
}
```

![img.png](../ui/탭메뉴3.png)

10. 각 li요소들의 간격을 css로 추가한다

```css
#toggle-list li {
    float: left;

    margin-right: 10px;
    padding: 10px 7px 0;
}
```

11. **이제 다음줄로 넘어감 방지를 해야하는데, 기본은 `height`가 정해져있을 때의 `white-space:nowrap; overflow:hidden;`이다.**

- height를 주지 않으면 ul자체의 높이가 늘어난다. **다음줄방지를 했찌만, height가 없는 ul태그가 자체높이를 늘려버린다.**

```css
/* scroll 공간 스타일 */
#toggle-list ul {
    list-style: none;
    margin: 0;
    padding: 0;

    height: 45px;
    white-space: nowrap;
    overflow: hidden;
}
```

- **문제는, scroll하려면, 다음줄로 아예 안넘어가야하는데, `ul태그는 공간의 개념이 없이 넘어가버린다`**
    - scroll 공간이 flex-grow-1을 차지하고 있는 상황에서, **flex-grow된 공간을 차지할 `ul태그를 감쌀 중간공간`이 추가로 필요하다**
    - **나는 따로 공간을 마련하지 않고 `flex-grow-1`되는 flex-item을 다시 `d-flex`로 flex-layout으로 만들어버린 뒤, 공간책임자로서 overflow-hidden을 넣어준다**
    - **ul태그는 그에 대한 flex-item이지만 너비조정이 안되도록 `flex:none;`속성을 추가해서 nowrap이 적용되게 하였다.**
    - **flex:none;으로 대체된 white-space:nowrap;은 제거해주고, height도 공간div에 옮긴다**

```css
#toggle-list {
    position: relative;

    height: var(--tab-height);
    display: flex;
    overflow: hidden;
}

#toggle-list ul {
    flex: none;
}
```

12. 이제 하이라이트를 만들기 전에, 폰트등을 정리한다

- 나눔스퀘어 : https://github.com/moonspam/NanumSquare

```css
@import url(https://cdn.jsdelivr.net/gh/moonspam/NanumSquare@2.0/nanumsquare.css);

:root {
    --tab-font-family: 'NanumSquare', sans-serif;
}

#toggle-list ul {
    font-family: var(--tab-font-family);
    font-weight: 700;
}
```

```html

<div id="toggle-list" class="flex-grow-1 fs-13">
```

13. 높이를 모두 45-> 35px로 변경한다

```css
#toggle-all, #toggle-list, #toggle-prev, #toggle-next {
    float: left;
    height: 35px;
}

#toggle-all, #toggle-prev, #toggle-next {
    width: 35px;
}

#toggle-list ul {
    height: 35px;
}
```

- :root {} 에 변수로 저장해놓고 3곳에서 활용하게 한다

```css
    :root {
    --tab-height: 35px;
}

#toggle-all, #toggle-list, #toggle-prev, #toggle-next {
    float: left;
    height: var(--tab-height);
}
```

- 그에 따라 tab-icon의 width/height도 조정해준다.

14. 이제 hover시 굵기변화 / on(직접), active(js라이브러리)시 변화를 정의해준다.

- 추후 내부의 `li` -> `a`태그로 변화될 수 있다.

```css
#toggle-list li:hover {
    font-weight: 1000;
}

#toggle-list li.on, #toggle-list li.active {
    font-weight: 1000;
    border-bottom: 3px solid var(--color-submain);
    color: var(--color-submain);
}
```

```html

<li class="on">한의원소개</li>
```

![img.png](../ui/탭메뉴4.png)

15. 이 때 bottom의 bordre는, padding까지를 먹는데, tab-height를 적용해서 그 때만큼은 높이가 생겨서 bottom의 border도 height이후로 자리잡게 한다

```css
#toggle-list li.on, #toggle-list li.active {
    font-weight: 600;
    border-bottom: 2px solid var(--color-submain);
    color: var(--color-submain);

    height: var(--tab-height);
}
```

16. 크기에 따라 변해야하는 ul의 height + 버튼 width + 우측간격 + 글자크기는 root에 반응형으로 넣어주고 사용한다

```css
:root {
    --tab-height: 45px;
    --tab-margin-right: 25px;
    --tab-font-size: 1.1rem;
}

@media screen and (max-width: 776px) {
    :root {
        --tab-height: 35px;
        --tab-margin-right: 15px;
        --tab-font-size: 13px;
    }
}

.fs-tab {
    font-size: var(--tab-font-size);
}

#toggle-all, #toggle-list, #toggle-prev, #toggle-next {
    float: left;
    height: var(--tab-height);
}
```

17. 이제 양옆으로 가리는 효과를 #toggle-list 속 ul 형제로 양옆에 div.opacity.left .right를 생성해서 css로 준다.

- 공통인 클래스1개 (opacity) 좌/우 선택 클래스 1개씩으로 2개 클래스로 구성된다.

```html
<!-- scroll 공간-->
<div id="toggle-list" class="flex-grow-1 fs-tab border-start ps-2">
    <!-- 가리개 -->
    <div class="opacity left"></div>
    <ul>
        <li class="on">한의원 소개</li>
        <li>길찾기</li>
        <li>자가진단</li>
        <li>치료후기</li>
        <li>연구실적</li>
        <li>비급여진료비</li>
        <li>자주묻는 질문</li>
    </ul>
    <div class="opacity right"></div>
</div>
```

- 각각은 left:0, right:0으로 시작하는 absolute 아이템들이다.
- 그럴려면 부모인 ul은 relative여야, 자식 가리개들이 absolute로 덮을 수 있다

```css
    /* 가리개 */
#toggle-list {
    position: relative;
}

.opacity {
    opacity: .8;
}

.opacity.left {
    position: absolute;
    left: 0;
    top: 0;
    height: var(--tab-height);
    width: 20px;

    background: white;
}

.opacity.right {
    position: absolute;
    right: 0;
    top: 0;
    height: var(--tab-height);
    width: 20px;

    background: white;
}
```

![img.png](../ui/탭메뉴5.png)
