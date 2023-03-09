---
layout: page
title: 행 그룹핑 이벤트
order: 6
devbox: true
devboxfile: RowGroupEvent-devbox.md
published: true
categories:
  - 행 그룹
tags: ['grouping', '그룹', 'event', 'onExpanded', 'onCollapsed', 'onExpanding', 'onCollapsing']
---

행 그룹핑의 접거나 펼칠때 발생하는 이벤트들을 모아놓은 페이지입니다.

<script>
var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
  dataProvider.setRows(data);
}
var onDoneDataSet = function() {
  var events = 0;

  gridView.setPanel({"visible": true})
  gridView.groupBy(["Country","CompanyName","OrderID"]);
  gridView.onExpanded = function(grid, model) {
     addLog("onExpanded: {type:" + model.type + ", itemIndex: " + model.itemIndex + ", level: "+ model.level + "}");
  };
  gridView.onExpanding = function(grid, model) {
       addLog("onExpanding: {type:" + model.type + ", itemIndex: " + model.itemIndex + ", level: "+ model.level + "}");
  };
  gridView.onCollapsed = function(grid, model) {
       addLog("onCollapsed: {type:" + model.type + ", itemIndex: " + model.itemIndex + ", level: "+ model.level + "}");
  };
  gridView.onCollapsing = function(grid, model) {
       addLog("onCollapsing: {type:" + model.type + ", itemIndex: " + model.itemIndex + ", level: "+ model.level + "}");
  };

  $('#btnClearTextaea').click(function() {
      events = 0;
      $("#eventLog").val('');
  });

  function addLog(log) {
    var prevLog = $("#eventLog").val();
    $("#eventLog").val(prevLog + "[" + events++ + "] " + log + "\n");
    $("#eventLog").scrollTop($("#eventLog")[0].scrollHeight);
  }; 
}
</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="rowGroupingField"
  columnSet="rowGroupingColumn"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption1"
  styleSet="style1"

  dataSet="CustomOrders.json"
  successDataSet="onGridSuccessDataSet"  
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}

<a class="btn secondary small round lowercase" id="btnClearTextaea">지우기</a>
<textarea id="eventLog" style="width:100%; height:200px; border: 2px solid #5d8cc9"></textarea>