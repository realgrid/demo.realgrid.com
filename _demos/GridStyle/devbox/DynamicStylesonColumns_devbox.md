#### 동적 컬럼 스타일
셀 값에 따라 동적으로 셀에 스타일을 적용합니다.

- `cellDynamicStyles`: 동적 스타일을 지정합니다.

<a class="btn primary small round lowercase" id="btnSetDynamicStyles">동적 컬럼 스타일 변경</a>

```js
var newDynamicStyles = [{
    criteria: "value >= 1000",
    styles: "background=#FF0000"
}];

gridView.setStyles({
    body: {
        cellDynamicStyles: newDynamicStyles
    }
});
```

`1997`컬럼에 동적 스타일을 지정합니다.

<a class="btn primary small round lowercase" id="btnSetColumnDynamicStyles">동적 컬럼 스타일 변경</a>

```js
gridView.setColumnProperty(
    gridView.columnByField("1997"),
    "dynamicStyles", [{
        criteria: "(value >= 500) and (value < 1000)",
        styles: "background=#FF0000"
    }]
)
```

<script>
  $('#btnSetDynamicStyles').click(function() {
    var newDynamicStyles = [{
        criteria: "value >= 1000",
        styles: "background=#FF0000"
    }];

    gridView.setStyles({
        body: {
            cellDynamicStyles: newDynamicStyles
        }
    });
  });

  $('#btnSetColumnDynamicStyles').click(function() {
    gridView.setColumnProperty(
        gridView.columnByField("1997"),
        "dynamicStyles", [{
            criteria: "(value >= 500) and (value < 1000)",
            styles: "background=#FF0000"
        }]
    );
  });
</script>
