---
layout: page
title: 셀 버튼
order: 2
devbox: true
devboxfile: CellButton-dbox.md
categories:
  - 셀 구성요소
tags: ['CellButton', 'button']
--- 

<script>
	var onDoneDataSet = function() {
		gridView.setDisplayOptions({rowHeight:30})

		var menu = [{
	        label: "menu1 입니다."
	    }, {
	        label: "menu2 입니다."
	    }, {
	        label: "menu3 입니다."
	    }];
	    gridView.addPopupMenu("customerPopup", menu);

	    gridView.onMenuItemClicked = function (grid, data) {
	        alert(data.label);
	    };

		gridView.onCellButtonClicked = function (grid, itemIndex, column) {
	        alert("CellButton Clicked: itemIndex=" + itemIndex + ", fieldName=" + column.fieldName);
	    };
 
    	gridView.onImageButtonClicked = function (grid, itemIndex, column, buttonIndex, name) {
	        alert("onImageButtonClicked: " + itemIndex + ", " + column.name+", " + buttonIndex + ", " + name);
	    };
	}
</script>

셀 버튼은 `action`, `popup`, `image` 중 하나로 지정할 수 있습니다.  

<p></p>
{% include realgrid.html
  gridVar="gridView"
  dpVar="dataProvider"
  fieldSet="cellButtonField"
  columnSet="cellButtonColumn"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption1"
  doneDataSet="onDoneDataSet"
  styleSet="style1"
  dataSet="griddata1"
  gridId="realgrid"
  gridWidth="100%"
  gridHeight="300px" %}