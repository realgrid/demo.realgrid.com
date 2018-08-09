---
layout: page
title: 피벗 날짜 타입
order: 6
devbox: true
devboxfile: PivotDatetime_devbox.md
published: true
categories:
  - 피벗(RealPivot)
tags: ['pivot', 'datetime', '날짜']
---

피벗에서는 하나의 날짜 필드를 년도,반기,분기,월,년주차,월주차,일,시 로 각각 구성할 수 있습니다.

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