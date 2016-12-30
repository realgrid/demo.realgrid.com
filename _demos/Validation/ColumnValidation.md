---
layout: page
title: 컬럼 유효성 검사
order: 1
devbox: true
devboxfile: ColumnValidation_devbox.md
published: true
categories:
  - 유효성 검사
tags: ['validation', '유효성']
---

행 편집 중에 각 셀의 사용자 편집이 끝나면 셀 컬럼에 설정된 컬럼 validation들을 순서대로 실행합니다.   
컬럼 Validations는 데이터필드가 아니라 컬럼 단위로 설정됩니다.   
예제에서 "Quantity 2" 컬럼은 "Quantity"와 같이 "Quantity" 데이터필드를 참조하지만 Validation 설정이 없으므로 에러가 발생하지 않습니다. 


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