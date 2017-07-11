---
layout: page
title: Excel - Column Group
order: 2
devbox: true
devboxfile: ExcelColumnGroup_devbox.md
published: true
categories:
  - 엑셀 내보내기
tags: ['excel', 'export', 'group']
---

컬럼 그룹핑된 구조대로 출력하거나, ExportOptions.linear 속성을 true로 지정하면 컬럼들을 선형으로 펼쳐서 출력할 수 있습니다. 기본값은 false입니다. 

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

  fieldSet="DefaultField"
  columnSet="ColumnGroupingColumn"
  dpOptionSet="DefaultDataProviderOption"
  gridOptionSet="DefaultGridOption"
  styleSet="style1"

  dataSet="CustomOrders.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}