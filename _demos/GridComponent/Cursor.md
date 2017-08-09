---
layout: page
title: 커서
order: 6
published: true
categories:
  - 그리드 구성요소
tags: ['Cursor', '커서']
---

[DataColumn](http://help.realgrid.com/api/types/DataColumn/).cursor 속성에 마우스 커서를 지정할 수 있습니다. 
아래 그리드의 컬럼에 마우스 포인터를 지정하여 컬럼별로 커서가 어떻게 변하는지 확인해보세요. 

cursor에 지정할 수 있는 값은 W3C 표준(http://www.w3.org/wiki/CSS/Properties/cursor)을 준수합니다. uri 미지원 합니다.  `(Only JS Support)`

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

  fieldSet="cursorField"
  columnSet="cursorColumn"
  dpOptionSet="DefaultDataProviderOption"
  gridOptionSet="DefaultGridOption"
  styleSet="style1"

  dataSet="CursorDataSet.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}