---
layout: page
title: 피벗 정보 가져오기
ico: true
order: 21
devbox: true
devboxfile: PivotFields_devbox.md
published: true
categories:
  - 피벗(RealPivot)
tags: ['pivot', 'pivotFields', 'getPivotFields']
---

피벗 설정 정보를 한번에 가져올 수 있다.

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