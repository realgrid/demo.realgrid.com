---
layout: page
title: 바코드 렌더러
order: 9
devbox: true
devboxfile: BarcodeCellRenderer_devbox.md
published: true
categories: 
  - 렌더러
tags: ['렌더러', 'renderer']
---

Barcode 셀 렌더러를 이용해서 데이터를 표시할 수 있습니다.   

<script>
var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
	dataProvider.setRows(data);
}
var onDoneDataSet = function() {
	gridView.setDisplayOptions({rowHeight:50})
}
</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="rendererFields"
  columnSet="barcodeCellRendererColumns"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption1"
  styleSet="style1"

  dataSet="CustomOrders.json"
  successDataSet="onGridSuccessDataSet"  
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}