---
layout: page
title: 마스터 디테일 예
order: 10
devbox: true
devboxfile: MasterDetailSample_devbox.md
published: true
categories:
  - 데이터 가져오기
tags: ['filldata', 'sample', 'master', 'detail']
---

간단하게 구현한 Master, Detail 화면입니다.

<script>
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


var onGridSuccessDataSetDetail = function(data, textStatus, jqXHR) {
	setMasterOptions(dpMain, mainGrid);  
	setMasterCallback();
	dpMain.setRows(masterData);
	setDetailOptions(dpDetail, detailGrid);
	setDetailCallback();
}


function setMasterCallback() {
    mainGrid.onCurrentRowChanged = function (grid, oldRow, newRow) {
        //console.log("mainGrid.onCurrentRowChanged");
 
        var isNew = (newRow < 0) || dpMain.getRowState(newRow) === "created";
 
        // 최초 입력시에만 수정가능하도록
        if (!RealGridJS.isMobile())
            grid.setColumnProperty("OrderID", "editable", isNew);
        detailControl(newRow);
    };
 
    mainGrid.onEditCommit = function (grid, index, oldValue, newValue) {
 
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
        //console.log("Master Rows삭제: " + rows);
        detailControl(mainGrid.getCurrent().dataRow);
    };
    dpMain.onRowDeleted = function (provider, row) {
        //master 레코드 삭제 처리
        //console.log("Master Row삭제: " + row);
        detailControl(mainGrid.getCurrent().dataRow);
    };
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
 

 
function onbtnMasterSave(event) {
	//console.log("저장")
    mainGrid.commit();
    //마스터 저장 생략.
    dpMain.clearRowStates();
};
 
function onbtnMasterAdd(event) {
    var row = dpMain.addRow({});
    mainGrid.setCurrent({ dataRow: row })
    mainGrid.setFocus();
};

function setGridStyles() {
    var skins = {
        selection:{
            background:"#50ffd400", 
            border:"#ffffd400,1px"
        },
        body:{
            background:"#fffafbfc",
            foreground:"#ff000000"
        },
        header:{
            background:"linear,#ffe4f2fb,#ffddeefa,90",
            fontBold:"true"
        },
        indicator:{
            background:"#d8ecfa",
            foreground:"#ff3a85ba"
        }
    };

    mainGrid.setStyles(skins);

    detailGrid.setStyles(skins);
}


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
        //console.log("Detail Row삭제: " + row);
    };
};

///detail
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
	console.log("저장")
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

</script>


<a class="btn primary small round lowercase" id="btnMasterSave" onclick="onbtnMasterSave();">저장</a>

{% include realgrid.html

  gridVar="mainGrid"
  dpVar="dpMain"
  gridId="main"

  fieldSet="setMasterFields"
  columnSet="setMasterColumns"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="DefaultGridOption"
  styleSet="style1"

  gridWidth="100%"
  gridHeight="300px" %}

<a class="btn primary small round lowercase" id="btnDetailSave" onclick="onbtnDetailSave()">저장</a>

{% include realgrid.html

  gridVar="detailGrid"
  dpVar="dpDetail"
  gridId="detail"

  fieldSet="setDetailFields"
  columnSet="setDetailColumns"
  styleSet="style1"

  dataSet="firRowHeightData.json"
  successDataSet="onGridSuccessDataSetDetail"

  gridWidth="100%"
  gridHeight="300px" %}