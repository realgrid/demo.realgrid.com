---
layout: page
title: 컬럼 너비 자동 조정
order: 8
devbox: true
devboxfile: GridFitting-devbox.md
published: true
categories:
  - 컬럼
tags: ['Fitting']
---

RealGrid는 최상위 컬럼 셋 전체를 그리드의 너비에 채워서 맞추는 몇가지 방식을 제공하고 있습니다.
DevBox에서 기능을 확인해보세요.


<script>
  var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
    gridView.setPanel({visible: false})
    dataProvider.setRows(data);
  }
  var onDoneDataSet = function() {
    
  }


</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="DefaultField"
  columnSet="GridFittingColumn"
  dpOptionSet="DefaultDataProviderOption"
  gridOptionSet="DefaultGridOption"
  styleSet="style1"

  dataSet="CustomOrders.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" 
%}

