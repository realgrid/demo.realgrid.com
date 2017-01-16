---
layout: page
title: Region Events
order: 6
devbox: true
devboxfile: RegionEvents_devbox.md
published: true
categories:
  - 이벤트
tags: ['event', '이벤트']
---

RealGrid의 각 영역이 클릭, 더블클릭되었을때 발생하는 콜백을 확인해보는 페이지입니다.

<script>
var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
	dataProvider.setRows(data);
}

var onDoneDataSet = function() {
	var events = 0;

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

    function addLog(log) {
	    var prevLog = $("#eventLog").val();
	    $("#eventLog").val(prevLog + "[" + events++ + "] " + log + "\n");
	    $("#eventLog").scrollTop($("#eventLog")[0].scrollHeight);
	};

	gridView.setPanel({"visible": true})
    
    gridView.setStyles({
        header: {
            group: {
                background: "linear,#ffe9f0f8,#ffc3f8d8,90",
                foreground: "#ff666666"
            }
        }
    });
    $('#btnClearTextaea').click(function() {
        events = 0;
        $("#eventLog").val('');
    });
}

</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="eventOrderFields"
  columnSet="regionEventsColumns"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption1"
  styleSet="style1"

  dataSet="CustomOrders.json"
  successDataSet="onGridSuccessDataSet"  
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}

<a class="btn secondary small round lowercase" id="btnClearTextaea">지우기</a>
<textarea id="eventLog" style="width:100%; height:200px; border: 2px solid #5d8cc9"></textarea>