---
layout: page
title: 피벗 셀값 확인
ico: true
order: 20
devbox: true
devboxfile: PivotCellValue_devbox.md
published: true
categories:
  - 피벗(RealPivot)
tags: ['pivot', 'value', 'getCellValue']
---

포커스가 위치한 셀이 어떤 데이터행으로 이루어진 값인지 확인한다.

<script>
var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
    dataProvider.setRows(data);
    pivot.setDisplayOptions({showFocus:true});
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