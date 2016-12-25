---
layout: page
title: 빈 행 채우기
order: 7
devbox: true
devboxfile: SetRowCount_devbox.md
published: true
categories:
  - 데이터 가져오기
tags: ['filldata', 'setRowCount']
---

[LocalDataProvider.setRowCount()](http://help.realgrid.com/api/LocalDataProvider/setRowCount/) 함수를 이용하여 DataProvider에 행의 갯수를 지정하고 그 갯수 만큼 비어있는 데이터를 채울수 있습니다.

<script>
  var onSuccessDataSet = function(data, textStatus, jqXHR) {
    dataProvider.fillJsonData(data,
      {count: 5});
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
  dataSet="cardata2.json"
  successDataSet="onSuccessDataSet"

  showToolbox=true
  gridWidth="100%"
  gridHeight="300px" %}
