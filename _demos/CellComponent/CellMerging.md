---
layout: page
title: 셀 병합
order: 4
devbox: true
devboxfile: CellMerging-devbox.md
published: true
categories:
  - 셀 구성요소
tags: ['CellMerging', '병합', 'merge']
---

컬럼에 속한 셀들을 묶어서 표시할 수 있습니다.

{% include realgrid.html
  gridVar="gridView"
  dpVar="dataProvider"
  fieldSet="cellMergingField"
  columnSet="cellMergingColumn"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption1"
  styleSet="style1"
  dataSet="griddata1"
  gridId="realgrid"
  gridWidth="100%"
  gridHeight="300px" %}