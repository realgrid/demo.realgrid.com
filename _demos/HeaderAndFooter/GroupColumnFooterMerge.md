---
layout: page
title: 그룹컬럼 푸터 병합
order: 9
devbox: true
devboxfile: GroupColumnFooterMerge_devbox.md
published: true
categories:
  - 헤더와 푸터
tags: ['footer', 'merge', '푸터', '병합', '머지']
---

Footer의 경우 병합할 컬럼들을 array형태로 지정하여 병합할 수 있습니다. 병합 셀이 하나일 때 1차원 배열, 병합 셀이 여러개일 때 2차원 배열로 지정합니다. 이 때 배열의 0번째 에 있는 컬럼의 footer내용이 병합된 셀의 표시됩니다.


<script>
  var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
    dataProvider.setRows(data);
  }
  var onDoneDataSet = function() {
  	gridView.setStyles({
        header: {
            group: {
                background: "linear,#ffe9f0f8,#ffc3f8d8,90",
                foreground: "#ff666666"
            }
        }
    });	
    
    gridView.setColumnProperty("OrderID", "footer", {text: "OrderID", styles:{textAlignment:"center"}})
    gridView.setColumnProperty("CustomerID", "footer", {text: "CustomerID", styles:{textAlignment:"center"}})
    gridView.setColumnProperty("EmployeeID", "footer", {text: "EmployeeID", styles:{textAlignment:"center"}})
  }
</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="DefaultField"
  columnSet="ColumnGroupingColumn"
  dpOptionSet="DefaultDataProviderOption"
  gridOptionSet="DefaultGridOption"
  styleSet="style1"

  dataSet="CustomOrders.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}