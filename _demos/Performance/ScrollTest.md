---
layout: page
title: 스크롤 성능 테스트
order: 1
published: true
categories:
  - 성능
tags: ['성능', 'performance', '스크롤', 'scroll']
---

RealGrid의 랜더링 성능은 그리드에 그려야할 대상이 얼마나 많은 가에 따라 다릅니다.
그리드는 셀들의 집합으로 셀 하나 하나를 개별적으로 랜더링 하게 되며, 따라서 셀들이 많을 수록 랜더링 성능이 나빠집니다. 보이는 그리드 영역에 그려야할 셀의 갯수는 화면에 보이는 컬럼과 행의 갯수로 결정됩니다. 따라서 보이는 컬럼의 갯수, 행의 갯수를 조절해 랜더링 속도를 개선할 수 있습니다.

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

  fieldSet="carFieldset"
  columnSet="carColumn"
  dpOptionSet="dataProviderOption1"  
  styleSet="style1"

  dataSet="carData1.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="600px" %}
