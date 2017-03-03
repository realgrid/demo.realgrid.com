#### 모든 컬럼 소트 가능 여부 설정

[SortingOptions](http://help.realgrid.com/api/types/SortingOptions/){:target="_blank"}.enabled 값을 False로 설정하면 사용자가 모든 컬럼을 사용자가 정렬할 수 없습니다.

<a class="btn primary small round lowercase" id="btnToggleGlobalColumnSortable">ToggleGlobalColumnSortable</a>

```js
var options = gridView.getSortingOptions();

options.enabled = !options.enabled;
gridView.setSortingOptions(options);
```

#### 선택한 컬럼 소트 가능 여부 설정  
테스트할 컬럼 선택 <select id="columnList" onchange="javascript:selectColumn()">
[DataColumn](http://help.realgrid.com/api/types/DataColumn/){:target="_blank"}.sortable의 값이 False로 설정된 컬럼은 사용자가 정렬할 수 없습니다.

<a class="btn primary small round lowercase" id="btnToggleColumnSortable">ToggleColumnSortable</a>

```js
var colName = $("#columnList").val();

if (colName) {
    var proxy = gridView.columnByName(colName);
    proxy.sortable = !proxy.sortable;
    gridView.setColumn(proxy);
}
```

#### 소트 스타일 지정

<a class="btn primary small round lowercase" id="btnNone">none</a>

```js
gridView.orderBy([]);

gridView.setSortingOptions({
  style: "none"
});
```

<a class="btn primary small round lowercase" id="btnExclusive">exclusive</a>

```js
gridView.orderBy([]);

gridView.setSortingOptions({
  style: "exclusive"
});
```

<a class="btn primary small round lowercase" id="btnInclusive">inclusive</a>

```js
gridView.orderBy([]);

gridView.setSortingOptions({
  style: "inclusive"
});
```

<a class="btn primary small round lowercase" id="btnReverse">reverse</a>

```js
gridView.orderBy([]);

gridView.setSortingOptions({
  style: "reverse"
});
```

#### 핸들 표시방법 지정

<a class="btn primary small round lowercase" id="btnHidden">hidden</a>

```js
gridView.orderBy([]);

gridView.setSortingOptions({
  handleVisibility: "hidden"
});
```

<a class="btn primary small round lowercase" id="btnVisible">visible</a>

```js
gridView.orderBy([]);

gridView.setSortingOptions({
  handleVisibility: "visible"
});
```

<a class="btn primary small round lowercase" id="btnAlways">always</a>

```js
gridView.orderBy([]);

gridView.setSortingOptions({
  handleVisibility: "always"
});
```

#### 핸들 기호를 이미지로 표시

이미지의 크기는 22px * 11px 이며 더 큰 크기일 경우 자동으로 스트레치 됩니다. 
이미지를 표시하기 위해서는 SortingOptions.handleImages의 ascending, descending, hoveredAscending, hoveredDescending, none, hoveredNone 속성에 해당 상태에 표시되는 이미지의 경로를 지정해야 합니다.

<a class="btn primary small round lowercase" id="btnSetHandleImage">setHandleImage</a>

```js
gridView.setSortingOptions({
  imageHandle: true,
  handleImages: {
      ascending: "/Images/desc.png",
      descending: "/Images/asc.png",
      hoveredAscending: "/Images/desc_hov.png",
      hoveredDescending: "/Images/asc_hov.png",
      none: "/Images/none.png",
      hoveredNone: "/Images/none_hov.png"
  }
});

gridView.refresh();
```

#### 정렬 순서 표시

[SortingOptions](http://help.realgrid.com/api/types/SortingOptions/){:target="_blank"}.showSortOrder 값을 True로 설정하면 Sort핸들 오른쪽에 정렬순서가 표시됩니다. 

<a class="btn primary small round lowercase" id="btnSetShowSortOrder">setShowSortOrder</a>

```js
gridView.setSortingOptions({
  showSortOrder: true, 
  sortOrderStyles: {
    font:"굴림체", 
    fontSize:10, 
    fontBold:true, 
    foreground:"#ffff8888", 
    textAlignment:"far"
  }
});
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

$("#btnToggleGlobalColumnSortable").click(function() { 
  var options = gridView.getSortingOptions();

  options.enabled = !options.enabled;
  gridView.setSortingOptions(options);
});

$("#btnToggleColumnSortable").click(function() { 
  var colName = $("#columnList").val();

  if (colName) {
      var proxy = gridView.columnByName(colName);
      proxy.sortable = !proxy.sortable;
      gridView.setColumn(proxy);
  }
});

$("#btnNone").click(function() { 
  gridView.orderBy([]);

  gridView.setSortingOptions({
    style: "none"
  });
});

$("#btnExclusive").click(function() { 
  gridView.orderBy([]);

  gridView.setSortingOptions({
    style: "exclusive"
  });
});

$("#btnInclusive").click(function() { 
  gridView.orderBy([]);

  gridView.setSortingOptions({
    style: "inclusive"
  });
});

$("#btnReverse").click(function() { 
  gridView.orderBy([]);

  gridView.setSortingOptions({
    style: "reverse"
  });
});

$("#btnHidden").click(function() { 
  gridView.orderBy([]);

  gridView.setSortingOptions({
    handleVisibility: "hidden"
  });
});

$("#btnVisible").click(function() { 
  gridView.orderBy([]);

  gridView.setSortingOptions({
    handleVisibility: "visible"
  });
});

$("#btnAlways").click(function() { 
  gridView.orderBy([]);

  gridView.setSortingOptions({
    handleVisibility: "always"
  });
});

$("#btnSetHandleImage").click(function() { 
  gridView.setSortingOptions({
    imageHandle: true,
    handleImages: {
        ascending: "{{"/resource/image/common/" | prepend: site.baseurl}}" + "/desc.png",
        descending: "{{"/resource/image/common/" | prepend: site.baseurl}}" + "/asc.png",
        hoveredAscending: "{{"/resource/image/common/" | prepend: site.baseurl}}" + "/desc_hov.png",
        hoveredDescending: "{{"/resource/image/common/" | prepend: site.baseurl}}" + "/asc_hov.png",
        none: "{{"/resource/image/common/" | prepend: site.baseurl}}" + "/none.png",
        hoveredNone: "{{"/resource/image/common/" | prepend: site.baseurl}}" + "/none_hov.png"
    }
  });

  gridView.refresh();
});

$("#btnSetShowSortOrder").click(function() { 
  gridView.setSortingOptions({
    showSortOrder: true, 
    sortOrderStyles: {
      font:"굴림체", 
      fontSize:10, 
      fontBold:true, 
      foreground:"#ffff8888", 
      textAlignment:"far"
    }
  });
});

</script>

