---
layout: page
title: 헤더 추가 문자열 사용
order: 1
devbox: true
devboxfile: HeaderSubtext_devbox.md
published: true
categories:
  - 헤더와 푸터
tags: ['header', 'subtext', '헤더', '서브텍스트', '추가 문자열']
---

RealGrid의 헤더에 text외에 부가적인 subText를 표시하는 방법을 설명하는 예제입니다.

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

  fieldSet="indicatorField"
  columnSet="headerSubtextColumn"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption_HeaderImage"
  styleSet="style1"

  dataSet="CustomOrders.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}
