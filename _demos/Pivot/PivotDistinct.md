---
layout: page
title: 피벗 고유값(distinct)
order: 11
devbox: true
devboxfile: PivotDistinct_devbox.md
published: true
categories:
  - 피벗(RealPivot)
tags: ['pivot', '고유', 'distinct']
---

피벗에 표시되는 값의 유형을 고유의 값으로 표시할 수 있습니다.

<script>
var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
    pivot.setSummaryOptions({
        columnVisible:false,
        rowVisible: false,
        columnGroupVisible: false,
        rowGroupVisible: false
    })

    pivot.setDisplayOptions({columnHeight:40,rowHeight:40,columnWidth:60,blankFillValue:null,virtualRendering:true})

    dataProvider.fillJsonData(data);
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

  fieldSet="pivotDistinct_setFields"
  fieldMappingSet="pivotDistinct_fieldMapping"
  pivotFieldsSet="pivotDistinct_pivotFields"

  dataSet="pivotCarData.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  pivotWidth="100%"
  pivotHeight="500px" %}