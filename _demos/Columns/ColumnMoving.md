---
layout: page
title: 컬럼 이동
order: 6
devbox: true
devboxfile: ColumnMoving-devbox.md
published: true
categories:
  - 컬럼
tags: ['Moving', '이동']
---

그리드 [DisplayOptions](http://help.realgrid.com/api/types/DisplayOptions/){:target="_blank"}.columnMovable이 true이고, 컬럼의 movable이 true이면, 실행 시간에 사용자는 컬럼 헤더를 드래깅하여 컬럼의 위치를 변경할 수 있습니다. 또한, 컬럼의 displayIndex 속성을 이용해서 javascript 코드로 컬럼의 위치를 변경할 수 있습니다.

<script>
  var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
    gridView.setPanel({visible: false})
    dataProvider.setRows(data);
  }
  var onDoneDataSet = function() {
    
  }

  var onSuccessColumnSet = function(data, textStatus, jqXHR) {
    createColumnList(gridView);
  }  

</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="DefaultField"
  columnSet="ColumnGroupingColumn"
  dpOptionSet="DefaultDataProviderOption"
  gridOptionSet="DefaultGridOption"
  styleSet="style1"

  dataSet="CustomOrders.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  successColumnSet="onSuccessColumnSet"  

  gridWidth="100%"
  gridHeight="300px" 
%}