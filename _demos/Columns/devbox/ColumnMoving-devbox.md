테스트할 컬럼 선택 <select id="columnList" onchange="javascript:selectColumn()">

#### 모든 컬럼 이동 가능 여부 설정

[DisplayOptions](http://help.realgrid.com/api/types/DisplayOptions/){:target="_blank"}.columnMovable를 값을 False로 설정하면 모든 컬럼을 사용자가 이동할 수 없게 됩니다.

<a class="btn primary small round lowercase" id="btnToggleGlobalColumnMovable">ToggleGlobalColumnMovable</a>

```js
var options = gridView.getDisplayOptions();
options.columnMovable = !options.columnMovable;
gridView.setDisplayOptions(options);
```

#### 부모 컬럼 변경 가능 여부 설정 

[DisplayOptions](http://help.realgrid.com/api/types/DisplayOptions/){:target="_blank"}.parentChangable 값이 True이면 컬럼의 부모를 사용자가 드래깅으로 변경할 수 있습니다. (그룹 내 자식 컬럼의 수가 1개이면 이동이 불가합니다)

<a class="btn primary small round lowercase" id="btnToggleParentChangable">ToggleParentChangable</a>

```js
var options = gridView.getDisplayOptions();
options.parentChangable = !options.parentChangable;
gridView.setDisplayOptions(options);
```

#### 선택한 컬럼 이동 가능 여부 설정  

<a class="btn primary small round lowercase" id="btnToggleSelectedColumnMovable">ToggleSelectedColumnMovable</a>

```js
  var colName = $("#columnList").val();
  if (colName) {
    var proxy = gridView.columnByName(colName);
    proxy.movable = !proxy.movable;
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

$("#btnToggleGlobalColumnMovable").click(function() { 
  var options = gridView.getDisplayOptions();
  options.columnMovable = !options.columnMovable;
  gridView.setDisplayOptions(options);
});

$("#btnToggleParentChangable").click(function() { 
  var options = gridView.getDisplayOptions();
  options.parentChangable = !options.parentChangable;
  gridView.setDisplayOptions(options);
});

$("#btnToggleSelectedColumnMovable").click(function() { 
  var colName = $("#columnList").val();
  if (colName) {
    var proxy = gridView.columnByName(colName);
    proxy.movable = !proxy.movable;
    gridView.setColumn(proxy);
  } 
});

</script>

