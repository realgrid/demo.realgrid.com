---
layout: page
title: 컬럼 푸터
order: 6
devbox: true
devboxfile: ColumnFooter_devbox.md
published: true
categories:
  - 헤더와 푸터
tags: ['footer', 'summary', '합계', '푸터']
---

리얼그리드에서 컬럼별 합계를 구해서 표시하는 것은 간단한 일입니다. 컬럼 footer.**expression**에 통계값을 표시하는 expression을 지정하면 되는데, 그리드 **summaryMode**에 따라 expression에서 사용할 수 있는 값의 종류가 달라집니다. 그리드가 계산해서 제공하는 합계값이 정확하지 않거나 필요한 합산 식이 존재하지 않는 경우, 그리드 외부에서 계산한 그 값을 footer.**text** 속성으로 지정해서 표시하게 할 수 있습니다.
또, GridBase.**getSummary(field, summary)** 함수를 호출해서 필드의 합계값을 가져올 수도 있습니다. field는 필드명이나 필드인덱스가 될 수 있습니다. summary 지정할 수 있는 합계 목록은 아래 리스트에서 확인 하십시오.

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
  columnSet="columnFooterColumn"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption_ColumnFooter"
  styleSet="style1"

  dataSet="CustomOrders.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}
