---
layout: page
title: 링크 렌더러
order: 8
devbox: true
devboxfile: LinkCellRenderer_devbox.md
published: true
categories:
  - 렌더러
tags: ['렌더러', 'renderer']
---

Link 셀 렌더러는 컬럼에 Hyperlink형태로 표현하고 클릭할 때 다른 페이지를 띄우거나 팝업처리 등을 구현할 수 있습니다.

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

  fieldSet="rendererFields"
  columnSet="linkCellRendererColumns"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption1"
  styleSet="style1"

  dataSet="CustomOrders.json"
  successDataSet="onGridSuccessDataSet"  
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}