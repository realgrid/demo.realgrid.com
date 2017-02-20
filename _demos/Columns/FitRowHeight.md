---
layout: page
title: 행 높이 개별지정
order: 12
devbox: true
devboxfile: FitRowHeight-devbox.md
published: true
categories:
  - 컬럼
tags: ['Height', '행 높이']
---

지정한 행 높이를 표시되는 데이터에 맞게 변경합니다.

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

  fieldSet="DefaultField"
  columnSet="fitRowHeightColumn"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="DefaultGridOption"
  styleSet="style1"

  dataSet="firRowHeightData.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}