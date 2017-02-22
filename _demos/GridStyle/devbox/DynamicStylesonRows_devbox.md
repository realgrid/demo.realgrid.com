#### 동적 행 스타일
셀 값에 따라 동적으로 셀에 스타일을 적용합니다.

- `dynamicStyles`: 동적 스타일을 적용할 조건과 표현식을 지정합니다.

<a class="btn primary small round lowercase" id="btnSetDynamicStyles">동적 행 스타일 변경</a>

```js
var newDynamicStyles = [{
    criteria: "row mod 2 <> 0",
    styles: "background=#D4F4FA"
}];

gridView.setStyles({
    body: {
        dynamicStyles: newDynamicStyles
    }
});
```

#### 동적 행 스타일
행 동적 스타일 적용 순서를 컬럼 배경으로 셀에 스타일을 적용합니다.

- `rowStylesFirst`: 행 동적 스타일 순서를 정합니다. 이 속성은 setOptions 에서 설정합니다.

<a class="btn primary small round lowercase" id="btnSetRowStylesFirst">행 동적 스타일 먼저 실행</a>
<a class="btn primary small round lowercase" id="btnSetRowStylesBack">행 동적 스타일 나중에 실행</a>

```js
gridView.setOptions({
    body: {
        rowStylesFirst: "true"
    }
});
```

<script>
  $('#btnSetDynamicStyles').click(function() {
    var newDynamicStyles = [{
        criteria: "row mod 2 <> 0",
        styles: "background=#D4F4FA"
    }];

    gridView.setStyles({
        body: {
            dynamicStyles: newDynamicStyles
        }
    });
  });

  $('#btnSetRowStylesFirst').click(function() {
    gridView.setOptions({
        body: {
            rowStylesFirst: true
        }
    });
  });

  $('#btnSetRowStylesBack').click(function() {
    gridView.setOptions({
        body: {
            rowStylesFirst: false
        }
    });
  });

</script>
