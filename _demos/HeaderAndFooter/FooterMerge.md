---
layout: page
title: 푸터 병합
order: 7
devbox: true
devboxfile: FooterMerge_devbox.md
published: true
categories:
  - 헤더와 푸터
tags: ['footer', 'merge', '푸터', '병합', '머지']
---
RowGroup.**footerCellMerge**를 true로 지정하면 그룹핑한 컬럼들의 RowGroup Cell을 하나로 병합하여 표시할 수 있습니다. 병합된 셀에 표시되는 값은 RowGroup의 그룹핑 컬럼을 기준으로 합니다.
Footer의 경우 병합할 컬럼들을 array형태로 지정하여 병합할 수 있습니다. 병합 셀이 하나일 때 1차원 배열, 병합 셀이 여러개일 때 2차원 배열로 지정합니다. 이 때 배열의 0번째 에 있는 컬럼의 footer내용이 병합된 셀의 표시됩니다.  
`multiFooter 사용 시 Footer 행끼리 병합은 할 수 없습니다.`

<script>
  var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
    dataProvider.setRows(data);
  }
  var onDoneDataSet = function() {
    gridView.groupBy(["Country", "CompanyName", "OrderID"]);
  }
</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="fieldset1"
  columnSet="footerMergeColumn"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption_ColumnFooter"
  styleSet="style1"

  dataSet="CustomOrders.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}
