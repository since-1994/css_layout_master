# css_layout_master

### [grid의 justify-items, align-items]()

### auto columns and rows

```css
.grid {
  display: grid;
  grid-template-columns: repeat(4, 100px);
  grid-template-rows: repeat(4, 100px);
}
```

위의 상황에서 셀이 16개를 넘어간다면 row의 높이가 17개부터는 작아질 것이다. 예상 못한 높이를 지정해주고 싶으면 `grid-auto-rows : 100px`를 추가해주면 16개를 넘어가도 높이는 100px을 유지한다.

```css
.grid {
  display: grid;
  grid-template-columns: repeat(4, 100px);
  grid-template-rows: repeat(4, 100px);
  grid-auto-flow: column;
}
```

grid-auto-flow는 진행방향을 바꾼다. 아래 이미지를 보자.
<img src ="./readImg/img2.png">

### minmax

minmax는 1fr과 사용하면 유용하다. 아래 코드를 보자

```css
.grid {
  display: grid;
  grid-template-columns: repeat(4, minmax(100px, 1fr));
  grid-template-rows: repeat(4, 100px);
}
```

위와 같이 코드를 작성하면 1fr이 100px 보다 작으면 100px로 1fr이 100px보다 크면 1fr로 유지된다.

### auto-fit, auto-fill

auto-fit과 auto-fill은 repeat과 함께 사용되는 것으로 아래 코드와 그 결과를 보자.

```css
.grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(100px, 1fr));
  grid-template-rows: repeat(4, 100px);
}

.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
  grid-template-rows: repeat(4, 100px);
}
```

<img src = "./readImg/img1.png">

- auto-fill은 최대 그리드 수를 목표로 한다. (그러기 위해서 각 셀 너비가 최소로 되겠죠?)
- auto-fit은 최대 셀 너비를 목표로 한다.

### min-content, max-content

```css
.grid {
  display: grid;
  grid-template-columns: min-content max-content;
  grid-auto-rows: 100px;
}
```

min-content, max-content는 px, fr 과 같은 단위와 다르게 셀이 포함한 content에 따라 변한다. max-content는 content에 맞게 최대로 늘어나고 min-content는 content를 최소로 잘라 맞춘다. 아래의 예시가 적절하다.

<img src="./readImg/img3.png" width="400">
