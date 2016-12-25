---
layout: page
title: XML 데이타 가져오기
order: 3
devbox: true
devboxfile: LoadXmlData_devbox.md
published: true
categories:
  - 데이터 가져오기
tags: ['filldata', 'xml']
---


RealGrid는 [LocalDataProvider.fillXmlData()](http://help.realgrid.com/api/LocalDataProvider/fillXmlData/) 함수를 이용해 XML 포멧의 데이터를 읽어 올 수 있습니다. 

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
