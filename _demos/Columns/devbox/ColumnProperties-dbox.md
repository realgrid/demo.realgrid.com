컬럼선택 <select id="columnList"></select>

#### 컬럼속성 제어하기  
[`getColumnProperty()`](http://help.realgrid.com/api/GridBase/getColumnProperty/){:target="_blank"},[`setColumnProperty()`](http://help.realgrid.com/api/GridBase/setColumnProperty/){:target="_blank"} 함수를 이용하여 [컬럼](http://help.realgrid.com/api/types/DataColumn/){:target="_blank"}의 속성을 변경합니다.

<a class="btn primary small round lowercase" id="btnToggleVisible">표시 여부</a>

```js
var column = gridView.columnByName($("#columnList").val());
if (column) {
  var visible = !gridView.getColumnProperty(column, "visible");
  gridView.setColumnProperty(column, "visible", visible);
}
```

<a class="btn primary small round lowercase" id="btnIncWidth">너비 증가</a>

```js
var column = gridView.columnByName($("#columnList").val());
if (column) {
  var width = gridView.getColumnProperty(column, "width") + 10;
  gridView.setColumnProperty(column, "width", width);
}

```

<a class="btn primary small round lowercase" id="btnDecWidth">너비 감소</a>

```js

var column = gridView.columnByName($("#columnList").val());
if (column) {
  var width = gridView.getColumnProperty(column, "width") - 10;
  gridView.setColumnProperty(column, "width", width);
```

헤더의 우측 경계를 Drag하여 컬럼 크기 변경 가능 여부를 결정합니다. 

<a class="btn primary small round lowercase" id="btnToggleResizable">크기변경 여부</a>

```js
var column = gridView.columnByName($("#columnList").val());
if (column) {
  var resizable = !gridView.getColumnProperty(column, "resizable");
  gridView.setColumnProperty(column, "resizable", resizable);
}
```

헤더를 클릭하여 정렬 가능 여부를 결정합니다.

<a class="btn primary small round lowercase" id="btnToggleSortable">정렬 여부</a>

```js
var column = gridView.columnByName($("#columnList").val());
if (column) {
  var sortable = !gridView.getColumnProperty(column, "sortable");
  gridView.setColumnProperty(column, "sortable", sortable);
}
```

<script>
function createColumnList(grid) {
    var names = grid.getColumnNames();
    var list = $("#columnList");
 
    $.map(names, function (c) {
        $("<option />", { value: c, text: c }).appendTo(list);
    });
}

$("#btnToggleVisible").click(function() { 
	var column = gridView.columnByName($("#columnList").val());
	if (column) {
	    var visible = !gridView.getColumnProperty(column, "visible");
	    gridView.setColumnProperty(column, "visible", visible);
    }
});
$("#btnIncWidth").click(function() { 
    var column = gridView.columnByName($("#columnList").val());
    if (column) {
        var width = gridView.getColumnProperty(column, "width") + 10;
        gridView.setColumnProperty(column, "width", width);
    }
});
$("#btnDecWidth").click(function() { 
    var column = gridView.columnByName($("#columnList").val());
    if (column) {
        var width = gridView.getColumnProperty(column, "width") - 10;
        gridView.setColumnProperty(column, "width", width);
    }
});
$("#btnToggleResizable").click(function() { 
    var column = gridView.columnByName($("#columnList").val());
    if (column) {
        var resizable = !gridView.getColumnProperty(column, "resizable");
        gridView.setColumnProperty(column, "resizable", resizable);
    }
});
$("#btnToggleSortable").click(function() { 
    var column = gridView.columnByName($("#columnList").val());
    if (column) {
        var sortable = !gridView.getColumnProperty(column, "sortable");
        gridView.setColumnProperty(column, "sortable", sortable);
    }
});
</script>

