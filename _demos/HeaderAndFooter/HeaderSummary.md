---
layout: page
title: 상단 합계 표시
order: 5
devbox: true
devboxfile: HeaderSummary_devbox.md
published: true
categories:
  - 헤더와 푸터
tags: ['header', 'summary', '합계']
---

그리드의 끝에 위치한 footer와 함께 각 컬럼의 합계 및 통계에 대한 값을 그리드 시작 위치에 표시 합니다.  **header.summary.visible** 속성값을 true로 설정하면 footer와 같은 기능을 가진 bar가 시작 위치에 표시되는 것을 확인 할 수 있습니다.

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

  fieldSet="fieldset1"
  columnSet="headerSummaryColumn"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption_HeaderSummary"
  styleSet="style1"

  dataSet="CustomOrders.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}
