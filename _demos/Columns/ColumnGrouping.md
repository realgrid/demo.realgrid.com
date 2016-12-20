---
layout: page
title: 컬럼 그룹핑
order: 3
devbox: true
devboxfile: ColumnGrouping-devbox.md
published: true
categories:
  - 컬럼
tags: ['Grouping']
---

그리드에 표시하는 데이터셋이 주로 테이블 형태의 2차원 배열 모델이지만 실제로는 다양한 포맷의 리포팅이 요구되고 있습니다. 리얼그리드는 컬럼 그룹핑을 통해 복잡하고 다양한 레이아웃을 표현할 수 있도록 합니다. 아래 예제에서 녹색조로 표시된 것들이 컬럼그룹 입니다.  

컬럼 그룹은 데이터컬럼 및 하위 컬럼그룹을 포함하는 컬럼으로 자식 컬럼들을 수평 혹은 수직으로 배열합니다. 하위 컬럼그룹은 부모 컬럼그룹과 다른 방향으로 자신의 자식 컬럼들을 배열할 수 있습니다. 컬럼 그룹은 헤더에는 표시되거나 표시되지 않을 수 있지만, 데이터 행에는 표시되지 않습니다. 또한, 컬럼그룹은 자식들의 헤더를 그룹의 hideChildHeaders 속성으로 감출 수 있습니다.

<script>
  var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
    dataProvider.setRows(data);
  }
  var onDoneDataSet = function() {
  	gridView.setStyles({
        header: {
            group: {
                background: "linear,#ffe9f0f8,#ffc3f8d8,90",
                foreground: "#ff666666"
            }
        }
    });	
    
  }

  var onSuccessColumnSet = function(data, textStatus, jqXHR) {
	createGroupList(gridView);
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
  gridHeight="300px" %}