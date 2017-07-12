---
layout: page
title: Excel - TreeView
order: 6
devbox: true
devboxfile: ExcelTreeView_devbox.md
published: true
categories:
  - 엑셀 내보내기
tags: ['excel', 'export', 'tree']
---

현재 트리에 표시된 컬럼 구조대로 데이터셋을 엑셀 파일로 변환해서 로컬파일로 저장합니다.

<script>
  var onSuccessDataSet = function(data, textStatus, jqXHR) {
    treeDataProvider.fillCsvData(
      data,
      {
        tree: "tree",
        icon: "icon",
        children: "childrenField",
        quoted: true,
        start: 0
      }
    );
  }

  var onDoneDataSet = function() {

  }
</script>

{% include realtree.html
  treeVar="treeView"
  dpVar="treeDataProvider"
  treeId="realtree"

  fieldSet="treeFieldset5"
  columnSet="treeColumnset1"
  dpOptionSet="treeDataProviderOption1"
  treeOptionSet="treeOption1"
  styleSet="treeStyle1"

  dataSet="treedata5.txt"
  successDataSet="onSuccessDataSet"
  doneDataSet="onDoneDataSet"

  showToolbox="true"
  treeWidth="100%"
  treeHeight="300px" %}