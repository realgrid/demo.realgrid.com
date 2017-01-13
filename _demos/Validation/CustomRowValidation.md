---
layout: page
title: 사용자 지정 행 유효성 검사
order: 4
devbox: true
devboxfile: CustomRowValidation_devbox.md
published: true
categories:
  - 유효성 검사
tags: ['validation', '유효성']
---

그리드 Row Validation만으로 부족한 경우, 행 편집 완료 시 그리드가 발생 시키는 onValidateRow 이벤트를 활용해서 셀 단위로 값을 검증할 수 있습니다.

<script>
var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
	dataProvider.setRows(data);
}
var onDoneDataSet = function() {
	gridView.setColumnProperty("UnitPrice","styles",{background:"#22f09300"})
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