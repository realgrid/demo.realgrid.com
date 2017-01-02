테스트할 컬럼 선택 <select id="columnList" onchange="javascript:selectColumn()">

#### 모든 컬럼 크기변경 가능 여부 설정

[DisplayOptions](http://help.realgrid.com/api/types/DisplayOptions/){:target="_blank"}.columnResizable 값을 False로 설정하면 사용자가 모든 컬럼의 크기를 변경할 수 없습니다.

<a class="btn primary small round lowercase" id="btnToggleGlobalColumnResizable">ToggleGlobalColumnResizable</a>

```js
var options = gridView.getDisplayOptions();

options.columnResizable = !options.columnResizable;
gridView.setDisplayOptions(options);
```

#### 선택한 컬럼 크기변경 가능 여부 설정  

<a class="btn primary small round lowercase" id="btnToggleColumnResizable">ToggleColumnResizable</a>

```js
var colName = $("#columnList").val();

if (colName) {
    var proxy = gridView.columnByName(colName);

    proxy.resizable = !proxy.resizable;
    gridView.setColumn(proxy);
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

function selectColumn() {
    var colName = $("#columnList").val();
    if (colName) {
        var columns = gridView.columnsByTag("sel");
        if (columns) {
            for (i = 0; i < columns.length; i++) {
                var column = columns[i];
                column.tag = undefined;
                column.header = {};
                column.header.styles = {
                    borderLeft: undefined,
                    borderRight: undefined,
                    borderTop: undefined,
                    borderBottom: undefined
                };
                gridView.setColumn(column);
            }
        }
 
        var column = gridView.columnByName(colName);
        if (column) {
 
            column.tag = "sel";
            column.header = {};
            column.header.styles = {
                borderLeft: "#ff660000,2",
                borderRight: "#ff660000,2",
                borderTop: "#ff660000,2",
                borderBottom: "#ff660000,2"
            };
            gridView.setColumn(column);
        }
    }
}

$("#btnToggleGlobalColumnResizable").click(function() { 
  var options = gridView.getDisplayOptions();

  options.columnResizable = !options.columnResizable;
  gridView.setDisplayOptions(options);
});

$("#btnToggleColumnResizable").click(function() { 
  var colName = $("#columnList").val();

  if (colName) {
      var proxy = gridView.columnByName(colName);

      proxy.resizable = !proxy.resizable;
      gridView.setColumn(proxy);
  }
});


</script>

