---
layout: page
title: 문자 입력 제한
order: 13
devbox: true
devboxfile: LineCellEditor-devbox.md
published: true
categories:
  - 그리드 편집
tags: ['editing', '편집', '편집기', 'editor',]
---

inputCharacters, ignoreCharacters속성으로 특정 문자들만 입력받거나 특정 문자들만 제한할 수 있습니다.

<script>
  var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
    var datas = [
      ["VINET","10248","한글입력"],
      ["VINET","10248","한글입력"],
      ["VINET","10248","한글입력"],
      ["VINET","10248","한글입력"],
      ["VINET","10248","한글입력"],
      ["VINET","10248","한글입력"],
      ["VINET","10248","한글입력"],
      ["VINET","10248","한글입력"],
      ["VINET","10248","한글입력"],
      ["VINET","10248","한글입력"]
    ]
    dataProvider.setRows(datas)
  }

  var onDoneDataSet = function() {
  }
</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="DefaultField"
  columnSet="lineCellEditorColumns"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="DefaultGridOption"
  styleSet="style1"

  dataSet="DefaultDataSet.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}