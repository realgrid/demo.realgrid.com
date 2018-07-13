---
layout: page
title: 피벗 필드 재설정
order: 5
devbox: true
devboxfile: PivotSetting_devbox.md
published: false
categories:
  - 피벗(RealPivot)
tags: ['pivot', 'setting']
---

Pivot의 columns, rows, values 값을 직접 설정해서 Pivot 화면을 구성할 수 있습니다.

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