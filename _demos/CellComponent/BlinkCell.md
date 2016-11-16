---
layout: page
title: 같은 값의 셀 생략 하기
order: 1
devbox: true
devboxfile: BlinkCell-devbox.md
categories:
  - 셀 구성요소
tags: ['BlinkCell', '병합', '셀병합']
---

equalBlank속성을 이용하면 기초적인 셀 병합 효과를 낼 수 있습니다. 

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

 컬럼 비우기 대신 실제 컬럼 셀들을 병합하는 방법은 컬럼 셀 병합에서 확인 하십시오.   
 Row Grouping된 컬럼 셀들의 병합 방식에 대해서는 병합 모드 Row Grouping을 참조하십시오.