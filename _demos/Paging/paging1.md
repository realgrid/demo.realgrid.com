---
layout: page
title: 그리드에서 페이징 처리
order: 1
devbox: true
devboxfile: Paging1_devbox.md
published: true
categories:
  - 페이지 처리
tags: ['paging', '페이징']
---

[GridView.setPaging()](http://help.realgrid.com/api/GridView/setPaging/) 함수를 이용하여 그리드 자체적인 페이징 처리를 구현할 수 있습니다.  

> 이 구현 방법은 전체 페이지 데이터를 DataProvider에 불러온 다음 처리하게 되므로 네트웍 리소스를 절약하기 위한 방안으로의 페이지네이션(Pagination)을 구현하는 것과는 다르다는 사실에 주의해야 합니다.

<script>
  // var onSuccessDataSet = function(data, textStatus, jqXHR) {
  //   dataProvider.fillJsonData(data);
  // }
  //
  // var onDoneDataSet = function() {
  //
  // }
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

  showToolbox=true
  gridWidth="100%"
  gridHeight="300px" %}
