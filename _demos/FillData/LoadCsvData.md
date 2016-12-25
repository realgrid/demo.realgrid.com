---
layout: page
title: CSV 데이타 가져오기
order: 4
devbox: true
devboxfile: LoadCsvData_devbox.md
published: true
categories:
  - 데이터 가져오기
tags: ['filldata', 'csv']
---

RealGrid는 [LocalDataProvider.fillCsvData()](http://help.realgrid.com/api/LocalDataProvider/fillCsvData/) 함수를 이용해 CSV 포멧의 데이터를 읽어 올 수 있습니다. 

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="carFields2"
  columnSet="carColumns2"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption1"
  styleSet="style1"

  showToolbox=true
  gridWidth="100%"
  gridHeight="300px" %}
