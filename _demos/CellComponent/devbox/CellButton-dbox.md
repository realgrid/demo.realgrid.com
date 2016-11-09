셀 버튼은 `action`, `popup`, `image` 중 하나로 지정할 수 있습니다.  
`image`버튼은 하나의 컬럼에 여러 개를 표시할 수 있습니다.

```js
var columns = [{
    name: "EmployeeID",
    fieldName: "EmployeeID",
    width: "150",
    button: "image",
    imageButtons: {
        width: 45,
        height: 13,
        images: [{
            name: "팝업버튼",
            up: "/demo/resource/image/btnImages/popup_normal.png",
            hover: "/demo/resource/image/btnImages/popup_hover.png",
            down: "/demo/resource/image/btnImages/popup_click.png"
        }, {
            name: "조회버튼",
            up: "/demo/resource/image/btnImages/search_normal.png",
            hover: "/demo/resource/image/btnImages/search_hover.png",
            down: "/demo/resource/image/btnImages/search_click.png"           
        }]
    },
    styles: {
        textAlignment: "center"
    },
    header: {
        text: "Employee ID"
    }
},{
    name: "OrderID",
    fieldName: "OrderID",
    width: 90,
    styles: {
        textAlignment: "center"
    },
    button: "action",
    header: {
        text: "Order ID"
    }
}, {
    name: "CustomerID",
    fieldName: "CustomerID",
    width: 110,
    styles: {
        textAlignment: "center"
    },
    button: "popup",
    popupMenu: "customerPopup",
    header: {
        text: "Customer ID"
    }
},{
...
}];
grid.setColumns(columns);
```  
버튼은 컬럼의 alwaysShowButton을 true로 설정해 항상 보이게 하거나, 마우스가 해당 셀에 들어갈 때만 보이게 할 수 있습니다. 

<a class="btn primary small round lowercase" id="btnButtonAlwaysShowButton">alwaysShowButton</a>

```js
gridView.setColumnProperty("EmployeeID", "alwaysShowButton", "true");
gridView.setColumnProperty("OrderID", "alwaysShowButton", "true");
gridView.setColumnProperty("CustomerID", "alwaysShowButton", "true");
```
<p></p>

데이터 셀에 버튼을 표시하는 방법

- `always`: 항상 표시 
- `default`: hovering, focused상태에서 표시 
- `visible`: focused상태만 표시
- `hidden`: 표시하지 않음

<a class="btn primary small round lowercase" id="btnButtonAlways">Always</a>

```js
gridView.setColumnProperty("EmployeeID", "buttonVisibility", "always");
gridView.setColumnProperty("OrderID", "buttonVisibility", "always");
gridView.setColumnProperty("CustomerID", "buttonVisibility", "always");
```

<a class="btn primary small round lowercase" id="btnButtonDefault">Default</a>

```js
gridView.setColumnProperty("EmployeeID", "buttonVisibility", "default");
gridView.setColumnProperty("OrderID", "buttonVisibility", "default");
gridView.setColumnProperty("CustomerID", "buttonVisibility", "default");
```

<a class="btn primary small round lowercase" id="btnButtonVisible">Visible</a>

```js
gridView.setColumnProperty("EmployeeID", "buttonVisibility", "visible");
gridView.setColumnProperty("OrderID", "buttonVisibility", "visible");
gridView.setColumnProperty("CustomerID", "buttonVisibility", "visible");
```

<a class="btn primary small round lowercase" id="btnButtonHidden">Hidden</a>

```js
gridView.setColumnProperty("EmployeeID", "buttonVisibility", "hidden");
gridView.setColumnProperty("OrderID", "buttonVisibility", "hidden");
gridView.setColumnProperty("CustomerID", "buttonVisibility", "hidden");
```

<script>
  $('#btnButtonAlwaysShowButton').click(function() {
    gridView.setColumnProperty("EmployeeID", "alwaysShowButton", "true");
    gridView.setColumnProperty("OrderID", "alwaysShowButton", "true");
    gridView.setColumnProperty("CustomerID", "alwaysShowButton", "true");
  });

  $('#btnButtonAlways').click(function() {
    gridView.setColumnProperty("EmployeeID", "buttonVisibility", "always");
    gridView.setColumnProperty("OrderID", "buttonVisibility", "always");
    gridView.setColumnProperty("CustomerID", "buttonVisibility", "always");
  });

  $('#btnButtonDefault').click(function() {
    gridView.setColumnProperty("EmployeeID", "buttonVisibility", "default");
    gridView.setColumnProperty("OrderID", "buttonVisibility", "default");
    gridView.setColumnProperty("CustomerID", "buttonVisibility", "default");
  });

  $('#btnButtonVisible').click(function() {
    gridView.setColumnProperty("EmployeeID", "buttonVisibility", "visible");
    gridView.setColumnProperty("OrderID", "buttonVisibility", "visible");
    gridView.setColumnProperty("CustomerID", "buttonVisibility", "visible");
  });

  $('#btnButtonHidden').click(function() {
    gridView.setColumnProperty("EmployeeID", "buttonVisibility", "hidden");
    gridView.setColumnProperty("OrderID", "buttonVisibility", "hidden");
    gridView.setColumnProperty("CustomerID", "buttonVisibility", "hidden");
  });

</script>