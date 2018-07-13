---
layout: page
title: 피벗 숫자포맷
order: 14
devbox: true
devboxfile: PivotNumberFormat_devbox.md
published: true
categories:
  - 피벗(RealPivot)
tags: ['pivot', 'numberFormat']
---

numberFormat 기능을 사용해서 pivot에 표시될 데이터를 정수, 소수 형태로 설정할 수 있습니다.

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