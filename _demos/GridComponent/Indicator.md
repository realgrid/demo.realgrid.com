---
layout: page
title: 인디케이터
order: 1
devbox: true
devboxfile: indicator-devbox.md
published: true
categories:
  - 그리드 구성요소
tags: ['indicator', 'item', 'number', '행번호']
---

[인디케이터(Indicator)](http://help.realgrid.com/api/types/Indicator/)는 그리드의 가장 왼쪽에 위치한 수직 영역으로 데이터의 행 번호등을 표시하기 위한 용도로 사용 할 수 있습니다.

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

  fieldSet="indicatorField"
  columnSet="indicatorColumn"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption_indicator"
  styleSet="style1"

  dataSet="CustomOrders.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}