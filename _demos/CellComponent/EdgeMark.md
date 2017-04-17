---
layout: page
title: 엣지마크
order: 9
devbox: true
devboxfile: EdgeMark-devbox.md
published: true
categories:
  - 셀 구성요소
tags: ['edgemark', '엣지마크', '삼각형', '에지마크']
---

셀의 모서리에 삼각형을 표시할 수 있습니다. 4개의 모서리 중 하나의 위치에 표시할 수 있으며, 중요 표시나 별도의 정보가 있다는 강조 용도 등으로 사용할 수 있습니다.   

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

  fieldSet="DefaultField"
  columnSet="EdgeMarkColumn"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption_stateBar"
  styleSet="style1"

  dataSet="DefaultDataSet.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}