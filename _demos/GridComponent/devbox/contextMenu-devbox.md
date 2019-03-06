#### 컨텍스트 메뉴 설정
 [GridView.setContextMenu()](http://help.realgrid.com/api/GridBase/setContextMenu/)를 사용하여 컨텍스트 메뉴를 설정할 수 있습니다.

<a class="btn primary small round lowercase" id="btnSetContextMenu">컨텍스트 메뉴 설정</a>

```js
  gridView.setContextMenu([{
      label: "Menu1"
  }, {
      label: "Menu2"
  }, {
      label: "-" // menu separator를 삽입합니다.
  }, {
      label: "ExcelExport"
  }]);
```

#### 컨텍스트 메뉴 호출시 발생하는 콜백함수 `(Only JS Support)`
현재 [GridView.onContextMenuPopup()](http://help.realgrid.com/api/GridBase/onContextMenuPopup/)에는 아무것도 설정되어 있지 않기 때문에 그리드의 어느 영역에서나 마우스 오른쪽 버튼을 클릭하게되면 컨텍스트 메뉴가 팝업 됩니다.  
만약 onContextMenuPopup()에서 false를 리턴하게 되면 컨텍스트 메뉴 호출이 취소됩니다.  
헤더영역에서 호출시 팝업되지 않게 설정해보도록 하겠습니다.

<a class="btn primary small round lowercase" id="btnOnContextMenuPopup">onContextMenuPopup 설정</a>

```js
  gridView.onContextMenuPopup = function (grid, x, y, elementName) {
    //헤더셀 영역에서는 컨텍스트 메뉴 실행하지 않음
    return elementName != "HeaderCell";
  }
```


#### 컨텍스트 메뉴를 클릭시 발생하는 콜백함수
컨텍스트 메뉴를 클릭하면 [GridView.onContextMenuClicked()](http://help.realgrid.com/api/GridBase/onContextMenuClicked/)가 발생합니다. 이 콜백 함수에서 각 메뉴에 대한 기능정의를 할 수 있습니다.  

<a class="btn primary small round lowercase" id="btnOnContextMenuItemClicked">onContextMenuItemClicked 설정</a>

```js
  gridView.onContextMenuItemClicked = function (grid, label, index) {
    alert("Context menu가 클릭됐습니다: " + label.label + "\n" + JSON.stringify(index));
    if (label.label == "ExcelExport") {
        grid.exportGrid({
            type: "excel",
            target: "local"
        });
    };
  };
```

#### 동적 컨텍스트 메뉴

<a class="btn primary small round lowercase" id="btnSetContextMenu2">동적 컨텍스트 메뉴 설정</a>

컬럼 해더와 데이터 셀 영역에 다른 컨텍스트 메뉴와 동작들로 구성한 예제입니다.

```
var toggle = false;
function setContextMenu(grid) {
   grid.onContextMenuItemClicked = function (grid, data, index) {
       if (data.tag == 'excel') {
           grid.exportGrid({
               type: "excel",
               target: "local",
               fileName: "gridExportSample.xlsx"
           });
       } else if (data.tag == 'filter' && index.column) {
           createColumnFilter(grid, index.column);
       } else if (data.tag == 'visibleTrue') {
           var columns = grid.getColumns();

           for (var i in columns) {
               grid.setColumnProperty(columns[i].name, "visible", true);
           }
           toggle = false;
           setHeaderCellContextMenu(grid, toggle);
       } else if (data.tag == 'visibleFalse') {
           grid.setColumnProperty(index.column, "visible", false);

           toggle = true;
           setHeaderCellContextMenu(grid, toggle);
       } else if (data.tag == 'fixedCol') {
           var count = grid.getColumnProperty(index.column, "displayIndex") + 1;
           grid.setFixedOptions({ colCount: count });
       } else if (data.tag == 'fixedRow') {
           var count = index.itemIndex + 1;
           grid.setFixedOptions({ rowCount: count });
       } else if (data.tag == 'fixedCancel') {
           grid.setFixedOptions({ colCount: 0, rowCount: 0 });
       };
   }

   grid.onContextMenuPopup = function (grid, x, y, elementName) {
       if (elementName == 'HeaderCell') {
           setHeaderCellContextMenu(grid, toggle);
       } else if (elementName == 'DataCell') {
           setDataCellContextMenu(grid);
       } else {
           return false;
       }
   };

   setDataCellContextMenu(grid);
}

function setHeaderCellContextMenu(grid, val) {
   var contextMenu = [{
       label: '엑셀 내보내기',
       tag: 'excel'
   }, {
       label: '필터 만들기',
       tag: 'filter'
   }, {
       label: "-"
   }, {
       label: '컬럼 숨기기',
       tag: 'visibleFalse'
   }, {
       label: '컬럼 모두 보이기',
       tag: 'visibleTrue',
       enabled: val
   }];

   grid.setContextMenu(contextMenu);
}

function setDataCellContextMenu(grid) {
   var contextMenu = [{
       label: '엑셀 내보내기',
       tag: 'excel'
   }, {
       label: "-"
   }, {
       label: '열 고정',
       tag: 'fixedCol'
   }, {
       label: '행 고정',
       tag: 'fixedRow'
   }, {
       label: '고정 취소',
       tag: 'fixedCancel'
   }];

   grid.setContextMenu(contextMenu);
}

function setHeaderCellContextMenu(grid, val) {
   var contextMenu = [{
       label: '엑셀 내보내기',
       tag: 'excel'
   }, {
       label: '필터 만들기',
       tag: 'filter'
   }, {
       label: "-"
   }, {
       label: '컬럼 숨기기',
       tag: 'visibleFalse'
   }, {
       label: '컬럼 모두 보이기',
       tag: 'visibleTrue',
       enabled: val
   }];

   grid.setContextMenu(contextMenu);
}

function setDataCellContextMenu(grid) {
   var contextMenu = [{
       label: '엑셀 내보내기',
       tag: 'excel'
   }, {
       label: "-"
   }, {
       label: '열 고정',
       tag: 'fixedCol'
   }, {
       label: '행 고정',
       tag: 'fixedRow'
   }, {
       label: '고정 취소',
       tag: 'fixedCancel'
   }];

   grid.setContextMenu(contextMenu);
}

function createColumnFilter(grid, colName) {
    var fieldName = grid.getColumnProperty(colName, "fieldName");
    var distinctValues = dataProvider.getDistinctValues(fieldName);
    var filters = [];

    for (var i = 0; i < distinctValues.length; i++) {
        filters.push({ name: distinctValues[i], criteria: "value = " + "'" + distinctValues[i] + "'" });
    }

    gridView.setColumnFilters(colName, filters);
}

setContextMenu(gridView);
```

<script>

  $('#btnSetContextMenu').click(function() {
    gridView.setContextMenu([{
        label: "Menu1"
    }, {
        label: "Menu2"
    }, {
        label: "-" // menu separator를 삽입합니다.
    }, {
        label: "ExcelExport"
    }]);
  });

  $('#btnOnContextMenuPopup').click(function() {
    gridView.onContextMenuPopup = function (grid, x, y, elementName) {
      //헤더셀 영역에서는 컨텍스트 메뉴 실행하지 않음
      return elementName != "HeaderCell";
    }
  });

  $('#btnOnContextMenuItemClicked').click(function() {
    gridView.onContextMenuItemClicked = function (grid, label, index) {
      alert("Context menu가 클릭됐습니다: " + label.label + "\n" + JSON.stringify(index));
      if (label.label == "ExcelExport") {
          grid.exportGrid({
              type: "excel",
              target: "local"
          });
      };
    };
  });

  $('#btnSetContextMenu2').click(function() {
    var toggle = false;
    function setContextMenu(grid) {

       grid.onContextMenuItemClicked = function (grid, data, index) {
           if (data.tag == 'excel') {
               grid.exportGrid({
                   type: "excel",
                   target: "local",
                   fileName: "gridExportSample.xlsx"
               });
           } else if (data.tag == 'filter' && index.column) {
               createColumnFilter(grid, index.column);
           } else if (data.tag == 'visibleTrue') {
               var columns = grid.getColumns();

               for (var i in columns) {
                   grid.setColumnProperty(columns[i].name, "visible", true);
               }
               toggle = false;
               setHeaderCellContextMenu(grid, toggle);
           } else if (data.tag == 'visibleFalse') {
               grid.setColumnProperty(index.column, "visible", false);

               toggle = true;
               setHeaderCellContextMenu(grid, toggle);
           } else if (data.tag == 'fixedCol') {
               var count = grid.getColumnProperty(index.column, "displayIndex") + 1;
               grid.setFixedOptions({ colCount: count });
           } else if (data.tag == 'fixedRow') {
               var count = index.itemIndex + 1;
               grid.setFixedOptions({ rowCount: count });
           } else if (data.tag == 'fixedCancel') {
               grid.setFixedOptions({ colCount: 0, rowCount: 0 });
           };
       }

       grid.onContextMenuPopup = function (grid, x, y, elementName) {
           if (elementName == 'HeaderCell') {
               setHeaderCellContextMenu(grid, toggle);
           } else if (elementName == 'DataCell') {
               setDataCellContextMenu(grid);
           } else {
               return false;
           }
       };

       setDataCellContextMenu(grid);
   }

   function setHeaderCellContextMenu(grid, val) {
       var contextMenu = [{
           label: '엑셀 내보내기',
           tag: 'excel'
       }, {
           label: '필터 만들기',
           tag: 'filter'
       }, {
           label: "-"
       }, {
           label: '컬럼 숨기기',
           tag: 'visibleFalse'
       }, {
           label: '컬럼 모두 보이기',
           tag: 'visibleTrue',
           enabled: val
       }];

       grid.setContextMenu(contextMenu);
   }

   function setDataCellContextMenu(grid) {
       var contextMenu = [{
           label: '엑셀 내보내기',
           tag: 'excel'
       }, {
           label: "-"
       }, {
           label: '열 고정',
           tag: 'fixedCol'
       }, {
           label: '행 고정',
           tag: 'fixedRow'
       }, {
           label: '고정 취소',
           tag: 'fixedCancel'
       }];

       grid.setContextMenu(contextMenu);
   }
   
    function setHeaderCellContextMenu(grid, val) {
       var contextMenu = [{
           label: '엑셀 내보내기',
           tag: 'excel'
       }, {
           label: '필터 만들기',
           tag: 'filter'
       }, {
           label: "-"
       }, {
           label: '컬럼 숨기기',
           tag: 'visibleFalse'
       }, {
           label: '컬럼 모두 보이기',
           tag: 'visibleTrue',
           enabled: val
       }];

       grid.setContextMenu(contextMenu);
   }

   function setDataCellContextMenu(grid) {
       var contextMenu = [{
           label: '엑셀 내보내기',
           tag: 'excel'
       }, {
           label: "-"
       }, {
           label: '열 고정',
           tag: 'fixedCol'
       }, {
           label: '행 고정',
           tag: 'fixedRow'
       }, {
           label: '고정 취소',
           tag: 'fixedCancel'
       }];

       grid.setContextMenu(contextMenu);
   }

   function createColumnFilter(grid, colName) {
        var fieldName = grid.getColumnProperty(colName, "fieldName");
        var distinctValues = dataProvider.getDistinctValues(fieldName);
        var filters = [];

        for (var i = 0; i < distinctValues.length; i++) {
            filters.push({ name: distinctValues[i], criteria: "value = " + "'" + distinctValues[i] + "'" });
        }

        gridView.setColumnFilters(colName, filters);
    }

   setContextMenu(gridView);
  });

</script>
