---
layout: page
title: 토스트 메시지 창
order: 5
devbox: true
devboxfile: toastView-devbox.md
published: true
categories:
  - 그리드 구성요소
tags: ['ToastView', '토스트뷰']
---

대량 데이터셋의 정렬/필터링/그룹핑은 수 초 이상이 요구될 수 있습니다. 정렬/필터링/그룹핑의 진행 상태를 표시해 주는 것이 최선이지만, 리얼그리드는 아직 그렇게 구현되지 못하고 있습니다. 그 대안으로 정렬/필터링/그룹핑이 진행될 것이라는 메시지를 먼저 표시해주는 Toast View를 제공합니다.   
Toast View는 특별히 느리지 않다고 여겨지는 상태라면 표시하지 않도록 해야 합니다.  
짧은 시간에 수행되는 경우라면 Toast View를 표시하는 것이 오히려 사용자에게 방해가 될 수도 있습니다.

<script>
  var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
    dataProvider.fillJsonData(data, {});
  }
  var onDoneDataSet = function() {
	gridView.setStyles({
        header: { "fontSize": "12", "fontFamily": "맑은 고딕", "fontBold": "true" },
        selection: {
            background: "#11000000",
            border: "#88000000,1"
        }
    });
    
  }
</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="toastViewField"
  columnSet="toastViewColumn"
  dpOptionSet="DefaultDataProviderOption"
  gridOptionSet="DefaultGridOption"
  styleSet="style1"

  dataSet="LargeDataSet.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}