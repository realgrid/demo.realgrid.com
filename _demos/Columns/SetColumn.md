---
layout: page
title: 컬럼 만들기
order : 1
devbox: true
devboxfile: SetColumns-dbox.md
categories: 컬럼
tags: ['컬럼', 'column', 'setColumns']
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
</script>

{% include realgrid.html
  gridVar="gridView"
  dpVar="dataProvider"
  fieldSet="fieldset_setColumns"
  gridOptionSet="gridOption_setColumns"
  styleSet="style1"
  gridId="realgrid"
  gridWidth="100%"
  gridHeight="300px" 
  successFieldSet="onSuccessFieldSet"
%}

