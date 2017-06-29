---
layout: page
title: 선택
order: 9
devbox: true
devboxfile: selecting-devbox.md
published: true
categories:
  - 그리드 구성요소
tags: ['Selecting', '선택', '영역선택', '선택영역']
---

[SelectOptions](http://help.realgrid.com/api/types/SelectOptions/)을 사용하여 그리드의 영역 선택을 다양한 방법으로 지정할 수 있습니다.  

<script>
  var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
    dataProvider.setRows(data);
  }
  var onDoneDataSet = function() {
    gridView.setDisplayOptions({
      rowHoverMask:{
        visible:true,
        styles:{
          background:"#2065686b"
        },
        hoverMask:"cell"
      }
    });
  }
</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="DefaultField"
  columnSet="selectingColumn"
  dpOptionSet="DefaultDataProviderOption"
  gridOptionSet="DefaultGridOption"
  styleSet="style1"
 
 
  dataSet="DefaultDataSet.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %} 
