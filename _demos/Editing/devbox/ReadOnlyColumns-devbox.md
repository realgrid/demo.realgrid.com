#### skipReadOnly

[EditOptions](http://help.realgrid.com/api/types/EditOptions/){:target="_blank"}.skipReadOnly를 true로 지정하면 편집 중에 방향키나 탭키로 이동할 때 건너뛰게 됩니다.

<input type="checkbox" id="chkSkipReadOnly">skipReadOnly <a class="btn primary small round lowercase" id="btnSetEditOptions">설정</a>

```js
gridView.setEditOptions({
  skipReadOnly: $("#chkSkipReadOnly").is(":checked")
});
```

#### readOnly, editable
[DataColumn](http://help.realgrid.com/api/types/DataColumn/){:target="_blank"}의 readOnly 속성을 true로 하거나, editable을 false로 설정하면 해당 컬럼의 셀들에서는 사용자가 입력을 할 수 없게 됩니다.

컬럼선택 <select id="columnList"></select>

<input type="checkbox" id="chkReadOnly" >readOnly <a class="btn primary small round lowercase" id="btnSetColumnPropertyReadOnly">적용</a>

```js
var column = $("#columnList").val();
if (column) {
    gridView.setColumnProperty(column, "readOnly", $("#chkReadOnly").is(":checked"));
}
```

<input type="checkbox" id="chkEditable" >editable <a class="btn primary small round lowercase" id="btnSetColumnPropertyEditable">적용</a>

```js
var column = $("#columnList").val();
if (column) {
    gridView.setColumnProperty(column, "editable", $("#chkEditable").is(":checked"));
}
```


#### DataCellStyle
DataCellStyle의 편집 속성을 지정해서 특정 데이터셀을 read-only로 지정할 수 있습니다.

** CellStyle 정의

```js
gridView.addCellStyle("style01", {
	"foreground": "#ffffffff",
	"background": "#ff333333",
	"fontSize": 13,
	"fontBold": true,
	"editable": false
});
gridView.addCellStyle("style02", {
	"foreground": "#ff000000",
	"background": "#ffcccccc",
	"fontSize": 13,
	"readOnly": true
});
```

<a class="btn primary small round lowercase" id="btnReadOnly">ReadOnly 설정</a>

```js
gridView.setCellStyles([3, 4, 5], ["CompanyName"], "style01");
gridView.setFocus();
```

<a class="btn primary small round lowercase" id="btnEditable">Editable 설정</a>

```js
gridView.setCellStyles([6, 7, 8], ["CustomerID"], "style02");
gridView.setFocus();
```

<a class="btn primary small round lowercase" id="btnClearCellStyles">Style 해제</a>

```js
gridView.clearCellStyles();
gridView.setFocus();
```

<script>
function createColumnList(grid) {
    var names = grid.getColumnNames();
    var list = $("#columnList");
 
    $.map(names, function (c) {
        $("<option />", { value: c, text: c }).appendTo(list);
    });
}

$("#btnSetEditOptions").click(function() { 
	gridView.setEditOptions({
	  skipReadOnly: $("#chkSkipReadOnly").is(":checked")
	});
});

$("#btnSetColumnPropertyReadOnly").click(function() { 
	var column = $("#columnList").val();
	if (column) {
	    gridView.setColumnProperty(column, "readOnly", $("#chkReadOnly").is(":checked"));
	}
});

$("#btnSetColumnPropertyEditable").click(function() { 
	var column = $("#columnList").val();
	if (column) {
	    gridView.setColumnProperty(column, "editable", $("#chkEditable").is(":checked"));
	}
});

$("#btnReadOnly").click(function() { 
	gridView.setCellStyles([3, 4, 5], ["CompanyName"], "style01");
	gridView.setFocus();
});

$("#btnEditable").click(function() { 
	gridView.setCellStyles([6, 7, 8], ["CustomerID"], "style02");
	gridView.setFocus();
});

$("#btnClearCellStyles").click(function() { 
	gridView.clearCellStyles();
	gridView.setFocus();
});
</script>