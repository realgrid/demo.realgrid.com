---
layout: page
title: Event Order
order: 5
devbox: true
devboxfile: EventOrder_devbox.md
published: true
categories:
  - 이벤트
tags: ['event', '이벤트']
---

추가/수정/삭제 및 Current와 관련된 여러 Event들을 모아놓은 페이지입니다.

<script>
var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
    var events = 0;
    field = dataProvider.getFields();

    gridView.onCurrentChanging = function (grid, oldIndex, newIndex) {
        addLog("grid.onCurrentChanging: " + "(" + oldIndex.itemIndex + ", " + oldIndex.column + ") => (" + newIndex.itemIndex + ", " + newIndex.column + ")");
 
        return true;
    };
 
    gridView.onCurrentChanged = function (grid, newIndex) {
        addLog("grid.onCurrentChanged: " + "(" + newIndex.itemIndex + ", " + newIndex.column + ")");
    };
 
    gridView.onCurrentRowChanged = function (grid, oldRow, newRow) {
        addLog("grid.onCurrentRowChanged: " + "(" + oldRow + " => " + newRow + ")");
    };
 
    gridView.onRowsDeleting = function (grid, rows) {
        addLog("grid.onRowsDeleting:" + rows);
        return null;
    };
    // 추가하지 못하게 하려면 string 메시지나 boolean false를 리턴한다.
    gridView.onRowInserting = function (grid, itemIndex) {
        addLog("grid.onRowInserting:" + itemIndex);
        return null;
    };
 
    gridView.onEditChange = function (grid, index, value) {
        addLog("grid.onEditChange driven, edit value=" + value);
    };
 
    gridView.onEditCommit = function (id, index, oldValue, newValue) {
        addLog("grid.onEditCommit driven, " + oldValue + " => " + newValue);
    };
 
    gridView.onCellEdited = function (grid, itemIndex, dataRow, field) {
        var v = grid.getValue(itemIndex, field);
        addLog("grid.onCellEdited, edited value=" + v);
    };
 
    gridView.onEditRowChanged = function (grid, itemIndex, dataRow, field, oldValue, newValue) {
        var v = grid.getValue(itemIndex, field);
        addLog("grid.onEditRowChanged: " + oldValue + " => " + newValue);
    };
 
    gridView.onEditCanceled = function (grid, index) {
        addLog("grid.onEditCanceled driven, edit index=" + JSON.stringify(index));
    }
 
    gridView.onDataCellDblClicked = function (grid, index) {
        var fieldIndex = findField(field, index.fieldName);
        addLog("grid.onDataCellDblClicked, cell value=" + grid.getValue(index.itemIndex, fieldIndex));
    };
 
    gridView.onDataCellClicked = function (grid, index) {
        var fieldIndex = findField(field, index.fieldName);
        addLog("grid.onDataCellClicked, cell value=" + grid.getValue(index.itemIndex, fieldIndex));
    };
 
    var CustomerNames = ["ALFKI", "ANATR", "ANTON", "AROUT", "BERGS", "BLAUS", "BLONP", "BOLID", "BONAP", "BOTTM", "BSBEV", "CACTU", "CENTC", "CHOPS", "COMMI", "CONSH", "DRACD", "DUMON", "EASTC", "ERNSH", "FAMIA", "FISSA", "FOLIG", "FOLKO", "FRANK", "FRANR", "FRANS", "FURIB", "GALED", "GODOS", "GOURL", "GREAL", "GROSR", "HANAR", "HILAA", "HUNGC", "HUNGO", "ISLAT", "KOENE", "LACOR", "LAMAI", "LAUGB", "LAZYK", "LEHMS", "LETSS", "LILAS", "LINOD", "LONEP", "MAGAA", "MAISD", "MEREP", "MORGK", "NORTS", "OCEAN", "OLDWO", "OTTIK", "PARIS", "PERIC", "PICCO", "PRINI", "QUEDE", "QUEEN", "QUICK", "RANCH", "RATTC", "REGGC", "RICAR", "RICSU", "ROMEY", "SANTG", "SAVEA", "SEVES", "SIMOB", "SPECD", "SPLIR", "SUPRD", "THEBI", "THECR", "TOMSP", "TORTU", "TRADH", "TRAIH", "VAFFE", "VICTE", "VINET", "WANDK", "WARTH", "WELLI", "WHITC", "WILMK", "WOLZA"];
    gridView.onEditSearch = function (grid, index, text) {
        addLog("grid.onEditSearch:" + index.itemIndex + "," + index.column + ", " + text);
        var items = CustomerNames.filter(function (str) {
            return str.indexOf(text) == 0;
        });
        gridView.fillEditSearchItems(index.column, text, items);
    };
 
    gridView.onGetEditValue = function (grid, index, editResult) {
        addLog("onGetEditValue: " + JSON.stringify(editResult));
    };
 
    gridView.onSorting = function (grid, field, directions) {
        addLog("onSorting: " + JSON.stringify(field) + ", " + JSON.stringify(directions));
    };
 
    gridView.onSortingChanged = function (grid) {
        addLog("onSortingChanged");
    };
 
    gridView.onFiltering = function (grid) {
        addLog("onFiltering");
    };
 
    gridView.onFilteringChanged = function (grid) {
        addLog("onFilteringChanged");
    };
 
    gridView.onTopItemIndexChanged = function (grid, itemIndex) {
        addLog("onTopItemIndexChanged! Top " + itemIndex);
    }
 
    dataProvider.onValueChanged = function (provider, row, field) {
        addLog("dp.onValueChanged:" + row + "," + field);
    };
    dataProvider.onRowStateChanged = function (provider, row) {
        addLog("dp.onRowStateChanged:" + row);
    };
    dataProvider.onRowStatesChanged = function (provider, rows) {
        addLog("dp.onRowStatesChanged:" + rows.length + " rows");
    };
    dataProvider.onRowStatesCleared = function (provider) {
        addLog("dp.onRowStateCleared");
    };
    dataProvider.onRowCountChanged = function (provider, count) {
        addLog("dp.onRowCountChanged:" + count);
    };
    dataProvider.onRowUpdating = function (provider, row) {
        addLog("dp.onRowUpdating:" + row);
        return true;
    };
    dataProvider.onRowUpdated = function (provider, row) {
        addLog("dp.onRowUpdated:" + row);
    };
    dataProvider.onRowsUpdated = function (provider, row, count) {
        addLog("dp.onRowsUpdated:" + row + "," + count);
    };
    dataProvider.onRowInserting = function (provider, row) {
        addLog("dp.onRowInserting:" + row);
        return true;
    };
    dataProvider.onRowInserted = function (provider, row) {
        addLog("dp.onRowInserted:" + row);
    };
    dataProvider.onRowsInserted = function (provider, row, count) {
        addLog("dp.onRowsInserted:" + row + ',' + count);
    };
    dataProvider.onRowDeleting = function (provider, row) {
        addLog("dp.onRowDeleting:" + row);
        return true;
    };
    dataProvider.onRowDeleted = function (provider, row) {
        addLog("dp.onRowDeleted:" + row);
    };
    // 연속된 행들이 삭제되지 않았을 수 있으므로 이벤트르 제공한다.
    dataProvider.onRowsDeleted = function (provider, rows) {
        addLog("dp.onRowsDeleted:" + rows.length + " rows");
    };
    dataProvider.onRowMoving = function (provider, row, newRow) {
        addLog("dp.onRowMoving:" + row + "," + newRow);
        return true;
    };
    dataProvider.onRowMoved = function (provider, row, newRow) {
        addLog("dp.onRowMoved:" + row + "," + newRow);
    };
    dataProvider.onRowsMoving = function (provider, row, count, newRow) {
        addLog("dp.onRowsMoving:" + row + "," + count + "," + newRow);
        return true;
    };
    dataProvider.onRowsMoved = function (provider, row, count, newRow) {
        addLog("dp.onRowsMoved:" + row + "," + count + "," + newRow);
    };
    dataProvider.onDataChanged = function (provider) {
        addLog("dp.onDataChanged");
    } 

    function addLog(log) {
        var prevLog = $("#eventLog").val();
        $("#eventLog").val(prevLog + "[" + events++ + "] " + log + "\n");
        $("#eventLog").scrollTop($("#eventLog")[0].scrollHeight);
    };  

	  dataProvider.setRows(data);
}

var onDoneDataSet = function() {

}



function findField(field, fieldName) {
    for (var i = 0; i < field.length; i++) {
        if (field[i].orgFieldName == fieldName)
            return i;
    }
    return -1;
}

function clearTextarea() {
	events = 0;
	$("#eventLog").val('');
}
</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="eventOrderFields"
  columnSet="eventOrderColumns"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption1"
  styleSet="style1"

  dataSet="CustomOrders.json"
  successDataSet="onGridSuccessDataSet"  
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}

<input type="button" onclick="clearTextarea()" value="지우기" style="width:60px; height:20;
	background-color: #5d8cc9;
    border: none;
    color: white;
    padding: 5px 5px;
    text-align: center;
    text-decoration: none;
    display: inline-block;
    font-size: 15px;" >
<textarea id="eventLog" style="width:100%; height:200px; border: 2px solid #5d8cc9"></textarea>