---
layout: page
title: 바 렌더러
order: 3
devbox: true
devboxfile: BarCellRenderer_devbox.md
published: true
categories:
  - 렌더러
tags: ['렌더러', 'renderer', 'bar']
---

BarCellRenderer는 숫자형 컬럼 셀의 값을 막대 상자로 표시합니다.   
BarCellRenderer가 설정된 컬럼을 정렬 시키면 막대 상자가 Gradient로 표시된 걸 확인할 수 있습니다.

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
  columnSet="barCellRendererColumns"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption1"
  styleSet="style1"

  dataSet="CustomOrders.json"
  successDataSet="onGridSuccessDataSet"  
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}