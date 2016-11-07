---
layout: page
title: 컬럼 속성 변경하기
order: 2
devbox: true
devboxfile: ColumnProperties-dbox.md
categories: 컬럼
tags: ['column', '컬럼', 'properties', '속성']
---

<script>
var onSuccessFieldSet = function(data, textStatus, jqXHR) {
	var flds = dataProvider.getFieldCount();
	if (flds > 0) {
	    var rows = [];

	    for (var i = 0; i < 10; i++) {
	        var row = [];
	        for (var c = 0; c < flds; c++) {
	            row.push("Cell(" + i + ", " + c + ")");
	        }
	        rows.push(row);
	    }

	    dataProvider.setRows(rows);
	}
}
var onSuccessColumnSet = function(data, textStatus, jqXHR) {
	createColumnList(gridView);
}
</script>

{% include realgrid.html
  gridVar="gridView"
  dpVar="dataProvider"
  fieldSet="fieldset_setColumns"
  columnSet="columnset_setColumns"
  styleSet="style1"
  gridId="realgrid"
  gridWidth="100%"
  gridHeight="300px" 
  successFieldSet="onSuccessFieldSet"
  successColumnSet="onSuccessColumnSet"
%}

