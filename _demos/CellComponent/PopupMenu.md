---
layout: page
title: 팝업 메뉴
order: 3
devbox: true
devboxfile: PopupMenu-devbox.md
categories:
  - 셀 구성요소
tags: ['PopupMenu', 'popup']
---

Javascript 설정으로 컬럼 셀에 팝업메뉴를 추가할 수 있습니다.

<script>
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
	        enabled: false
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
	        alert(data.label);
	    };
	}
</script>

{% include realgrid.html
  gridVar="gridView"
  dpVar="dataProvider"
  fieldSet="popupField"
  columnSet="popupColumn"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption1"
  doneDataSet="onDoneDataSet"
  styleSet="style1"
  dataSet="griddata1"
  gridId="realgrid"
  gridWidth="100%"
  gridHeight="300px" %}