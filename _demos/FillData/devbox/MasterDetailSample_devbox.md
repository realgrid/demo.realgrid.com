#### Master, Detail 설정

Master의 key는 `"OrderID"`이며, Detail의 key는 `"OrderID"`,`"ProductName"` 입니다.  
Detail의 "OrderID" 는 저장시 자동으로 입력되도록 코딩되어 있습니다.  
소스에서 dpDetail.onRowInserting를 확인하시기 바랍니다.

- `삽입/추가`: 원하는 위치에서 [ctrl] + [insert] key or 맨 마지막 행에서 [↓] key(down arrow) 
- `삭제`: [ctrl] + [Del] key, Master의 경우 바로 삭제, Detail의 경우 softDeleting이 적용되었습니다.

```js
var mainGrid, detailGrid, dpMain, dpDetail;
 
var masterData = [
    ["10248", "VINET", "Vins et alcools Chevalier", "5", "1996-07-04", "Vins et alcools Chevalier", "59 rue de l'Abbaye", "Reims", "France"],
    ["10249", "TOMSP", "Toms Spezialitäten", "6", "1996-07-05", "Toms Spezialitäten", "Luisenstr. 48", "Münster", "Germany"],
    ["10250", "HANAR", "Hanari Carnes", "4", "1996-07-08", "Hanari Carnes", "Rua do Paço, 67", "Rio de Janeiro", "Brazil"],
    ["10251", "VICTE", "Victuailles en stock", "3", "1996-07-08", "Victuailles en stock", "2, rue du Commerce", "Lyon", "France"],
    ["10252", "SUPRD", "Suprêmes délices", "4", "1996-07-09", "Suprêmes délices", "Boulevard Tirou, 255", "Charleroi", "Belgium"],
    ["10253", "HANAR", "Hanari Carnes", "3", "1996-07-10", "Hanari Carnes", "Rua do Paço, 67", "Rio de Janeiro", "Brazil"]
];
 
var detailData = [
    { OrderID: 10248, ProductName: "Queso Cabrales", UnitPrice: 14, Quantity: 12 },
    { OrderID: 10248, ProductName: "Singaporean Hokkien Fried Mee", UnitPrice: 9.8, Quantity: 10 },
    { OrderID: 10248, ProductName: "Mozzarella di Giovanni", UnitPrice: 34.8, Quantity: 5 },
    { OrderID: 10249, ProductName: "Tofu", UnitPrice: 18.6, Quantity: 9 },
    { OrderID: 10249, ProductName: "Manjimup Dried Apples", UnitPrice: 42.4, Quantity: 40 },
    { OrderID: 10250, ProductName: "Jack's New England Clam Chowder", UnitPrice: 7.7, Quantity: 10 },
    { OrderID: 10250, ProductName: "Manjimup Dried Apples", UnitPrice: 42.4, Quantity: 35 },
    { OrderID: 10250, ProductName: "Louisiana Fiery Hot Pepper Sauce", UnitPrice: 16.8, Quantity: 15 },
    { OrderID: 10251, ProductName: "Gustaf's Knäckebröd", UnitPrice: 16.8, Quantity: 6 },
    { OrderID: 10251, ProductName: "Ravioli Angelo", UnitPrice: 15.6, Quantity: 15 },
    { OrderID: 10251, ProductName: "Louisiana Fiery Hot Pepper Sauce", UnitPrice: 16.8, Quantity: 20 },
    { OrderID: 10252, ProductName: "Sir Rodney's Marmalade", UnitPrice: 64.8, Quantity: 40 },
    { OrderID: 10252, ProductName: "Geitost", UnitPrice: 2, Quantity: 25 },
    { OrderID: 10252, ProductName: "Camembert Pierrot", UnitPrice: 27.2, Quantity: 40 },
    { OrderID: 10253, ProductName: "Gorgonzola Telino", UnitPrice: 10, Quantity: 20 },
    { OrderID: 10253, ProductName: "Chartreuse verte", UnitPrice: 14.4, Quantity: 42 }
];
 
$(function () {
    $("#btnMasterSave").click(onbtnMasterSave);
    $("#btnDetailSave").click(onbtnDetailSave);
 
    RealGridJS.setTrace(false);
    RealGridJS.setRootContext("/img/realgridjs");
 
    // Master 
    dpMain = new RealGridJS.LocalDataProvider();
    mainGrid = new RealGridJS.GridView("mainGrid");
    mainGrid.setDataProvider(dpMain);
 
    setMasterField(dpMain);
    setMasterColumn(mainGrid);
    setMasterOptions(dpMain, mainGrid);   
    setMasterCallback();
 
    // detail
    dpDetail = new RealGridJS.LocalDataProvider();
    detailGrid = new RealGridJS.GridView("detailGrid");
    detailGrid.setDataProvider(dpDetail);
 
    setDetailField(dpDetail);
    setDetailColumn(detailGrid);
    setDetailOptions(dpDetail, detailGrid);
    setDetailCallback();
 
    dpMain.setRows(masterData);
    mainGrid.setCurrent({ itemIndex: 0 });
});
 
function setMasterCallback() {
    mainGrid.onCurrentRowChanged = function (grid, oldRow, newRow) {
        console.log("mainGrid.onCurrentRowChanged");
 
        var isNew = (newRow < 0) || dpMain.getRowState(newRow) === "created";
 
        // 최초 입력시에만 수정가능하도록
        if (!RealGridJS.isMobile())
            grid.setColumnProperty("OrderID", "editable", isNew);
        detailControl(newRow);
    };
    mainGrid.onCurrentChanging = function (grid, oldIndex, newIndex) {
        // detail을 확인해서 수정중이거나. 수정후 저장된것이 있으면 종료..
        if (oldIndex.itemIndex != newIndex.itemIndex && !chkDetail()) {
            return false;
        }
    };
    mainGrid.onSorting = function (grid) {
        if (!chkDetail()) {
            return false;
        }
    };
    mainGrid.onFiltering = function (grid) {
        if (!chkDetail()) {
            return false;
        }
    };
    mainGrid.onGrouping = function (grid) {
        if (!chkDetail()) {
            return false;
        }
    };
    dpMain.onRowsDeleted = function (provider, rows) {
        //master 레코드 삭제 처리
        console.log("Master Rows삭제: " + rows);
        detailControl(mainGrid.getCurrent().dataRow);
    };
    dpMain.onRowDeleted = function (provider, row) {
        //master 레코드 삭제 처리
        console.log("Master Row삭제: " + row);
        detailControl(mainGrid.getCurrent().dataRow);
    };
};
 
function setDetailCallback() {
    detailGrid.onCurrentRowChanged = function (grid, oldRow, newRow) {
        var isNew = (newRow < 0) || dpMain.getRowState(newRow) === "created";
 
        // 최초 입력시에만 수정가능하도록
        if (!RealGridJS.isMobile()) {
            grid.setColumnProperty("OrderID", "editable", isNew);
            grid.setColumnProperty("ProductName", "editable", isNew);
        }
    };
    detailGrid.onRowInserting = function (grid, itemIndex, dataRow) {
        if (mainGrid.isItemEditing() || dpMain.getRowStateCount("all") > 0) {
 
            return "마스터를 저장해야 합니다.";
        };
    };
    dpDetail.onRowInserting = function (provider, row, values) {
        var idx = dpDetail.getFieldIndex("OrderID");
        var OrderID = mainGrid.getValue(mainGrid.getCurrent().itemIndex, "OrderID");
 
        values[idx] = OrderID;
    };
    dpDetail.onRowDeleted = function (provider, row) {
        console.log("Detail Row삭제: " + row);
    };
};
 
function setMasterField(provider) {
    var fields = [
        ...
    ];

    provider.setFields(fields);
};
function setMasterColumn(grid) {
    var columns = [
        ...
    ];
 
    grid.setColumns(columns);
};
 
function setMasterOptions(provider, grid) {
    provider.setOptions({
        restoreMode: "auto"
    });
 
    grid.setOptions({
        edit: {
            insertable: true,
            appendable: true,
            deletable: true,
            upateable: true,
            commitWhenExitLast: true,
            crossWhenExitLast: true,
            enterToTab: true,
        },
        sort: {
            keepFocusedRow: true
        },
        footer: {
            visible: false
        }
    })
};
 
function setDetailField(provider) {
    var fields = [
        ...
    ];

    provider.setFields(fields);

};
function setDetailColumn(grid) {
    // OrderID는 자동으로 입력됨, ProductName의 경우 신규만 가능, 수정은 불가능하게 처리.
    var columns = [
        ...
    ];
 
    grid.setColumns(columns);
};
 
function setDetailOptions(provider, grid) {
    provider.setOptions({ softDeleting: true });
    grid.setOptions({
        edit: {
            insertable: true,
            appendable: true,
            deletable: true,
            upateable: true,
            commitWhenExitLast: true,
            enterToTab: true,
        }
    })
};
 
function detailControl(masterRow) {
    dpDetail.clearRows();
 
    if (masterRow >= 0) {
        var mstKey = dpMain.getValue(masterRow, "OrderID");
 
        // detailData 배열에서 자료추출. DB대용
        var datas = detailData.filter(function (element) {
            if (element.OrderID === mstKey) {
                return true;
            }
        });
 
        dpDetail.setRows(datas);
    };
};
 
function chkDetail() {
    if (detailGrid.isItemEditing() || dpDetail.getRowStateCount("*") > 0) {
        alert("Detail을 저장해야 합니다");
        return false;
    };
    return true;
};
 
function onbtnDetailSave(evt) {
    detailGrid.commit();
 
    var states = dpDetail.getAllStateRows();
 
    if (states.created.length > 0) {
        // 생성
        for (var i = 0; i < states.created.length; i++) {
            detailData.push(dpDetail.getJsonRow(states.created[i]));
            dpDetail.setRowState(states.created[i], "none");
        }
    };
    if (states.updated.length > 0) {
        // 수정인 경우
        for (var i = 0; i < states.updated.length; i++) {
            var orderId = dpDetail.getValue(states.updated[i], "OrderID");
            var productName = dpDetail.getValue(states.updated[i], "ProductName");
            var rowData = dpDetail.getJsonRow(states.updated[i]);
 
            for (var j = 0; j < detailData.length - 1; j++) {
                if ((orderId == detailData[j].OrderID) && (productName == detailData[j].ProductName)) {
                    detailData.splice(j, 1, rowData);
                    dpDetail.setRowState(states.updated[i], "none");
                    break;
                }
            }
        }
    };
    if (states.deleted.length > 0) {
        // 삭제 softDelete인경우
        for (var i = 0; i < states.deleted.length; i++) {
            var orderId = dpDetail.getJsonRow(states.deleted[i]).OrderID;
            var productName = dpDetail.getJsonRow(states.deleted[i]).ProductName;
 
            for (var j = 0; j < detailData.length - 1; j++) {
                if ((orderId == detailData[j].OrderID) && (productName == detailData[j].ProductName)) {
                    detailData.splice(j, 1);
                    break;
                }
            }
        }
 
        dpDetail.clearRowStates(true, true);
    };
    if (states.createAndDeleted.length > 0) {
        // 생성후 삭제.
        dpDetail.clearRowStates(true);
    };
};
 
function onbtnMasterSave(event) {
    mainGrid.commit();
    //마스터 저장 생략.
    dpMain.clearRowStates();
};
 
function onbtnMasterAdd(event) {
    var row = dpMain.addRow({});
    mainGrid.setCurrent({ dataRow: row })
    mainGrid.setFocus();
};
```