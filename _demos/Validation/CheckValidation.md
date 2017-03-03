---
layout: page
title: 전체 유효성 검사
order: 5
devbox: true
devboxfile: CheckValidation_devbox.md
published: true
categories:
  - 유효성 검사
tags: ['validation', '유효성']
---

사용자의 입력 데이터만 유효성을 확인하는 것이 아닌 기존에 로드된 데이터를 대상으로 확인 할 수 있는 기능입니다.     
[gridView.checkValidateCells(itemIndices)](http://help.realgrid.com/api/GridBase/checkValidateCells/)를 사용하여 특정 데이터 행이나 모든 행을 확인 할 수 있으며, 
[gridView.getInvalidCellList()](http://help.realgrid.com/api/GridBase/getInvalidCellList/)를 사용하여 현재 확인 실패 목록을 가져올 수 있습니다. 

getInvalidCellList()을 실행하기 전에 checkValidateCells()가 선행되어 있어야 합니다.

<script>
var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
	dataProvider.setRows(data, 0, 20);
}
var onDoneDataSet = function() {

} 
</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="DefaultField"
  columnSet="CheckValidationColumns"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="DefaultGridOption"
  styleSet="style1"

  dataSet="DefaultDataSet.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}