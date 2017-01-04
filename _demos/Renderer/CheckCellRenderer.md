---
layout: page
title: 체크 렌더러
order: 2
devbox: true
devboxfile: CheckCellRenderer_devbox.md
published: true
categories:
  - 렌더러
tags: ['렌더러', 'renderer']
---

Check 셀 렌더러는 셀의 값을 true/false 두 가지 상태로 표시하는 렌더러입니다. 

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

  fieldSet="checkCellRendererFields"
  columnSet="checkCellRendererColumns"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption1"
  styleSet="style1"

  dataSet="CustomOrders.json"
  successDataSet="onGridSuccessDataSet"  
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}