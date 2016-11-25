---
layout: page
title: 셀 버튼
order: 2
devbox: true
devboxfile: CellButton-devbox.md
published: true
categories:
  - 셀 구성요소
tags: ['CellButton', 'button']
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

      gridView.onImageButtonClicked = function (grid, itemIndex, column, buttonIndex, name) {
          alert("onImageButtonClicked: " + itemIndex + ", " + column.name+", " + buttonIndex + ", " + name);
      };
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

<!-- 비교해 보고 나중에 지우세요.
  include realgrid.html
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
  gridHeight="300px"
-->
