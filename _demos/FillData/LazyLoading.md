---
layout: page
title: 그리드 Lazy Loading 구현
order: 8
devbox: true
devboxfile: LazyLoading_devbox.md
published: true
categories:
  - 데이터 가져오기
tags: ['filldata', 'lazy']
---


그리드에서 Lazy Loading은 맨 마지막 행까지 스크롤 되었을때 그 다음 데이터를 읽어 오는 방식으로 구현 할 수 있습니다. RealGrid에서 이런 동작을 구현 할 수 있도록 스크롤 관련 콜백 함수를 제공하고 있습니다.

<script>
  var onSuccessDataSet = function(data, textStatus, jqXHR) {
    dataProvider.fillJsonData(data,
      {count: 100});
  }

  var onDoneDataSet = function() {

  }
</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="carFields2"
  columnSet="carColumns2"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption1"
  styleSet="style1"
  dataSet="carData2.json"
  successDataSet="onSuccessDataSet"

  showToolbox=true
  gridWidth="100%"
  gridHeight="300px" %}
