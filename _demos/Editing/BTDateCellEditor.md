---
layout: page
title: 월 선택 달력
order: 11
devbox: true
devboxfile: BTDataCellEditor_devbox.md
published: true
categories:
  - 그리드 편집
tags: ['editing', '편집', '편집기', 'editor', '달력','월']
---

기본적인 사용법은 DateCellEditor와 동일하며 bootStrap datepicker의 옵션을 입력할수 있도록 btOptions속성을 사용해서 월만 선택할 수 있도록 설정할 수 있습니다.

<script type="text/javascript" src="/lib/bootstrap/bootstrap-datepicker.js"></script>
<script type="text/javascript" src="/lib/bootstrap/bootstrap-datepicker.ko.min.js"></script>
<link rel="stylesheet" type="text/css" href="/lib/css/bootstrap-datepicker.css">
<script>
  var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
    dataProvider.setRows(data);
    var btOptions1 = {
        startView: 1,
        minViewMode: 1,
        todayBtn: "linked",
        language: "kr",
        todayHighlight: true,
        language:"ko"
    }
    gridView.setColumnProperty("OrderDate","editor",{type:"btdate", btOptions:btOptions1, datetimeFormat:"yyyy-MM", textReadOnly:true})
  }
  var onDoneDataSet = function() {
  }
</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="BTDateFields"
  columnSet="BTDateColumns"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="DefaultGridOption"
  styleSet="style1"

  dataSet="BTDateData.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}