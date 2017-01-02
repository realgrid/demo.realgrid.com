---
layout: page
title: 컬럼 높이
order: 5
devbox: true
devboxfile: ColumnHeight-devbox.md
published: true
categories:
  - 컬럼
tags: ['Height', '높이', '컬럼높이']
---

RealGrid는 컬럼 grouping을 통해 복잡한 layout을 표현할 수 있습니다. 이 때 컬럼그룹에 속한 각 셀의 높이는 전체적으로 계산된 행의 높이에 따라 균등하게 배분되지만, fillHeight 속성으로 수직으로 배열되는 컬럼 그룹 내에서 각 컬럼의 높이를 다르게 할 수 있습니다.  

height(기본값 0 - 기본 행 높이)나 minHeight로 지정된 값들로 지정된 고정 높이들을 모두 합한 후에도 컬럼 그룹의 높이에 여분이 생기면 fillHeigth 값에 따라 비율적으로 배분하여 높이를 계산합니다.   

아래 예제 그리드에서 배경색이 흰색이 아닌 컬럼들이 fillHeight 속성을 가지고 있습니다. 첫번째 행의 인디케이터 셀 아래 부분을 드래깅해서 행의 높이를 변경해보면 속성의 역할을 알 수 있습니다.

<script>
  var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
    dataProvider.setRows(data);
  }
  var onDoneDataSet = function() {
    gridView.setDisplayOptions({
      heightMeasurer: "fixed",
      rowResizable: true,
      rowHeight: 80
    });    
  }

</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="DefaultField"
  columnSet="ColumnHeightColumn"
  dpOptionSet="DefaultDataProviderOption"
  gridOptionSet="DefaultGridOption"
  styleSet="style1"

  dataSet="CustomOrders.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" 
%}
