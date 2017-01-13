#### 이벤트 확인하기

그리드의 각 영역을 클릭하여 결과를 확인하시기 바랍니다.

checkBar.head 에 "v" 표시 여부를 지정합니다.

CheckBar Header의 전체선택 Checkbox 표시여부에 따라 클릭 시 발생하는 이벤트가 달라집니다.

<a class="btn primary small round lowercase" id="btn">showAll 보이기/숨기기</a>

```js
var checked;
if (gridView.getCheckBar().showAll){
    checked = false;
}else{
    checked = true;
}

gridView.setCheckBar({
    showAll: checked
});
```

#### 클릭, 더블클릭 이벤트

현재 데모에 적용된 `클릭`, `더블클릭` 이벤트들입니다.

```js
gridView.onColumnHeaderClicked = function (grid, column) {
    addLog("onColumnHeaderClicked: " + "(" + column.name + ")");
};
gridView.onColumnHeaderDblClicked = function (grid, column) {
    addLog("onColumnHeaderDblClicked: " + "(" + column.name + ")");
};
gridView.onColumnCheckedChanged = function (grid, column, checked) {
    addLog("onColumnCheckedChanged: " + "(" + column.name + ", " + checked + ")");
};
gridView.onDataCellClicked = function (grid, index) {
    addLog("onDataCellClicked: " + JSON.stringify(index));
};
gridView.onDataCellDblClicked = function (grid, index) {
    addLog("onDataCellDblClicked: " + JSON.stringify(index));
};
gridView.onFooterCellClicked = function (grid, column) {
    addLog("onFooterCellClicked : " + "(" + column.name + ")");
};
gridView.onFooterCellDblClicked = function (grid, column) {
    addLog("onFooterCellDblClicked : " + "(" + column.name + ")");
};
gridView.onItemChecked = function (grid, itemIndex, checked) {
    addLog("onItemChecked: " + itemIndex + ", " + checked);
};
gridView.onItemsChecked = function (grid, items, checked) {
    addLog("onItemsChecked: " + items + ", " + checked);
};
gridView.onItemAllChecked = function (grid, checked) {
    addLog("onItemAllChecked: " + checked);
};
gridView.onCheckBarHeadClicked = function (grid) {
    addLog("onCheckBarHeadClicked");
};
gridView.onCheckBarFootClicked = function (grid) {
    addLog("onCheckBarFootClicked");
};
gridView.onIndicatorCellClicked = function (grid, index) {
    addLog("onIndicatorCellClicked : " + "(" + index + ")");
};
gridView.onStateBarCellClicked = function (grid, index) {
    addLog("onStateBarCellClicked : " + "(" + index + ")");
};
gridView.onRowGroupHeadClicked = function (grid) {
    addLog("onRowGroupHeadClicked");
};
gridView.onRowGroupFootClicked = function (grid) {
    addLog("onRowGroupFootClicked");
};
gridView.onRowGroupHeaderFooterClicked = function (grid, index) {
    addLog("onRowGroupHeaderFooterClicked : " + "(" + index + ")");
};
gridView.onRowGroupBarClicked = function (grid, index) {
    addLog("onRowGroupBarClicked : " + "(" + index + ")");
};
gridView.onCheckBarFootDblClicked = function (grid) {
    addLog("onCheckBarFootDblClicked");
};
gridView.onIndicatorCellDblClicked = function (grid, index) {
    addLog("onIndicatorCellDblClicked : " + "(" + index + ")");
};
gridView.onStateBarCellDblClicked = function (grid, index) {
    addLog("onStateBarCellDblClicked : " + "(" + index + ")");
};
gridView.onRowGroupHeadDblClicked = function (grid) {
    addLog("onRowGroupHeadDblClicked");
};
gridView.onRowGroupFootDblClicked = function (grid) {
    addLog("onRowGroupFootDblClicked");
};
gridView.onRowGroupHeaderFooterDblClicked = function (grid, index) {
    addLog("onRowGroupHeaderFooterDblClicked : " + "(" + index + ")");
};
gridView.onRowGroupBarDblClicked = function (grid, index) {
    addLog("onRowGroupBarDblClicked : " + "(" + index + ")");
};
gridView.onPanelClicked = function (grid, index) {
    addLog("onPanelClicked : " + "(" + index + ")");
};
gridView.onPanelDblClicked = function (grid, index) {
    addLog("onPanelDblClicked : " + "(" + index + ")");
};
gridView.onRowGroupPanelClicked = function (grid, column) {
    addLog("onRowGroupPanelClicked : " + "(" + column.name + ")");
};
gridView.onRowGroupPanelDblClicked = function (grid, column) {
    addLog("onRowGroupPanelDblClicked : " + "(" + column.name + ")");
};
```

<script>
$('#btn').click(function() {
	var checked;
	if (gridView.getCheckBar().showAll){
		checked = false;
	}else{
		checked = true;
	}

	gridView.setCheckBar({
        showAll: checked
    });
});
</script>