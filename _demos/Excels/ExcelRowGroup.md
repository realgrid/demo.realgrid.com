---
layout: page
title: Excel - Row Group
order: 3
devbox: true
devboxfile: ExcelRowGroup_devbox.md
published: true
categories:
  - 엑셀 내보내기
tags: ['excel', 'export', 'group']
---

그리드가 Row 그룹핑된 상태일 때, ExportOptions.allItems 속성을 통해 감춰진 그룹 행들을 출력에서 제외 시키거나 포함시킬 수 있습니다.

<script>
var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
  dataProvider.setRows(data);
}
var onDoneDataSet = function() {
  gridView.setPanel({"visible": true});
  gridView.groupBy(["Country","CompanyName","OrderID"]);
}
</script>

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