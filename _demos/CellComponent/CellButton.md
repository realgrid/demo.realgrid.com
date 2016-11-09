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
	var doneDataSet = function() {
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

데이터 셀의 편집기 외에 버튼을 표시하고 사용자 버튼 클릭 이벤트를 이용해 추가 작업을 실행할 수 있습니다.

<p></p>
{% include realgrid.html
  gridVar="gridView"
  dpVar="dataProvider"
  fieldSet="fieldset1"
  columnSet="btnColumnset"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption1"
  doneDataSet="doneDataSet"
  styleSet="style1"
  dataSet="griddata1"
  gridId="realgrid"
  gridWidth="100%"
  gridHeight="300px" %}

Action 버튼을 클릭하면 그리드 [onCellButtonClicked](http://help.realgrid.com/api/GridBase/onCellButtonClicked/)가 발생합니다.    
Popup 버튼을 클릭하면 컬럼에 지정한 popupMenu가 표시됩니다. 메뉴에 대해서는 [Popup Menu]()를 참조하십시오.  
IMAGE 버튼을 클릭하면 그리드 [onImageButtonClicked](http://help.realgrid.com/api/GridBase/onImageButtonClicked/)가 발생합니다.