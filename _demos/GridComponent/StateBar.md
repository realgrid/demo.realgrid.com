---
layout: page
title: 상태바
order: 2
devbox: true
devboxfile: stateBar-devbox.md
published: true
categories:
  - 그리드 구성요소
tags: ['StateBar', '상태', 'state', '행번호']
---

[상태바(StateBar)](http://help.realgrid.com/api/types/StateBar/)는 데이터 [행의 상태(RowState)](http://help.realgrid.com/api/types/RowState/)를 표시하는 수직 Bar입니다. <br /> 
행의 상태는 `create`, `updated`, `createAndDeleted`, `deleted`, `none` 5가지가 존재 합니다.   

<script>
  var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
    dataProvider.setRows(data);
  }
  var onDoneDataSet = function() {
  	gridView.setStyles({
        body: {
            dynamicStyles: [{
                criteria: "state = 'd'",
                styles: "background=#11000000;foreground=#ffaaaaaa"
            }, {
                criteria: "state = 'u'",
                styles: "background=#11ffff00"
            }, {
                criteria: "state = 'c'",
                styles: "background=#11ff00ff"
            }, {
                criteria: "state = 'x'",
                styles: "background=#1100ffff;foreground=#ffaaaaaa"
            }]
        }
    });

  	dataProvider.setOptions({
        softDeleting: true
    });

  	dataProvider.onRowStateChanged = function (provider, row) {
      var state = dataProvider.getRowState(row);
      console.log("row = " + row + ", state = " + state);
    }
    dataProvider.onRowStatesCleared = function (provider, row) {
      console.log("rowStates cleared.");
    }
    
  }
</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="DefaultField"
  columnSet="DefaultColumn"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption_stateBar"
  styleSet="style1"

  dataSet="DefaultDataSet.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}