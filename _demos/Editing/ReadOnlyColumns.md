---
layout: page
title: 읽기 전용 컬럼
order: 7
devbox: true
devboxfile: ReadOnlyColumns-devbox.md
published: true
categories:
  - 그리드 편집
tags: ['editing', '편집', '편집불가']
---

[DataColumn](http://help.realgrid.com/api/types/DataColumn/){:target="_blank"}의 readOnly 속성을 true로 하거나, editable을 false로 설정하면 해당 컬럼의 셀들에서는 사용자가 입력을 할 수 없게 됩니다. 또한 DataCellStyle의 편집 속성을 지정해서 특정 데이터 셀을 read-only로 지정할 수도 있습니다.
Read-Only 컬럼은 그리드 edit 옵션의 skipReadOnly가 true로 지정되면 편집 중에 방향키나 탭키로 이동할 때 건너뛰게 됩니다.


<script>
  var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
    dataProvider.setRows(data);

 
  }
  var onDoneDataSet = function() {
  }
  var onSuccessColumnSet = function(data, textStatus, jqXHR) {
    createColumnList(gridView);

    gridView.addCellStyle("style01", {
      "foreground": "#ffffffff",
      "background": "#ff333333",
      "fontSize": 13,
      "fontBold": true,
      "editable": false
    });

    gridView.addCellStyle("style02", {
      "foreground": "#ff000000",
      "background": "#ffcccccc",
      "fontSize": 13,
      "readOnly": true
    });
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

  successColumnSet="onSuccessColumnSet"

  gridWidth="100%"
  gridHeight="300px" %}