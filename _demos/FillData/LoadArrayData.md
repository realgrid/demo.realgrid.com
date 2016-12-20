---
layout: page
title: Array 데이타 가져오기
order: 1
devbox: true
devboxfile: LoadArrayData_devbox.md
published: true
categories:
  - 데이터 가져오기
tags: ['filldata', 'json']
---

RealGrid는 [LocalDataProvider.setRows()](http://help.realgrid.com/api/LocalDataProvider/setRows/) 함수를 이용해 배열형 데이터를 읽어 올 수 있습니다. 

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="carFields1"
  columnSet="carColumns1"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption1"
  styleSet="style1"

  showToolbox=true
  gridWidth="100%"
  gridHeight="300px" %}
