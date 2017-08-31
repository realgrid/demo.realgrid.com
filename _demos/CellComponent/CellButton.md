---
layout: page
title: 셀 버튼
order: 2
devbox: true
devboxfile: CellButton-devbox.md
published: true
categories:
  - 셀 구성요소
tags: ['CellButton', 'button', '버튼']
---

셀 버튼은 `action`, `popup`, `image` 중 하나로 지정할 수 있습니다.

<script>
  var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
    dataProvider.setRows(data);
  }
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

    var imageButtons1 = [{
      "name": "팝업버튼",
      "up": "/resource/image/btnImages/popup_normal.png",
      "hover": "/resource/image/btnImages/popup_hover.png",
      "down": "/resource/image/btnImages/popup_click.png",
      "width":50
    }];
    var imageButtons2 = [{
      "name": "조회버튼",
      "up": "/resource/image/btnImages/search_normal.png",
      "hover": "/resource/image/btnImages/search_hover.png",
      "down": "/resource/image/btnImages/search_click.png",
      "width":50
    }];
    gridView.addCellRenderers([{
     "id":"buttons1",
     "type":"imageButtons",
     "images": imageButtons1,
     "margin":10
     },{
     "id":"buttons2",
     "type":"imageButtons",
     "images": imageButtons2,
     "margin":10
    }]);

    gridView.onImageButtonClicked = function (grid, itemIndex, column, buttonIndex, name) {
        alert("onImageButtonClicked: " + itemIndex + ", " + column.name+", " + buttonIndex + ", " + name);
    };

    var data = ["팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회","팝업","조회"]

    for(var i = 0; i < data.length; i++){
      dataProvider.setValue(i,"ImageButton",data[i])
    }
  }
</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="cellButtonField"
  columnSet="cellButtonColumn"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption1"
  styleSet="style1"

  dataSet="griddata1.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}
