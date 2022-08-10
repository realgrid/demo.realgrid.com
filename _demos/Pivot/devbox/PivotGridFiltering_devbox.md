#### 피벗 데이터 디테일 그리드

피벗 더블클릭 이벤트에서 그리드의 필터 기능을 동적으로 적용시킵니다.

```
pivot.onDblClick = function (pivot, type, index) {
    var colNames = gridView.getColumnNames()

    for(var j = 0; j < colNames.length; j++){
        gridView.clearColumnFilters(colNames[j])
    }

    //rowLabel 값 필터링
    for(var i = 0; i < Object.keys(index.rows).length; i++){
        if(Object.keys(index.rows)[i] !== "__sum"){
            var filters = [{
                name: Object.keys(index.rows)[i],
                criteria: "value = '" + index.rows[Object.keys(index.rows)[i]] + "'",
                active:true
            }];

            gridView.setColumnFilters(Object.keys(index.rows)[i], filters);
        }else{
        }
    }
}
```