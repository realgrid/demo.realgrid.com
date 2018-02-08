---
layout: page
title: ExportToCsv
order: 13
devbox: true
devboxfile: ExportToCsv_devbox.md
published: true
categories:
  - 엑셀 내보내기
tags: ['excel', 'export', "csv"]
---

지정한 설정에 따라 데이터를 CSV 문서로 내보냅니다. dataProvider 수준에서 export 되는 것이기 때문에 컬럼그룹 및 로우그룹, 스타일등 gridView와 관련된 부분은 적용되지 않습니다.

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