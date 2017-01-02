---
layout: page
title: 컬럼 레이아웃
order: 4
devbox: true
devboxfile: ColumnLayout-devbox.md
published: true
categories:
  - 컬럼
tags: ['Layout', '레이아웃']
---

그리드의 setColumns() 호출로 컬럼 셋을 설정한 후 실행 시간에 컬럼 셋을 변경하고 싶다면, 다시 setColumns()를 호출할 수 있습니다. 하지만, 최초 설정된 컬럼셋의 일부를 표시하거나, 그룹핑을 다시 하거나, 배치를 변경하고자 하는 경우, setColumns()를 다시 호출하지 않고 기존 컬럼 셋을 활용해서 컬럼들의 배치만을 재설정할 수 있습니다.

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
    
  }

</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="DefaultField"
  columnSet="ColumnLayoutColumn"
  dpOptionSet="DefaultDataProviderOption"
  gridOptionSet="DefaultGridOption"
  styleSet="style1"

  dataSet="CustomOrders.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" 
%}