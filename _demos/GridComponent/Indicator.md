---
layout: page
title: 인디케이터
order: 1
devbox: true
devboxfile: indicator-dbox.md
categories:
  - 그리드 구성요소
tags: ['indicator', 'item', 'number', '행번호']
---

인디케이터(Indicator)는 그리드의 가장 왼쪽에 위치한 수직 영역으로 데이터의 행 번호등을 표시하기 위한 용도로 사용 할 수 있습니다.

{% include realgrid.html
  gridVar="gridView"
  dpVar="dataProvider"
  fieldSet="fieldset1"
  columnSet="columnset1"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption1"
  styleSet="style1"
  dataSet="griddata1"
  gridId="realgrid"
  gridWidth="100%"
  gridHeight="300px" %}


  *displayValue*
  * `none`: 값을 표시 하지 않습니다.
  * `index`: 1부터 시작하여 표시합니다. (정렬에 무관하게 1번부터 시작)
  * `row`: Row의 고유번호를 표시합니다. (정렬에 따라서 섞여서 표시)
