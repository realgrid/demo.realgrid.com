---
layout: page
title: 아이템 모델
order: 5
devbox: true
devboxfile: ItemModelApi-devbox.md
published: true
categories:
  - 행 그룹
tags: ['item', '모델', 'model']
---

그리드 아이템(Item)은 DataProvider의 한 행이나, RowGrouping된 그룹의 헤더나 푸터 등이 그리드나 트리에서 한 라인으로 표시되는 표시 모델입니다.

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
  dpOptionSet="dataProviderOption1"
  gridOptionSet="DefaultGridOption"
  styleSet="style1"

  dataSet="DefaultDataSet.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}