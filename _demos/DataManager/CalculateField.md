---
layout: page
title: 계산 필드
order: 10
devbox: true
devboxfile: CalculateField-devbox.md
published: true
categories:
  - 데이터 관리
tags: ['data', 'calcfield', '계산']
---

다른 필드값에 의해 자동으로 값이 계산되는 Calculate Field는 DataField.calculateExpression과 calculateCallback로 구현할 수 있습니다.  
예제 화면의 `PriceTotal`컬럼은 `calculateExpression`으로 `Discounted`컬럼은 `calculateCallback`방식으로 구현하였습니다.

<script>

var onDoneDataSet = function() {
	var fields = [{
    "fieldName": "OrderID",
    "dataType": "number"
}, {
    "fieldName": "CustomerID"
}, {
    "fieldName": "EmployeeID"
}, {
    "fieldName": "OrderDate",
    "dataType": "datetime"
}, {
    "fieldName": "CompanyName"
}, {
    "fieldName": "ProductName"
}, {
    "fieldName": "Quantity",
    "dataType": "number"
}, {
    "fieldName": "UnitPrice",
    "dataType": "number"
}, {
    "fieldName": "PriceTotal",
    "dataType": "number",
    "calculateExpression": "values['Quantity'] * values['UnitPrice']"
}, {
    "fieldName": "Discounted",
    "dataType": "number",
    "calculateCallback": function (dataRow, fieldName, fieldNames, values) {
        var quantity = values[fieldNames.indexOf("Quantity")];
        var unitprice = values[fieldNames.indexOf("UnitPrice")];
        if (isNaN(quantity) || isNaN(unitprice))
            return undefined;
        else
            return quantity >= 1000 ? Math.round(quantity * unitprice * 0.95) : quantity * unitprice;
    }
}]

dataProvider.setFields(fields);

$.getJSON("/demo/resource/data/calculateFieldData.json", function (data) {
        dataProvider.setRows(data);
    })
    .done(function () {
        gridView.setFocus();
    })
    .fail(function (jqxhr, textStatus, error) {
        var err = textStatus + ', ' + error;
        console && console.log("jQuery getJSON() Failed: " + err);
        alert("jQuery getJSON() Failed: " + err);
    });

}
</script>


{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="calculateField_setFields"
  columnSet="calculateField_setColumns"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption1"
  styleSet="style1"

  dataSet="calculateFieldData.json"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}