---
layout: page
title: 행 병합 그룹핑
order: 3
devbox: true
devboxfile: MergedRowGrouping-devbox.md
published: true
categories:
  - 행 그룹
tags: ['grouping', 'merge', '병합']
---

그리드 rowGroup.merged 속성을 true로 설정하면, 행 Grouping 시 묶여진 컬럼 셀들을 병합셀로 표시합니다. 

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
  columnSet="mergedRowGroupingColumn"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption1"
  styleSet="style1"

  dataSet="CustomOrders.json"
  successDataSet="onGridSuccessDataSet"  
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}