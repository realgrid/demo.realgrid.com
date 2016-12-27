---
layout: page
title: 헤더 체크박스 사용
order: 1
devbox: true
devboxfile: HeaderCheckbox_devbox.md
published: true
categories:
  - 헤더와 푸터
tags: ['Header checkbox', 'Header', 'checkbox', '체크박스']
---

RealGrid의 컬럼 헤더에 체크박스를 구현하는 방법을 설명하는 페이지 입니다.

Column.checked속성을 true로 설정하면 체크박스가 표시됩니다. 기본값은 false입니다.
ColumnHeader.checkLocation속성은 체크박스가 표시될 위치을 지정할 수 있습니다. 기본값은 "none"입니다. 자세한 내용은 help사이트의 ColumnHeaderItemLocation 페이지를 참고하시기 바랍니다.
헤더의 체크가 변경되면 onColumnCheckedChanged(grid, column, checked) 콜백함수가 호출됩니다.

<script>
  var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
    dataProvider.setRows(data);
  }
  var onDoneDataSet = function() {

  }
</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="HeaderHeightField"
  columnSet="headerCheckboxColumn"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption_HeaderHeight"
  styleSet="style1"

  dataSet="CustomOrders.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}
