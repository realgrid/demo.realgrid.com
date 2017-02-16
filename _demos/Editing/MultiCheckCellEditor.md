---
layout: page
title: 동시선택 편집기
order: 10
devbox: true
devboxfile: MultiCheckCellEditor-devbox.md
published: true
categories:
  - 그리드 편집
tags: ['editing', '편집', '편집기', 'editor', 'multi', 'check']
---

MultiCheckCellEditor는 DropDownList에서 여러 항목들을 선택할 수 있는 Editor입니다. 

<script>
  var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
    var datas = [{
        "OrderID": "10248", "CustomerID": "VINET", "EmployeeID": "5", "OrderDate": "1996-07-03T15:00:00.000Z", "CompanyName": "Vins et alcools Chevalier\r\n", "Country": "FR,KR,JP", "Phone": "26.47.15.10", "ProductName": "Queso Cabrales", "QuantityPerUnit": "1 kg pkg.", "Quantity": 1200, "UnitPrice": 14
    }, {
        "OrderID": "10248", "CustomerID": "VINET", "EmployeeID": "5", "OrderDate": "1996-07-03T15:00:00.000Z", "CompanyName": "Vins et alcools Chevalier\r\n", "Country": "KR,FR", "Phone": "26.47.15.10", "ProductName": "Singaporean Hokkien Fried Mee", "QuantityPerUnit": "32 - 1 kg pkgs.", "Quantity": 10, "UnitPrice": 9.8
    }, {
        "OrderID": "10248", "CustomerID": "VINET", "EmployeeID": "5", "OrderDate": "1996-07-03T15:00:00.000Z", "CompanyName": "Vins et alcools Chevalier\r\n", "Country": "DE,FR", "Phone": "26.47.15.10", "ProductName": "Mozzarella di Giovanni", "QuantityPerUnit": "24 - 200 g pkgs.", "Quantity": 5, "UnitPrice": 34.8
    }, {
        "OrderID": "10249", "CustomerID": "TOMSP", "EmployeeID": "6", "OrderDate": "1996-07-04T15:00:00.000Z", "CompanyName": "Toms Spezialitäten", "Country": "DE,US,UK", "Phone": "0251-031259", "ProductName": "Tofu", "QuantityPerUnit": "40 - 100 g pkgs.", "Quantity": 9, "UnitPrice": 18.6
    }, {
        "OrderID": "10249", "CustomerID": "TOMSP", "EmployeeID": "6", "OrderDate": "1996-07-04T15:00:00.000Z", "CompanyName": "Toms Spezialitäten", "Country": "DE", "Phone": "0251-031259", "ProductName": "Manjimup Dried Apples", "QuantityPerUnit": "50 - 300 g pkgs.", "Quantity": 1004, "UnitPrice": 42.4
    }, {
        "OrderID": "10250", "CustomerID": "HANAR", "EmployeeID": "4", "OrderDate": "1996-07-07T15:00:00.000Z", "CompanyName": "Hanari Carnes", "Country": "KR,BE,CH,BR,FR,JP,CN", "Phone": "(21) 555-0091", "ProductName": "Jack's New England Clam Chowder", "QuantityPerUnit": "12 - 12 oz cans", "Quantity": 10, "UnitPrice": 7.7
    }, {
        "OrderID": "10250", "CustomerID": "HANAR", "EmployeeID": "4", "OrderDate": "1996-07-07T15:00:00.000Z", "CompanyName": "Hanari Carnes", "Country": "BR", "Phone": "(21) 555-0091", "ProductName": "Manjimup Dried Apples", "QuantityPerUnit": "50 - 300 g pkgs.", "Quantity": 35, "UnitPrice": 42.4
    }, {
        "OrderID": "10250", "CustomerID": "HANAR", "EmployeeID": "4", "OrderDate": "1996-07-07T15:00:00.000Z", "CompanyName": "Hanari Carnes", "Country": "BR", "Phone": "(21) 555-0091", "ProductName": "Louisiana Fiery Hot Pepper Sauce", "QuantityPerUnit": "32 - 8 oz bottles", "Quantity": 15, "UnitPrice": 16.8
    }, {
        "OrderID": "10251", "CustomerID": "VICTE", "EmployeeID": "3", "OrderDate": "1996-07-07T15:00:00.000Z", "CompanyName": "Victuailles en stock", "Country": "FR", "Phone": "78.32.54.86", "ProductName": "Gustaf's Knäckebröd", "QuantityPerUnit": "24 - 500 g pkgs.", "Quantity": 6, "UnitPrice": 16.8
    }, {
        "OrderID": "10251", "CustomerID": "VICTE", "EmployeeID": "3", "OrderDate": "1996-07-07T15:00:00.000Z", "CompanyName": "Victuailles en stock", "Country": "FR", "Phone": "78.32.54.86", "ProductName": "Ravioli Angelo", "QuantityPerUnit": "24 - 250 g pkgs.", "Quantity": 15, "UnitPrice": 15.6
    }, {
        "OrderID": "10251", "CustomerID": "VICTE", "EmployeeID": "3", "OrderDate": "1996-07-07T15:00:00.000Z", "CompanyName": "Victuailles en stock", "Country": "FR", "Phone": "78.32.54.86", "ProductName": "Louisiana Fiery Hot Pepper Sauce", "QuantityPerUnit": "32 - 8 oz bottles", "Quantity": 20, "UnitPrice": 16.8
    }, {
        "OrderID": "10252", "CustomerID": "SUPRD", "EmployeeID": "4", "OrderDate": "1996-07-08T15:00:00.000Z", "CompanyName": "Suprêmes délices", "Country": "BE", "Phone": "(071) 23 67 22 20", "ProductName": "Sir Rodney's Marmalade", "QuantityPerUnit": "30 gift boxes", "Quantity": 40, "UnitPrice": 64.8
    }, {
        "OrderID": "10252", "CustomerID": "SUPRD", "EmployeeID": "4", "OrderDate": "1996-07-08T15:00:00.000Z", "CompanyName": "Suprêmes délices", "Country": "BE,CN", "Phone": "(071) 23 67 22 20", "ProductName": "Geitost", "QuantityPerUnit": "500 g", "Quantity": 25, "UnitPrice": 2
    }, {
        "OrderID": "10252", "CustomerID": "SUPRD", "EmployeeID": "4", "OrderDate": "1996-07-08T15:00:00.000Z", "CompanyName": "Suprêmes délices", "Country": "BE", "Phone": "(071) 23 67 22 20", "ProductName": "Camembert Pierrot", "QuantityPerUnit": "15 - 300 g rounds", "Quantity": 40, "UnitPrice": 27.2
    }, {
        "OrderID": "10253", "CustomerID": "HANAR", "EmployeeID": "3", "OrderDate": "1996-07-09T15:00:00.000Z", "CompanyName": "Hanari Carnes", "Country": "SG,AE,BR", "Phone": "(21) 555-0091", "ProductName": "Gorgonzola Telino", "QuantityPerUnit": "12 - 100 g pkgs", "Quantity": 20, "UnitPrice": 10
    }, {
        "OrderID": "10253", "CustomerID": "HANAR", "EmployeeID": "3", "OrderDate": "1996-07-09T15:00:00.000Z", "CompanyName": "Hanari Carnes", "Country": "BR", "Phone": "(21) 555-0091", "ProductName": "Chartreuse verte", "QuantityPerUnit": "750 cc per bottle", "Quantity": 42, "UnitPrice": 14.4
    }, {
        "OrderID": "10253", "CustomerID": "HANAR", "EmployeeID": "3", "OrderDate": "1996-07-09T15:00:00.000Z", "CompanyName": "Hanari Carnes", "Country": "SG,BR", "Phone": "(21) 555-0091", "ProductName": "Maxilaku", "QuantityPerUnit": "24 - 50 g pkgs.", "Quantity": 40, "UnitPrice": 16
    }, {
        "OrderID": "10254", "CustomerID": "CHOPS", "EmployeeID": "5", "OrderDate": "1996-07-10T15:00:00.000Z", "CompanyName": "Chop-suey Chinese", "Country": "CH", "Phone": "0452-076545", "ProductName": "Guaraná Fantástica", "QuantityPerUnit": "12 - 355 ml cans", "Quantity": 15, "UnitPrice": 3.6
    }, {
        "OrderID": "10254", "CustomerID": "CHOPS", "EmployeeID": "5", "OrderDate": "1996-07-10T15:00:00.000Z", "CompanyName": "Chop-suey Chinese", "Country": "AE,FR,CH", "Phone": "0452-076545", "ProductName": "Pâté chinois", "QuantityPerUnit": "24 boxes x 2 pies", "Quantity": 21, "UnitPrice": 19.2
    }, {
        "OrderID": "10254", "CustomerID": "CHOPS", "EmployeeID": "5", "OrderDate": "1996-07-10T15:00:00.000Z", "CompanyName": "Chop-suey Chinese", "Country": "CH", "Phone": "0452-076545", "ProductName": "Longlife Tofu", "QuantityPerUnit": "5 kg pkg.", "Quantity": 21, "UnitPrice": 8
    }]
 
    dataProvider.setRows(datas);
  }
  var onDoneDataSet = function() {


  }
</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="multiCheckFields"
  columnSet="multiCheckColumns"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption_Editors"
  styleSet="style1"

  dataSet="DefaultDataSet.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}