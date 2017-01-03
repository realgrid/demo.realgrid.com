---
layout: page
title: 행 그룹핑
order: 1
devbox: true
devboxfile: RowGrouping-devbox.md
published: true
categories:
  - 행 그룹
tags: ['grouping', '그룹']
---

Row grouping은 데이터 행들을 하나 이상의 지정한 컬럼의 값을 기준으로 구분시켜 계층적인 구조로 표시합니다. 컬럼 헤더를 panel 영역으로 드래깅하면 그 컬럼으로 grouping 합니다. 또는 GridView.groupBy() 함수를 호출해서 grouping할 수도 있습니다.

<script>
var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
  dataProvider.setRows(data);
}
var onDoneDataSet = function() {
  gridView.setPanel({"visible": true})
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