---
layout: page
title: 마스크 편집기
order: 8
devbox: true
devboxfile: MaskEditor-devbox.md
published: true
categories:
  - 그리드 편집
tags: ['editor','mask']
---

텍스트와 날짜 필드의 편집기에 마스크를 적용할 수 있습니다. 

<script>
  var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
    dataProvider.setRows(data);
  }
  var onDoneDataSet = function() {
    gridView.setColumnProperty("time","displayRegExp", /^([0-9]{2})([0-9]{2})([0-9]{2})$/)
    gridView.setColumnProperty("time","displayReplace", "$1:$2:$3")
  }
</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="maskEditorFields"
  columnSet="maskEditorColumns"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption1"
  styleSet="style1"

  dataSet="MaskEditorData.json"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}