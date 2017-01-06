---
layout: page
title: Export DocumentTitle
order: 8
devbox: true
devboxfile: ExportDocumentTitle_devbox.md
published: true
categories:
  - 엑셀 내보내기
tags: ['excel', 'title']
---

Excel Export시 *documentTitle*, *documentSubtitle*, *documentTail* 속성을 이용하여 Excel문서에 *제목*, *부제*, *꼬릿말*을 추가할 수 있습니다. 

<script>
var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
  dataProvider.setRows(data);
}
var onDoneDataSet = function() {

}
</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="excelExportFields"
  columnSet="excelExportColumns"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption1"
  styleSet="style1"

  dataSet="CustomOrders.json"
  successDataSet="onGridSuccessDataSet"  
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}