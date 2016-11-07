---
layout: page
title: 트리뷰 노드 조작하기
order: 7
devbox: true
devboxfile: TreeNodeControl_devbox.md
categories:
  - 트리뷰(TreeView)
tags: ['트리', 'Tree']
---


<script>
  var onDoneDataSet = function() {
    var imgFiles = [
                  "kr.png",
                  "br.png",
                  "fr.png",
                  "mx.png",
                  "pt.png",
                  "es.png",
                  "gb.png",
                  "us.png",
                  "ve.png"
      ];
      var imageList = new RealGridJS.ImageList("images", "{{"/resource/image/smallflag/" | prepend: site.baseurl}}");

      imageList.addUrls(imgFiles);
      treeView.registerImageList(imageList);

      treeView.setTreeOptions({
          iconImages: imageList.getName(),
          iconWidth: 20
      });
  }
</script>

RealGrid의 트리뷰(TreeView)는 트리 노드를 조작하기 위해 다양한 API를 제공하고 있습니다.
접기, 펼치기는 물론, [RowId](http://help.realgrid.com/tutorial/a9/)를 이용해
부모 자식간 노드를 이동하거나 자식 노드의 개수를 알 수 있는 함수도 있습니다.

{% include realtree.html
  treeVar="treeView"
  dpVar="treeDataProvider"
  fieldSet="treeFieldset1"
  columnSet="treeColumnset1"
  dpOptionSet="treeDataProviderOption1"
  treeOptionSet="treeOption1"
  styleSet="treeStyle1"
  dataSet="treedata1"
  doneDataSet="onDoneDataSet"
  treeId="realtree"
  treeField="tree"
  needSorting="true"
  childrenField=""
  iconField="icon"
  showToolbox="true"
  treeWidth="100%"
  treeHeight="300px" %}
