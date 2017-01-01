---
layout: page
title: Scroll Test 2
order: 2
published: true
categories:
  - 성능
tags: ['성능', 'performance', '스크롤', 'scroll']
---

동적 스타일이 적용된 상태에서 상하, 좌우 스크롤에 따른 그리드 성능을 테스트 합니다.

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

  fieldSet="scrollTestField"
  columnSet="scrollTestColumn"
  dpOptionSet="dataProviderOption1"  
  styleSet="style1"

  dataSet="celloData.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="600px" %}
