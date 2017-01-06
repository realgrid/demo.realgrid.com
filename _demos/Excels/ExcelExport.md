---
layout: page
title: Excel Export
order: 1
devbox: true
devboxfile: ExcelExport_devbox.md
published: true
categories:
  - 엑셀 내보내기
tags: ['excel', 'export']
---

현재 그리드에 표시된 컬럼 구조대로 데이터셋을 엑셀 파일로 변환해서 로컬파일로 저장하거나 서버로 업로드합니다.  
`new` excel로 data 내보내기가 완료되었을 때 실행할 수 있는 함수를 지정하는 done 속성이 추가되었습니다. 

<script>
var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
  dataProvider.setRows(data);
}
var onDoneDataSet = function() {
	var cellDefaultStyles = [{
        criteria: "value like 'VI%'",
        styles: "background=#11ff0000"
	}];
	gridView.setStyles({
		body: {
	        cellDynamicStyles: cellDefaultStyles
	    }
	});
}
</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="excelExportFields"
  columnSet="excelExportColumns"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption1"
  styleSet="style1"

  dataSet="CustomOrders.json"
  successDataSet="onGridSuccessDataSet"  
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}