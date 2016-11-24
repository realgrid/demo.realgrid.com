#### Tooltip 표시하기

전체 헤더의 툴팁 표시 여부를 설정합니다.

<a class="btn primary small round lowercase" id="btnHeaderShowTooltip">헤더 툴팁 표시</a>

```js
gridView.setHeader({showTooltip: true})
```

특정 컬럼 헤더의 툴팁 표시여부를 설정합니다.   
(전체 헤더의 툴팁 표시가 true 때 특정 컬럼만 해제할 수 있습니다.)

<a class="btn primary small round lowercase" id="btnColumnHeaderShowTooltip">R/D컬럼 헤더 툴팁 표시 해제</a>

```js
gridView.setColumnProperty("RequiredDate", "header", {showTooltip:false})
```

헤더 툴팁을 다른 내용으로 변경하려면 `header.tooltip`에 문자열을 지정합니다.

<a class="btn primary small round lowercase" id="btnColumnHeaderTooltip">O/D컬럼 헤더 툴팁 내용 변경</a>

```js
gridView.setColumnProperty("OrderDate", "header", {tooltip:"Order Date"})
```

데이터 영역에서 툴팁을 표시할 경우 `column.renderer.showTooltip`을 true로 설정하면 됩니다.  
데이터 영역의 툴팁은 기본적으로 원래의 값이 표시되고 다른 내용을 표시하려면 onShowTooltip 이벤트를 사용합니다.

```js
var columns = [{
    name: "OrderID",
    fieldName: "OrderID",
    width: "90",
    renderer: {
        showTooltip: true //툴팁 표시 여부
    },
    styles: {
        textAlignment: "center",
        background: "#ffffff99"
    },
    header: {
        text: "Order"
    }
}, {
	...
}];

gridView.setColumns(columns);
```

#### onShowTooltip 이벤트

[onShowTooltip](http://help.realgrid.com/api/GridBase/onShowTooltip/) 이벤트는
데이터셀의 툴팁이 표시될때 발생하는 콜백 함수입니다.   

```js
gridView.onShowTooltip = function (grid, index, value) {
    var column = index.column;
    var itemIndex = index.itemIndex;
     
    var tooltip = value;
    if (column == "OrderID") {
        tooltip = "No: " + value +
            "\r\nSales Emp: " + grid.getValue(itemIndex, "EmployeeID") +
            "\r\nProduct:" + grid.getValue(itemIndex, "ProductName") +
            "\r\nQty:" + grid.getValue(itemIndex, "Quantity");
    } else if (column == "CustomerID") {
        tooltip = "Id: " + value +
            "\r\nName: " + grid.getValue(itemIndex, "CompanyName") +
            "\r\nPhone:" + grid.getValue(itemIndex, "Phone");
    } else if (column == "ShipVia") {
        tooltip = "ShipVia: " + value +
            "\r\nShip Name: " + grid.getValue(itemIndex, "ShipName") +
            "(" + grid.getValue(itemIndex, "ShipAddress") +  " " +
                  grid.getValue(itemIndex, "ShipCity") + " " +
                  grid.getValue(itemIndex, "ShipCountry") +  ")" +
            "\r\nFreight:" + grid.getValue(itemIndex, "Freight");
    }
    return tooltip;
}
```

<script>
$('#btnHeaderShowTooltip').click(function() {
    gridView.setHeader({showTooltip: true})
});

$('#btnColumnHeaderShowTooltip').click(function() {
    gridView.setColumnProperty("RequiredDate", "header", {showTooltip:false})
});

$('#btnColumnHeaderTooltip').click(function() {
    gridView.setColumnProperty("OrderDate", "header", {tooltip:"OrderDate"})
});
</script>