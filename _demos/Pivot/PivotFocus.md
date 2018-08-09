---
layout: page
title: 피벗 포커스
order: 14
devbox: true
devboxfile: PivotFocus_devbox.md
published: true
categories:
  - 피벗(RealPivot)
tags: ['pivot', '포커스', 'focus']
---

pivot 화면에 포커스를 setDisplayOpyions() 함수의 showFocus 속성으로 설정할 수 있습니다.

<script>
var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
    pivot.onCurrentChanged = function (pivot, index) {
        console.log(index); 
    }
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