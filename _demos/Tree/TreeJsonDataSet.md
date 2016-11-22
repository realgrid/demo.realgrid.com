---
layout: page
title: 트리 구현 - JSON 데이터
order: 3
devbox: true
devboxfile: TreeJsonDataSet_devbox.md
categories:
  - 트리뷰(TreeView)
tags: ['트리', 'Tree']
---


트리뷰(TreeView)를 구현하기 위해 `JSON 데이터`를 사용할 수 있습니다.
JSON 데이터의 구조와 함수를 사용해 트리뷰를 구현하는 방법을 확인하세요.

{% include realtree.html
  treeVar="treeView"
  dpVar="treeDataProvider"
  fieldSet="treeFieldset2"
  columnSet="treeColumnset2"
  dpOptionSet="treeDataProviderOption1"
  treeOptionSet="treeOption1"
  styleSet="treeStyle1"
  doneDataSet="onDoneDataSet"
  treeId="realtree"
  treeField="tree"
  needSorting="true"
  childrenField=""
  iconField="icon"
  showToolbox="true"
  treeWidth="100%"
  treeHeight="300px" %}
