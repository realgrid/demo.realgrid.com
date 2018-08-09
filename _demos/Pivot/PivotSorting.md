---
layout: page
title: 피벗 정렬(Sorting)
order: 3
devbox: true
devboxfile: PivotSorting_devbox.md
published: true
categories:
  - 피벗(RealPivot)
tags: ['pivot', 'sort']
---

라벨값 또는 특정 조건의 값을 기준으로 피벗을 정렬할 수 있습니다.

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