---
layout: page
title: 행 유효성 검사
order: 2
devbox: true
devboxfile: RowValidation_devbox.md
published: true
categories:
  - 유효성 검사
tags: ['validation', '유효성']
---

사용자가 시작한 행 편집이 완료될 때, 그리드에 설정된 행 Validation들이 지정한 순서대로 검사됩니다.

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

  fieldSet="validationFields"
  columnSet="validationColumns"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption1"
  styleSet="style1"

  dataSet="CustomOrders.json"
  successDataSet="onGridSuccessDataSet"  
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}