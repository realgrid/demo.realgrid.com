---
layout: page
title: 컬럼 만들기
codebox: true
codefile: SetColumns.md
categories: columns
---

그리드 fiteringOptions.enabled 가 true이고, 컬럼에 filter들이 설정되면 컬럼 헤더에 필터 핸들이 표시되고, 사용자는 그 핸들을 클릭해서 표시되는 필터 리스트를 이용 컬럼 별로 데이터를 필터링할 수 있습니다. 한 컬럼 내에서 복수 필터가 선택되면 필터셋 중 하나의 필터 조건에만 해당되어도 행들이 표시됩니다. 하지만 여러 컬럼에 필터가 설정되면 모든 컬럼의 필터셋에 해당되는 행들만이 표시됩니다.
아래는 "CustmerID" 필드에 대한 컬럼 필터 적용 예제입니다.
RealGridJS 1.1.18 버전부터 datetime 필드에 필터를 적용할 수 있습니다.
더보기 버튼을 눌러 기능을 확인하세요.

```js
var column = grid.columnByName("CustomerId");
if (column) {
    var filters = [{
        name: "VINET",
        criteria: "value = 'VINET'"
    }, {
        name: "VICTE",
        criteria: "value = 'VICTE'"
    }, {
    ...
    ];

    column.filters = filters;
    grid.setColumn(column);
};
```

```js
var columns = [
// column1
{
    name : "column1",
    fieldName : "Field1",
    header : {
        text : "컬럼 1"
    },
    footer : {
    },
    styles : {
    },
    width : 150
},
// column 2
{
},
...
];
this.set();
grid.setColumns(columns);
```
