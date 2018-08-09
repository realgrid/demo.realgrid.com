---
layout: page
title: 피벗 컨텍스트 메뉴
order: 10
devbox: true
devboxfile: PivotContextMenu_devbox.md
published: true
categories:
  - 피벗(RealPivot)
tags: ['pivot', 'contextMenu']
---

피벗 왼쪽 상단의 메뉴 아이콘 클릭 시 contextMenu에 설정한 메뉴를 표시합니다.

<script>
var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
    dataProvider.setRows(data);
    pivot.drawView();
}
var onDoneDataSet = function() {

}

var onSuccessColumnSet = function(data, textStatus, jqXHR) {
}  

</script>

{% include realpivot.html

  pivotVar="pivot"
  dpVar="dataProvider"
  pivotId="realpivot"

  fieldSet="pivot_setFields"
  fieldMappingSet="pivot_fieldMapping"
  pivotFieldsSet="pivot_pivotFields"

  dataSet="pivotDataSet.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  pivotWidth="100%"
  pivotHeight="500px" %}