---
layout: page
title: Excel - MultiExport
order: 12
devbox: true
devboxfile: ExcelMultiExport_devbox.md
published: true
categories:
  - 엑셀 내보내기
tags: ['excel', 'export', 'group']
---

다중 그리드 사용 시 하나의 엑셀파일에 각 시트별로 그리드를 export 해서 하나의 excel파일에 여러개의 그리드를 내려받을 수 있습니다.

<script>
var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
  dataProvider.setRows(data);
  dataProvider2.setRows(data);
}
var onDoneDataSet = function() {
}
</script>


<h4>Grid1</h4>
{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="rowGroupingField"
  columnSet="rowGroupingColumn"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption1"
  styleSet="style1"

  dataSet="CustomOrders.json"
  successDataSet="onGridSuccessDataSet"  
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}


<h4>Grid2</h4>
{% include realgrid.html

  gridVar="gridView2"
  dpVar="dataProvider2"
  gridId="realgrid2"

  fieldSet="cellMergingField"
  columnSet="cellMergingColumn"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption1"
  styleSet="style1"

  dataSet="griddata1.json"
  successDataSet="onGridSuccessDataSet"

  gridWidth="100%"
  gridHeight="300px" %}