---
layout: page
title: 트리뷰 Lazy Loading 구현
order: 7
devbox: true
devboxfile: TreeLazyLoading_devbox.md
published: true
categories:
  - 트리뷰(TreeView)
tags: ['트리', 'Tree']
---

트리뷰(TreeView)에서 Lazy Loading(지연된 로드, 레이지 로딩)은 트리의 노드가 펼쳐질때 자식 노드를
추가 하는 방식으로 구현할 수 있습니다.

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
