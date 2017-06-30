#### 이벤트 확인하기

Current를 [Enter] 나 [Tab] Key, 화살표 Key를 이용하여 변경하거나, 데이터를 `입력` / `수정` / `삭제` 해보면서 각 Event들이 어떤 순서로 발생하는지 확인해보세요.

※ `삽입` : 원하는 위치에서 [ctrl] + [insert] key   
※ `추가` : 맨 마지막 행에서 [↓] key(down arrow)   
※ `삭제` : [ctrl] + [Del] key 

#### 적용된 추가/수정/삭제 이벤트들

현재 데모에 적용된 `추가`/`수정`/`삭제` 이벤트들입니다.

```js
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
// 추가하지 못하게 하려면 string 메시지나 boolean false를 리턴합니다.
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

gridView.onRowsPasted =  function (grid, items) {
    addLog("grid.onRowsPasted" + items);
};

gridView.onEditRowPasted = function(grid, itemIndex, dataRow, fields, oldValues, newValues){
    var text = "grid.onEditRowPasted : itemIndex = "+itemIndex+", oldValues = "+ oldValues.toString() +", newValues = "+newValues.toString();
    addLog(text);
};

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
// 연속된 행들이 삭제되지 않았을 수 있으므로 이벤트르 제공합니다.
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
```