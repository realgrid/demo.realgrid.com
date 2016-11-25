---
layout: page
title: 툴팁
order: 8
devbox: true
devboxfile: Tooltip-devbox.md
published: true
categories:
  - 셀 구성요소
tags: ['Tooltip']
---

컬럼의 헤더및 데이터 영역에서 마우스 hovering시 툴팁을 표시할 수 있습니다.

<script>
  var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
    dataProvider.setRows(data);
  }
  var onDoneDataSet = function() {
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
  }
</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="tooltipField"
  columnSet="tooltipColumn"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption1"
  styleSet="style1"

  dataSet="CustomOrders.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}

<!-- 비교하고 지우세요.
<script>
var onDoneDataSet = function() {
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
}
</script>

{ % include realgrid.html
  gridVar="gridView"
  dpVar="dataProvider"
  fieldSet="tooltipField"
  columnSet="tooltipColumn"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption1"
  doneDataSet="onDoneDataSet"
  styleSet="style1"
  dataSet="CustomOrders"
  gridId="realgrid"
  gridWidth="100%"
  gridHeight="300px" % } -->
