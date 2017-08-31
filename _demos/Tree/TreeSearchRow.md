---
layout: page
title: 트리뷰 노드 검색하기
order: 12
devbox: true
devboxfile: TreeSearchRow_devbox.md
published: true
categories:
  - 트리뷰(TreeView)
tags: ['트리', 'Tree', 'search']
---


<script>
  var onSuccessDataSet = function(data, textStatus, jqXHR) {
    treeDataProvider.setRows(data, "tree", true, "", "icon");
  }

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

하나 이상의 필드에 대해 행 단위 검색을 할 수 있습니다.


{% include realtree.html
  treeVar="treeView"
  dpVar="treeDataProvider"
  treeId="realtree"

  fieldSet="treeFieldset1"
  columnSet="treeColumnset1"
  dpOptionSet="treeDataProviderOption1"
  treeOptionSet="treeOption1"
  styleSet="treeStyle1"

  dataSet="treedata1.json"
  successDataSet="onSuccessDataSet"
  doneDataSet="onDoneDataSet"

  showToolbox="true"
  treeWidth="100%"
  treeHeight="300px" %}
