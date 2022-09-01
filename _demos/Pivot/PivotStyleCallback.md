---
layout: page
title: 피벗 동적스타일
ico: true
order: 19
devbox: true
devboxfile: PivotStyleCallback_devbox.md
published: true
categories:
  - 피벗(RealPivot)
tags: ['pivot', 'style', 'callback', 'styleCallback']
---

styleCallback 속성으로 피벗 셀에 동적 className을 추가합니다.

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