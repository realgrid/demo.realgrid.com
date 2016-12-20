컬럼그룹선택 <select id="groupList"></select>

컬럼 그룹에 포함된 자식 컬럼들의 배치 방향을 수평 혹은 수직으로 바꿀 수 있습니다.

<a class="btn primary small round lowercase" id="btnToggleOrientation">표시 방향</a>

```js
var colName = $("#groupList").val();     
var group = colName ? gridView.columnByName(colName) : null;
if (group) {
    var orientation = gridView.getColumnProperty(group, "orientation");
    orientation = (orientation == "vertical") ? "horizontal" : "vertical";
    gridView.setColumnProperty(group, "orientation", orientation);
}
```

그룹 헤더를 감추거나 표시할 수 있습니다.

<a class="btn primary small round lowercase" id="btnToggleHeaderVisible">표시 여부</a>

```js
var colName = $("#groupList").val();     
var group = colName ? gridView.columnByName(colName) : null;
if (group) {
    var header = gridView.getColumnProperty(group, "header");
    header.visible = !header.visible;
    gridView.setColumnProperty(group, "header", header);
}

```

자식들의 헤더를 모두 감출 수 있습니다.

<a class="btn primary small round lowercase" id="btnToggleHideChildHeaders">자식 표시 여부</a>

```js
var colName = $("#groupList").val();     
var group = colName ? gridView.columnByName(colName) : null;
if (group) {
    var hide = !gridView.getColumnProperty(group, "hideChildHeaders");
    gridView.setColumnProperty(group, "hideChildHeaders", hide);
}
```

그룹의 너비를 변경합니다.

<a class="btn primary small round lowercase" id="btnIncWidth">10 증가</a>

```js
var colName = $("#groupList").val();     
var group = colName ? gridView.columnByName(colName) : null;
if (group) {
    var width = gridView.getColumnProperty(group, "displayWidth") + 10;
    gridView.setColumnProperty(group, "displayWidth", width);
}
```

<a class="btn primary small round lowercase" id="btnDecWidth">10 감소</a>

```js
var colName = $("#groupList").val();     
var group = colName ? gridView.columnByName(colName) : null;
if (group) {
    var width = gridView.getColumnProperty(group, "displayWidth") - 10;
    gridView.setColumnProperty(group, "displayWidth", width);
}
```


<script>
function createGroupList(grid) {
  var names = grid.getGroupNames();
  var list = $("#groupList");
  
  $.map(names, function (c) {
    $("<option />", { value: c, text: c }).appendTo(list);
  });
} 

$("#btnToggleOrientation").click(function() { 
  var colName = $("#groupList").val();     
  var group = colName ? gridView.columnByName(colName) : null;
  if (group) {
      var orientation = gridView.getColumnProperty(group, "orientation");
      orientation = (orientation == "vertical") ? "horizontal" : "vertical";
      gridView.setColumnProperty(group, "orientation", orientation);
  }
});

$("#btnToggleHeaderVisible").click(function() { 
  var colName = $("#groupList").val();     
  var group = colName ? gridView.columnByName(colName) : null;
  if (group) {
      var header = gridView.getColumnProperty(group, "header");
      header.visible = !header.visible;
      gridView.setColumnProperty(group, "header", header);
  }
});

$("#btnToggleHideChildHeaders").click(function() { 
  var colName = $("#groupList").val();     
  var group = colName ? gridView.columnByName(colName) : null;
  if (group) {
      var hide = !gridView.getColumnProperty(group, "hideChildHeaders");
      gridView.setColumnProperty(group, "hideChildHeaders", hide);
  }
});

$("#btnIncWidth").click(function() { 
  var colName = $("#groupList").val();     
  var group = colName ? gridView.columnByName(colName) : null;
  if (group) {
      var width = gridView.getColumnProperty(group, "displayWidth") + 10;
      gridView.setColumnProperty(group, "displayWidth", width);
  }
});
$("#btnDecWidth").click(function() { 
  var colName = $("#groupList").val();     
  var group = colName ? gridView.columnByName(colName) : null;
  if (group) {
      var width = gridView.getColumnProperty(group, "displayWidth") - 10;
      gridView.setColumnProperty(group, "displayWidth", width);
  }
});
</script>

