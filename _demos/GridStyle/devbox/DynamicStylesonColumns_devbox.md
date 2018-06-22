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

#### 편집된 셀 동적 스타일
값이 수정된 셀에 해당 스타일을 적용합니다.  
changedcell조건을 사용하기 위해서는 DataProvider.restoreMode속성이 “explicit”이거나 또는 “auto”이어야 합니다.

버튼 클릭 시 상태가 none 인 행의 값 수정 시 해당 셀의 leftTop렌더러를 표시합니다.

<a class="btn primary small round lowercase" id="btnChangedcell">편집 셀 스타일</a>

```js
dataProvider.setOptions({restoreMode:"explicit"});
gridView.setStyles({
    body:{
        cellDynamicStyles:[{criteria:"changedcell", styles:{figureName:"leftTop", figureBackground:"#FF00ebeb", figureSize:"30%"}}]
    }
});
```

컬럼별로 스타일을 적용하는 경우에는 column.dynamicStyles를 사용합니다.
```js
gridView.setColumnProperty("columnName", "dynamicStyles", [{
    criteria:"changedcell", 
    styles:{
        figureName:"leftTop", 
        figureBackground:"#FF00ebeb", 
        figureSize:"20%"
    }
}]);
```

#### 동적 스타일 함수로 지정

`1997`컬럼에 동적 스타일을 함수형태로 지정합니다.

<a class="btn primary small round lowercase" id="btnSetColumnDynamicFunctionStyles">동적 컬럼 스타일 변경</a>

```js
gridView.setColumnProperty("1997","dynamicStyles",function(grid, index, value) {
    if (value > 1000) {
        return {foreground:"#FFFF0000"}
    }
})
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

  $('#btnChangedcell').click(function() {
    dataProvider.setOptions({restoreMode:"explicit"});
    gridView.setStyles({
        body:{
            cellDynamicStyles:[{criteria:"changedcell", styles:{figureName:"leftTop", figureBackground:"#FF00ebeb", figureSize:"30%"}}]
        }
    });
  });

  $('#btnSetColumnDynamicFunctionStyles').click(function() {
    gridView.setColumnProperty("1997","dynamicStyles",function(grid, index, value) {
        if (value > 1000) {
            return {foreground:"#FFFF0000"}
        }
    })
  });
</script>
