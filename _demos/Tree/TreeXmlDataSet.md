---
layout: page
title: 트리 구현 - XML 데이터
order: 4
devbox: true
devboxfile: TreeXmlDataSet_devbox.md
categories:
  - 트리뷰(TreeView)
tags: ['트리', 'Tree']
---

트리뷰(TreeView)를 구현하기 위해 `XML 데이터`를 사용할 수 있습니다.
XML 데이터의 구조와 [TreeDataProvider.setXmlRows()](http://help.realgrid.com/api/TreeDataProvider/setXmlRows/)함수를 사용하여 트리뷰(TreeView)를 구현하는 샘플 코드를 살펴보세요.

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
