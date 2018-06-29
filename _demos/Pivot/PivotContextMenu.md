---
layout: page
title: 피벗 컨텍스트 메뉴
order: 10
devbox: true
devboxfile: PivotContextMenu_devbox.md
published: true
categories:
  - 피벗(RealPivot)
tags: ['pivot', 'contextMenu']
---

피벗 왼쪽 상단의 메뉴 아이콘 클릭 시 contextMenu에 설정한 메뉴를 표시합니다.

<link rel="stylesheet" type="text/css" href="/lib/realpivot/realpivot_eval.0.9.0/css/default_blue.css">
<link rel="stylesheet" type="text/css" href="/lib/css/pivot_demo.css">
<script type="text/javascript" src="/lib/jquery/jquery-1.11.2.min.js"></script>
<script type="text/javascript" src="/lib/realgrid/realgridjs-lic.js"></script>  
<script type="text/javascript" src="/lib/realgrid/realgridjs_eval.1.1.27/realgridjs_eval.1.1.27.min.js"></script>
<script type="text/javascript" src="/lib/realgrid/realgridjs_eval.1.1.27/realgridjs-api.1.1.27.js"></script>
<script type="text/javascript" src="/lib/realpivot/realpivot_eval.1.0.0/messages/realpivot-messages.js"></script>
<script type="text/javascript" src="/lib/realpivot/realpivot_eval.1.0.0/realpivot_eval.1.0.0.min.js"></script>


<script>
var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
    dataProvider.setRows(data);
    pivot.drawView();
}
var onDoneDataSet = function() {

}

var onSuccessColumnSet = function(data, textStatus, jqXHR) {
}  

</script>

{% include realpivot.html

  pivotVar="pivot"
  dpVar="dataProvider"
  pivotId="realpivot"

  fieldSet="pivotContextMenu_setFields"
  fieldMappingSet="pivotContextMenu_fieldMapping"
  pivotFieldsSet="pivotContextMenu_pivotFields"

  dataSet="pivotDataSet.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  pivotWidth="100%"
  pivotHeight="500px" %}