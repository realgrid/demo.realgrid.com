---
layout: page
title: 필터 적용 데이타 가져오기
order: 5
devbox: true
devboxfile: LoadFilter_devbox.md
published: true
categories:
  - 데이터 가져오기
tags: ['filldata']
---

[LocalDataProvider.setFilters()](http://help.realgrid.com/api/LocalDataProvider/setFilters/)함수는 `DataProvider`레벨의 필터링 기능을 제공합니다. 즉, 데이터를 로드하는 시점에 원하는 조건에 맞는 데이터를 걸러낼 수 있습니다.

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
