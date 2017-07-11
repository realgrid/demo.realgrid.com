---
layout: page
title: Excel - Merged Row Group
order: 5
devbox: true
devboxfile: ExcelMergedRowGroup_devbox.md
published: true
categories:
  - 엑셀 내보내기
tags: ['excel', 'export', 'mergedRowGroup', 'rowGroup', 'merge']
---

병합모드로 Row 그룹핑된셀들을 병합된 채로 출력하거나, ExportOptions.separateRows 속성을 true로 지정해서 풀려진 상태로도 출력할 수 있습니다.   
또, ExportOptions.allItems 속성을 false나 true로 지정해서 감춰진 행들을 출력하거나 제외시킬 수 있습니다.


<script>
var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
  dataProvider.setRows(data);
}
var onDoneDataSet = function() {
  gridView.setPanel({visible: true})
  gridView.setRowGroup({mergeMode:true, expandedAdornments: "footer", collapsedAdornments:"footer"})
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