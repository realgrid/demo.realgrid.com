---
layout: page
title: 데이터 정렬(Sorting)
order: 9
devbox: true
devboxfile: ColumnSorting-devbox.md
published: true
categories:
  - 컬럼
tags: ['Sorting', '소트', '소팅']
---

그리드 SortingOptions.enabled 가 true이고, 컬럼의 sortable이 true이면, 사용자는 컬럼 헤더를 클릭하여 컬럼이 참조하는 필드 값들을 기준으로 데이터셋을 정렬시킬 수 있습니다. 또한, sortingOptions.style 설정에 따라 복수 필드에 대한 정렬 방식을 지정할 수 있습니다.

<script>
  var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
    gridView.setPanel({visible: false});

    var months = ['01.jan', '02.feb', '03.mar', '04.apr', '05.may', '06.jun', '07.jul', '08.aug', '09.sep', '10.oct', '11.nov', '12.dec'];
    var days = ['0-sun', '1-mon', '2-tue', '3-wed', '4-thu', '5-fri', '6-sat'];
    var rows = [];
    for (var i = 0; i < 1000; i++) {
        var row = [];
        row.push(Math.round(2000 + Math.random() * 13));
        row.push(months[Math.floor(Math.random() * 12)]);
        row.push(months[Math.floor(Math.random() * 7)]);
        row.push(Math.round(Math.random() * 24));
        rows.push(row);
    };

    dataProvider.setRows(rows);
  }
  var onDoneDataSet = function() {
    
  }

  var onSuccessColumnSet = function(data, textStatus, jqXHR) {
    createColumnList(gridView);
  }  

</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="ColumnSortingField"
  columnSet="ColumnSortingColumn"
  dpOptionSet="DefaultDataProviderOption"
  gridOptionSet="DefaultGridOption"
  styleSet="style1"

  dataSet="CustomOrders.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  successColumnSet="onSuccessColumnSet"  

  gridWidth="100%"
  gridHeight="300px" 
%}