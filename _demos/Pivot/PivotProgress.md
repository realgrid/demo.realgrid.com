---
layout: page
title: 피벗 프로그레스바
order: 9
devbox: true
devboxfile: PivotProgress_devbox.md
published: false
categories:
  - 피벗(RealPivot)
tags: ['pivot', 'progress']
---

피벗 데이터 로드 시 프로그레드바를 표시합니다.

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

  fieldSet="pivotContextMenu_setFields"
  fieldMappingSet="pivotContextMenu_fieldMapping"
  pivotFieldsSet="pivotContextMenu_pivotFields"

  dataSet="pivotDataSet.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  pivotWidth="100%"
  pivotHeight="500px" %}