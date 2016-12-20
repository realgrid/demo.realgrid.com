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

#### 컨텍스트 메뉴 호출시 발생하는 콜백함수
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

</script>
