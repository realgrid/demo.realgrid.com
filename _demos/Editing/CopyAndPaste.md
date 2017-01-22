---
layout: page
title: 복사하기 / 붙여넣기
order: 9
devbox: true
devboxfile: CopyAndPaste-devbox.md
published: true
categories:
  - 그리드 편집
tags: ['editing', '편집', '복사', '붙여넣기', 'copy', 'paste']
---
그리드 copyOptions나 pasteOptions의 singleMode가 false이면(기본값), 선택된 하나 이상의 셀을 클립보드로 복사하거나, 하나 이상의 셀을 구성하는 클립보드 데이터를 그리드에 붙여넣을 수 있습니다. 다만, 이런 복사/붙여넣기는 보안을 위해 사용자가 Ctrl+C 나 Ctrl+V 키를 직접 입력하는 경우에만 실행될 수 있습니다. 즉, 단축메뉴나 javascript api를 통해 실행시킬 수 없습니다.  

<script>
  var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
    dataProvider.setRows(data);

 
  }
  var onDoneDataSet = function() {
    var options = gridView.getCopyOptions();
    $("#chkSingleMode").attr("checked", options.sinlgeMode);
    $("#chkEnabled").attr("checked", options.enabled);

    var options = gridView.getPasteOptions();
    $("#chkPasteSingleMode").attr("checked", options.sinlgeMode);
    $("#chkPasteEnabled").attr("checked", options.enabled);
    $("#chkStartEdit").attr("checked", options.startEdit);
    $("#chkCommitEdit").attr("checked", options.commitEdit);
    $("#chkEnableAppend").attr("checked", options.enableAppend);
    $("#chkFillFieldDefaults").attr("checked", options.fillFieldDefaults);
    $("#chkFillColumnDefaults").attr("checked", options.fillColumnDefaults);
    $("#chkForceRowValidation").attr("checked", options.forceRowValidation);
    $("#chkForceColumnValidation").attr("checked", options.forceColumnValidation);
    $("#chkSelectionBase").attr("checked", options.selectionBase);
    $("#chkStopOnError").attr("checked", options.stopOnError);
    $("#chkNoEditEvent").attr("checked", options.noEditEvent);
    $("#chkEventEachRow").attr("checked", options.eventEachRow);
    $("#chkcheckReadOnly").attr("checked", options.checkReadOnly);
    $("#chkcheckDomainOnly").attr("checked", options.checkDomainOnly);   
  }
</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="CopyAndPasteField"
  columnSet="CopyAndPasteColumn"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption_CopyAndPaste"
  styleSet="style1"

  dataSet="DefaultDataSet.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}