---
layout: page
title: 컨텍스트 메뉴
order: 4
devbox: true
devboxfile: contextMenu-devbox.md
published: true
categories:
  - 그리드 구성요소
tags: ['ContextMenu', '컨텍스트메뉴', '컨텍스트메뉴', '팝업', 'popup']
---

`컨텍스트메뉴(ContextMenu)`는 그리드 영역에서 마우스 오른쪽 버튼을 클릭하였을때 표시되는 메뉴를 말합니다.  

[GridView.setContextMenu()](http://help.realgrid.com/api/GridBase/setContextMenu/) 함수를 호출해서 컨텍스트 메뉴에 메뉴 항목을 추가할 수 있습니다. 
메뉴 항목 label에 "-" 문자를 지정하면 메뉴 구분선(menu separator)이 추가됩니다.
마우스 오른쪽 버튼이 클릭되면 [GridView.onContextMenuPopup()](http://help.realgrid.com/api/GridBase/onContextMenuPopup/) 이벤트에 지정된 핸들러가 실행되고 false를 리턴하면 컨텍스트 메뉴가 실행되지 않습니다.   
그리고 실행 시간에 메뉴가 클릭되면 [GridView.onContextMenuClicked()](http://help.realgrid.com/api/GridBase/onContextMenuItemClicked/) 이벤트에 지정된 핸들러가 실행됩니다.   


<script>
  var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
    dataProvider.setRows(data);
  }
  var onDoneDataSet = function() {

    
  }
</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="DefaultField"
  columnSet="DefaultColumn"
  dpOptionSet="DefaultDataProviderOption"
  gridOptionSet="DefaultGridOption"
  styleSet="style1"

  dataSet="DefaultDataSet.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}