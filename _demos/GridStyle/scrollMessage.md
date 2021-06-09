---
layout: page
title: scrollMessage
order: 13
published: true
devbox: true
devboxfile: scrollMessage_devbox.md
categories:
  - 그리드 스타일
tags: ['style', '스타일', 'css', '씨에스에스', '스크롤', 'scroll']
---

RealGridJS 1.1.35 버전부터 setDisplayOptions.liveScroll 이 false일 때
scrollBar의 thumb를 마우스로 이동시 위치정보를 표시하는 view가 그리드 오른쪽 상단에 표시할 수 있습니다.

<style type="text/css">
.rg-scroll-tip-view {
  border: 1px solid red;
  background: white;
  font-size: 12px;
  white-space: nowrap;
  border-radius: 4px;
}
</style>
<script>
  var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
    dataProvider.setRows(data);
        
    gridView.setDisplayOptions({
        liveScroll: false,
        scrollMessageCallback:function(grid, vertical, itemIndex) {
            console.log(itemIndex)
            if (vertical === "vertical") {
                var dataRow = grid.getDataRow(itemIndex); 
                if (dataRow >= 0) {
                    return "<span style='color:red'>"+ (itemIndex + 1) +"</span>"
                }
            }
        }
    });
  }

  var onDoneDataSet = function() {
    
  }
  
</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="indicatorField"
  columnSet="indicatorColumn"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption_indicator"
  styleSet="style1"

  dataSet="CustomOrders.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}
