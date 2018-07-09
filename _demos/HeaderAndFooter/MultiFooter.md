---
layout: page
title: 멀티 푸터
order: 8
devbox: true
devboxfile: MultiFooter_devbox.md
published: true
categories:
  - 헤더와 푸터
tags: ['footer', 'summary', '합계', '푸터', '멀티푸터', '여러줄', 'multi footer']
---

때때로 업무 화면 구성시 푸터를 여러 줄로 표시하길 원하는 경우가 있습니다. 이 경우 RealGridJS 1.1.21 버전부터 Footer를 여러 줄로 표시할수 있도록 [footer](http://help.realgrid.com/api/types/Footer/).**count** 속성을 지원하고 있습니다. 이 속성에 표시할 푸터의 라인 수를 지정하면 됩니다.  
Footer를 여러 줄로 표시하는 경우에 수식과 문자열은 Column.Footer.Expression, Column.Footer.Text를 배열로 지정로 지정합니다.  
`multiFooter 사용 시 Footer 행끼리 병합은 할 수 없습니다.`

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
  columnSet="MultiFooterColumn"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption_MultiFooter"
  styleSet="style1"

  dataSet="CustomOrders.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}
