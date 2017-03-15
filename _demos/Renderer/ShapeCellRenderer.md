---
layout: page
title: 도형 렌더러
order: 6
devbox: true
devboxfile: ShapeCellRenderer_devbox.md
published: true
categories:
  - 렌더러
tags: ['렌더러', 'renderer']
---

Shape 셀 렌더러는 그리드에 포함되어 있는 몇 개의 shape 아이콘 중 하나를 텍스트와 같이 표시합니다.

<script>
var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
  dataProvider.setRows(data);
}
var onDoneDataSet = function() {
  gridView.setColumnProperty("OrderID", "renderer", {type:"shape"});

  gridView.setColumnProperty("OrderID", "styles", {
      figureBackground: "#ff008800",
      figureName: "ellipse",
      iconLocation: "right",
      paddingRight: 6
  });
}
</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="shapeCellRendererFields"
  columnSet="shapeCellRendererColumns"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption1"
  styleSet="style1"

  dataSet="CustomOrders.json"
  successDataSet="onGridSuccessDataSet"  
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}