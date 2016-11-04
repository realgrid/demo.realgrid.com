---
layout: page
title: 트리뷰 데이터 모델
order: 1
devbox: true
devboxfile: TreeDataModel_devbox.md
categories:
  - 트리뷰(TreeView)
tags: ['트리', 'Tree']
---

데이터의 계층구조를 표현하기 위해 `트리뷰(TreeView)` 객체를 이용하여 트리(Tree)와 그리드(Grid)를 동시에 표현 할 수 있습니다.


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

<p></p>
