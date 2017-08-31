---
layout: page
title: CSS Styles
order: 6
published: true
devbox: true
devboxfile: CSSStyles_devbox.md
categories:
  - 그리드 스타일
tags: ['style', '스타일', 'css', '씨에스에스']
---

RealGridJS 1.1.17.2245 버전부터 Popup, DropDown, Date 에디터에서 CSS 스타일을 적용할 수 있습니다.
ContextMenu는 PopupMenu와 CSS 스타일을 공유 합니다.
그리드에서 마우스 오른쪽 버튼을 클릭하여 ContextMenu 스타일을 확인하세요.

<style type="text/css">
    /*                  */
    /*      Progress    */
    /*                  */
    .rg-progress {
        background-color: rgba(0, 111, 245, 0.05);
        border: 1px solid #d0f;
    }
    .rg-progress-bar {
        background : linear-gradient(#aaa, #ccc);
        border : 1px solid #d00;
    }
    .rg-progress-progress {
        background : linear-gradient(#fff, #f3d);
        border-right : 1px solid #ff0;
    }
    .rg-progress-message {
        font-size : 11px;
        font-family : Tahoma;
        font-weight : bold;
    }
    /*                  */
    /*      Filter      */
    /*                  */
    .rg-filterselector {
        background : rgb(233, 233, 233);
        border :1px solid rgb(200, 200, 200);
        box-shadow :rgba(0, 0, 0, 0.8) 1px 2px 5px;
        font-family :"나눔고딕코딩";
        font-style :normal;
        font-variant :normal;
        font-weight :normal;
        font-size :10pt;
        padding :4px;
    }
    .rg-filter-actions {
    }
    .rg-filter-action-item {
    } 
    .rg-filter-action-item:hover {
        text-decoration:underline;
    }
    .rg-filter-action-check {
    }
    .rg-filter-action-label {
    }
    .rg-filter-all {
        background-color : rgba(45, 164, 164, 1);
        color : #E0E0E0;
    }
    .rg-filter-all-check {
    }
    .rg-filter-all-label {
    }
    .rg-filter-all-hr {
    }
    .rg-filter-items {
    }
    .rg-filter-item {
        color: white;
        background-color: #151500;
    }
    .rg-filter-item:hover {
        text-decoration:underline;
    }
    .rg-filter-item-check {
    }
    .rg-filter-item-label {
    }
    /*                  */
    /*    MultiCheck    */
    /*                  */
    .rg-filterselector {
        background : rgb(233, 233, 233);
        border :1px solid rgb(200, 200, 200);
        box-shadow :rgba(0, 0, 0, 0.8) 1px 2px 5px;
        font-family :"나눔고딕코딩";
        font-style :normal;
        font-variant :normal;
        font-weight :normal;
        font-size :10pt;
        padding :4px;
    }
    .rg-filter-actions {
    }
    .rg-filter-action-item {
    } 
    .rg-filter-action-item:hover {
        text-decoration:underline;
    }
    .rg-filter-action-check {
    }
    .rg-filter-action-label {
    }
    .rg-filter-all {
        background-color : rgba(45, 164, 164, 1);
        color : #E0E0E0;
    }
    .rg-filter-all-check {
    }
    .rg-filter-all-label {
    }
    .rg-filter-all-hr {
    }
    .rg-filter-items {
    }
    .rg-filter-item {
        color: white;
        background-color: #151500;
    }
    .rg-filter-item:hover {
        text-decoration:underline;
    }
    .rg-filter-item-check {
    }
    .rg-filter-item-label {
    }
    /*                  */
    /*    MultiCheck    */
    /*                  */
    .rg-multicheck {
        background: #fff;
        border: 1px solid rgb(50, 50, 50);
        box-shadow: rgba(0, 0, 0, 0.8) 1px 2px 5px;
        font-family: 나눔고딕코딩;
        font-style: normal;
        font-variant: normal;
        font-weight: normal;
        font-size: 12pt;
        padding: 0px;
        margin: 0px;
    }
    .rg-multicheck-button {
        text-align: center;
    }
    .rg-multicheck-accept {
        border: 1px solid #0a3c59;
        border-radius: 3px;
        color: #06426c;
        border-width: 1px; 
    }
    .rg-multicheck-cancel {
        border: 1px solid #0a3c59;
        border-radius: 3px;
        color: #06426c;
        border-width: 1px; 
    }
    .rg-multicheck-accept:hover {
        background-color: #888
    }
    .rg-multicheck-cancel:hover {
        background-color: #888
    }
    .rg-multicheck-select {
        background:#40ff0b;
        color:#ffffff;
    }
    .rg-multicheck-list {
    }
    .rg-multicheck-item {
        background:none;
        color:none;
    }
    .rg-multicheck-item:hover {
        background:rgba(0, 0, 255, 0.2);
        color:none;
    }
    .rg-multicheck-selectitem {
        background:rgba(0, 0, 255, 0.2);
        color:#000;
    }.rg-multicheck {
        background: #fff;
        border: 1px solid rgb(50, 50, 50);
        box-shadow: rgba(0, 0, 0, 0.8) 1px 2px 5px;
        font-family: 나눔고딕코딩;
        font-style: normal;
        font-variant: normal;
        font-weight: normal;
        font-size: 12pt;
        padding: 0px;
        margin: 0px;
    }
    .rg-multicheck-button {
        text-align: center;
    }
    .rg-multicheck-accept {
        border: 1px solid #0a3c59;
        border-radius: 3px;
        color: #06426c;
        border-width: 1px; 
    }
    .rg-multicheck-cancel {
        border: 1px solid #0a3c59;
        border-radius: 3px;
        color: #06426c;
        border-width: 1px; 
    }
    .rg-multicheck-accept:hover {
        background-color: #888
    }
    .rg-multicheck-cancel:hover {
        background-color: #888
    }
    .rg-multicheck-select {
        background:#40ff0b;
        color:#ffffff;
    }
    .rg-multicheck-list {
    }
    .rg-multicheck-item {
        background:none;
        color:none;
    }
    .rg-multicheck-item:hover {
        background:rgba(0, 0, 255, 0.2);
        color:none;
    }
    .rg-multicheck-selectitem {
        background:rgba(0, 0, 255, 0.2);
        color:#000;
    }
 
    /*              */
    /*    Popup     */
    /*              */
    .rg-popup-menu {
        background: #ffeeb6;
        border: 1px solid rgb(200, 200, 200);
        box-shadow: rgba(0, 0, 0, 0.8) 1px 2px 5px;
        font-family: 나눔고딕코딩;
        font-style: normal;
        font-variant: normal;
        font-weight: normal;
        font-size: 10pt;
        padding: 4px;
        margin: 0px;
    }
 
    .rg-popup-item {
        padding-top: 2px;
        padding-bottom: 2px;
        height: 20px;
        cursor: pointer;
    }
 
    .rg-popup-item:hover {
        background-color: #ffd8d8;
    }
 
    .rg-popup-separator-hr {
        height: 1px;
        border: 0px;
        margin: 2px;
        color: #777;
        background-color: #777;
    }
 
    .rg-popup-expander {
        background-image: url("/resource/image/icon/menu_expander.png");
        background-repeat: no-repeat;
        background-position: center center;
    }
 
    .rg-popup-check {
        /*
        background-image:url("/resource/image/icon/menu_uncheck.png");
        background-repeat : no-repeat;
        background-position : center center;
        */
    }
 
    .rg-popup-check-checked {
        background-image: url("/resource/image/icon/menu_check.png");
        background-repeat: no-repeat;
        background-position: center center;
    }
 
    .rg-popup-radio {
        /*
        background-image:url("/resource/image/icon/menu_unradio.png");
        background-repeat : no-repeat;
        background-position : center center;
        */
    }
 
    .rg-popup-radio-checked {
        background-image: url("/resource/image/icon/menu_radio.png");
        background-repeat: no-repeat;
        background-position: center center;
    }
 
    .rg-popup-group1 {
        background: #ffd800;
    }
 
    /*              */
    /*    date      */
    /*              */
    .rg-calendar {
        font-family: "나눔고딕코딩";
        font-size: 12px;
        background: #fff;
        border: 1px solid rgba(50, 50, 50, 1);
        box-shadow: rgba(0, 0, 0, 0.8) 1px 2px 5px;
    }
 
    .rg-cal-header {
        height: 20px;
    }
 
    .rg-cal-year {
        cursor: default;
        top: 2px;
    }
 
    .rg-cal-month {
        cursor: pointer;
        top: 2px;
    }
 
    .rg-cal-prev-month {
        background-image: url("/resource/image/icon/cal_prev.png");
        width: 20px;
        height: 20px;
    }
 
    .rg-cal-prev-month:hover {
        background-image: url("/resource/image/icon/cal_prev_hover.png");
    }
 
    .rg-cal-prev-month:active {
        background-image: url("/resource/image/icon/cal_prev_active.png");
    }
 
    .rg-cal-next-month {
        background-image: url("/resource/image/icon/cal_next.png");
        width: 20px;
        height: 20px;
    }
 
    .rg-cal-next-month:hover {
        background-image: url("/resource/image/icon/cal_next_hover.png");
    }
 
    .rg-cal-next-month:active {
        background-image: url("/resource/image/icon/cal_next_active.png");
    }
 
    .rg-cal-today-button {
        font-size: 12px;
        font-family: "나눔고딕코딩";
        border: 1px solid transparent;
        border-radius: 3px;
        cursor: pointer;
    }
 
    .rg-cal-today-button:hover {
        border: 1px solid #aaa;
        background-color: #fff;
        text-decoration: underline;
    }
 
    .rg-cal-today-button:active {
    }
 
    .rg-cal-next-year {
        background-image: url("/resource/image/icon/cal_up.png");
    }
 
    .rg-cal-next-year:hover {
        background-image: url("/resource/image/icon/cal_up_hover.png");
    }
 
    .rg-cal-next-year:active {
        background-image: url("/resource/image/icon/cal_up_active.png");
    }
 
    .rg-cal-prev-year {
        background-image: url("/resource/image/icon/cal_down.png");
    }
 
    .rg-cal-prev-year:hover {
        background-image: url("/resource/image/icon/cal_down_hover.png");
    }
 
    .rg-cal-prev-year:active {
        background-image: url("/resource/image/icon/cal_down_active.png");
    }
 
    .rg-cal-weeks {
        color: black;
        font-size: 12px;
        font-family: "나눔고딕코딩";
        cursor: default;
    }
 
    .rg-cal-week-sun {
        color: red;
    }
 
    .rg-cal-week-sat {
        color: blue;
    }
 
    .rg-cal-days {
        font-family: "나눔고딕코딩";
        font-size: 12px;
        text-align: center;
    }
 
    .rg-cal-day {
        cursor: pointer;
        background: #f5f5f5;
        border: 1px solid #eee;
        width: 30px;
        height: 30px;
        border-radius: 7px;
        font-family: "나눔고딕코딩";
        font-size: 12px;
    }
 
    .rg-cal-day:hover {
        background: #55FFf5;
        color: red;
        border: 1px solid #eee;
    }
 
    .rg-cal-prev-day {
        color: #ccc;
        border: 1px solid #fff;
    }
 
    .rg-cal-next-day {
        color: #ccc;
        border: 1px solid #fff;
    }
 
    .rg-cal-today {
        background: #d5d5d5;
    }
 
    .rg-cal-focusday {
        background: rgba(255, 255, 0, 0.3);
        border: 1px solid #aaa;
        color: #333;
    }
 
    .rg-cal-month-picker {
        margin: 0px;
        cursor: pointer;
        background: #fff;
        border: 1px solid rgba(50, 50, 50, 0.5);
        box-shadow: rgba(0, 0, 0, 0.5) 1px 2px 5px;
        font-family: "나눔고딕코딩";
        font-size: 12px;
        font-style: normal;
        font-variant: normal;
        font-weight: normal;
    }
 
    .rg-cal-month-picker-month {
        padding: 1px 4px 1px 4px;
        width: 20px;
        height: 20px;
        border-radius: 7px;
        text-align: center;
    }
 
    .rg-cal-month-picker-month:hover {
        background: #e8e8e8;
    }
 
    /*              */
    /*   dropDown   */
    /*              */
    .rg-dropdownlist {
        background: #fff;
        font-family: 나눔고딕코딩;
        border: 1px solid rgb(50, 50, 50);
        box-shadow: rgba(0, 0, 0, 0.8) 1px 2px 5px;
        font-size: 10pt;
        padding: 0px;
        margin: 0px;
    }
 
    .rg-dropdown-select {
        background: #fffa00;
        margin: 2px;
    }
 
    .rg-dropdown-item {
        margin: 2px;
    }
 
    .rg-dropdown-item:hover {
        background: #88ff88;
    }
</style>
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

  //popup
  var onDoneDataSet = function() {
    var menu = [{
        label: "menu1 입니다.",
        enabled: true,
        children: [{
            label: "submenu1 입니다."
        }, {
            label: "submenu2 입니다."
        }]
    }, {
        label: "menu2 입니다",
        enabled: true
    }, {
        label: "-"
    }, {
        label: "menu3 입니다",
        type: "check",
        checked: true,
        tag: "check_menu"
    }, {
        label: "group menu",
        children: [{
            label: "group1 - 첫번째",
            type: "radio",
            group: "group1",
            checked: true
        }, {
            label: "group1 - 두번째",
            type: "radio",
            group: "group1"
        }, {
            label: "group1 - 세번째",
            type: "radio",
            group: "group1"
        }]
    }];
    gridView.addPopupMenu("menu1", menu);

    gridView.onMenuItemClicked = function (grid, data, index) {
        var s = data.label + (data.checked ? " checked" : "");
        if (data.tag)
            s += "n" + "tag: " + data.tag;
        alert(s);
    };

    // context
    gridView.setContextMenu([{
        label: "Menu1"
    }, {
        label: "Menu2"
    }, {
        label: "-" // menu separator를 삽입합니다.
    }, {
        label: "ExcelExport"
    }]);
 
    gridView.onContextMenuItemClicked = function (grid, label, index) {
        alert("Context menu가 클릭됐습니다: " + label.label + "\n" + JSON.stringify(index));
        if (label.label == "ExcelExport") {
            grid.exportGrid({
                type: "excel",
                target: "local",
                showConfirm: false,
                linear: true    // Expand all columns and Export
            });
        };
    };

    gridView.setEditOptions({
        insertable: true,
        appendable: true,
        updatable: true,
        checkDiff: true,
        checkCellDiff: true,
        enterToTab: false
    });
 
    gridView.setEditorOptions({
        //useCssStyle: true,      //모든 에디터에 CSS를 적용할 경우 사용  
        useCssStyleDropDownList: true,
        useCssStyleDatePicker: true,
        useCssStylePopupMenu: true,
        useCssStyleMultiCheck: true
         
    });
 
    gridView.setFilteringOptions({selector: {useCssStyle: true}});  
  }
</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="CSSStylesFields"
  columnSet="CSSStylesColumns"
  dpOptionSet="dataProviderOption1"  
  styleSet="style1"

  dataSet="CustomOrders.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}
