#### 헤더 높이 변경   

- `headerHeight`: 헤더의 높이

<a class="btn primary small round lowercase" id="btnSetHeaderHeightUp">헤더 높이 늘리기</a>

```js
var headerHeight = gridView.getHeader().height  // 헤더 높이
gridView.setHeader(
  {height : headerHeight + 10} // 헤더 높이 +10
);

```

<a class="btn primary small round lowercase" id="btnSetHeaderHeightDown">헤더 높이 줄이기</a>

```js
var headerHeight = gridView.getHeader().height  // 헤더 높이
gridView.setHeader(
  {height : headerHeight - 10} // 헤더 높이 -10
);

```

#### 헤더의 높이 계산 방식 선택
컬럼이 수직으로 배치될 때 전체 헤더 높이를 수직으로 배치된 컬럼 수에 따라 자동으로 높이를 배분하는 방법과 각각의 컬럼의 높이를 고정하는 방법을 headerHeightFill 속성으로 선택 사용할 수 있습니다.

- `headerHeightFill`: 헤더의 높이 계산 방식을 지정하는 상수
- `default`: 헤더의 높이를 자동으로 계산한다.
- `fixed`: 헤더의 높이를 고정한다.

<a class="btn primary small round lowercase" id="btnSetHeaderHeightFillDefault">헤더 높이 자동으로 계산 합니다.</a>

```js
gridView.setHeader(
  {headerHeightFill : "default"}
);
```

<a class="btn primary small round lowercase" id="btnSetHeaderHeightFillFixed">헤더 높이를 고정합니다.</a>

```js
gridView.setHeader(
  {headerHeightFill : "fixed"}
);
```

<script>

  $('#btnSetHeaderHeightUp').click(function() {
    var headerHeight = gridView.getHeader().height;
    gridView.setHeader(
      {height : headerHeight + 10}
    )
  });

  $('#btnSetHeaderHeightDown').click(function() {
    var headerHeight = gridView.getHeader().height;
    gridView.setHeader(
      {height : headerHeight - 10}
    );
  });

  $('#btnSetHeaderHeightFillDefault').click(function() {
    gridView.setHeader(
      {headerHeightFill : "default"}
    );
  });

  $('#btnSetHeaderHeightFillFixed').click(function() {
    gridView.setHeader(
      {headerHeightFill : "fixed"}
    );
  });

</script>
