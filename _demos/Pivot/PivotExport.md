---
layout: page
title: 피벗 엑셀 내보내기
ico: true
order: 19
devbox: true
devboxfile: PivotExport_devbox.md
published: true
categories:
  - 피벗(RealPivot)
tags: ['pivot', 'export']
---

현재 피벗에 표시된 구조대로 데이터셋을 엑셀 파일로 변환해서 로컬파일로 저장하거나 서버로 업로드합니다.

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