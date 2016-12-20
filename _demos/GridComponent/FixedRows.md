---
layout: page
title: 행 고정하기
order: 8
devbox: true
devboxfile: fixedRow-devbox.md
published: true
categories:
  - 그리드 구성요소
tags: ['FixedRows', '행고정']
---

[FixedOptions](http://help.realgrid.com/api/types/FixedOptions/)를 설정하여 그리드 최상위 행 중 하나 이상의 행을 스크롤에서 제외시킬 수 있습니다. 기본적으로 고정 행은 정렬, 필터링에서 제외됩니다.  

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
  columnSet="DefaultColumn"
  dpOptionSet="DefaultDataProviderOption"
  gridOptionSet="DefaultGridOption"
  styleSet="style1"

  dataSet="DefaultDataSet.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}
