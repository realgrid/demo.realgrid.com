---
layout: page
title: 트리 구현 - Array 데이터
order: 2
devbox: true
devboxfile: TreeArrayDataSet_devbox.md
categories:
  - 트리뷰(TreeView)
tags: ['트리', 'Tree']
---

트리뷰(TreeView)를 구현하기 위해 `배열형(Array) 데이터`를 사용할 수 있습니다.
`배열형(Array) 데이터`의 구조와 트리 구현 방법을 오른쪽 devbox에서 확인할 수 있습니다.

{% include realtree.html
  treeVar="treeView"
  dpVar="treeDataProvider"
  fieldSet="treeFieldset2"
  columnSet="treeColumnset2"
  dpOptionSet="treeDataProviderOption1"
  treeOptionSet="treeOption1"
  styleSet="treeStyle1"
  treeId="realtree"
  treeField="tree"
  needSorting="true"
  childrenField=""
  iconField="icon"
  showToolbox="true"
  treeWidth="100%"
  treeHeight="300px" %}
