---
layout: page
title: 피벗 필터링(Filtering)
order: 4
devbox: true
devboxfile: PivotFiltering_devbox.md
published: true
categories:
  - 피벗(RealPivot)
tags: ['pivot', 'filter']
---

원본데이터에서 조건을 만족하는 데이터만 피벗으로 구성할 수 잇습니다.

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