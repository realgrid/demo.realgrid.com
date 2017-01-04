---
layout: page
title: 텍스트 렌더러
order: 1
devbox: true
devboxfile: TextCellRenderer_devbox.md
published: true
categories:
  - 렌더러
tags: ['렌더러', 'renderer']
---

TextCellRenderer는 리얼그리드의 기본 Data 셀 렌더러입니다.   
별도로 추가된 속성없이 컬럼에 설정된 스타일 값들을 이용해 셀에 표시할 값을 텍스트로 표시합니다. 

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

  fieldSet="textCellRendererFields"
  columnSet="textCellRendererColumns"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption1"
  styleSet="style1"

  dataSet="CustomOrders.json"
  successDataSet="onGridSuccessDataSet"  
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}