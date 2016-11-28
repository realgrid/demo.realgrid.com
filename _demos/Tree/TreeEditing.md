---
layout: page
title: 트리뷰에서 추가/수정/삭제
order: 9
devbox: true
devboxfile: TreeEditing_devbox.md
published: true
categories:
  - 트리뷰(TreeView)
tags: ['트리', 'Tree']
---

`트리뷰(TreeView)`는 `그리드뷰(GridView)`처럼 `TreeDataProvider`객체의 함수들을 통해
데이터를 편집할 수 있습니다. 트리의 노드를 추가하거나 노드의 자식을 추가하는 등 
편집하는 방법을 실행해 보세요.

<script>
  var onSuccessDataSet = function(data, textStatus, jqXHR) {
    treeDataProvider.setJsonRows(data, "rows", "", "icon");

    treeView.expand(0);
    treeView.expand(1);
  }

  var onDoneDataSet = function() {
    var imageList = new RealGridJS.ImageList("images", "{{"/resource/image/smallflag/" | prepend: site.baseurl}}");
    imageList.addUrls([
                "icon_male.png",
                "icon_female.png",
                "icon_folder_col.png",
                "icon_folder_exp.png",
                "de.png",
                "gr.png",
                "hu.png",
                "is.png",
                "eg.png",
                "au.png",
                "nz.png",
                "ph.png",
                "sg.png",
                "th.png",
                "tr.png",
                "ca.png",
                "mx.png",
                "us.png",
                "bo.png",
                "cr.png",
                "pe.png",
                "uy.png"
        ]
    );
 
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
  treeId="realtree"

  fieldSet="treeFieldset3"
  columnSet="treeColumnset3"
  dpOptionSet="treeDataProviderOption1"
  treeOptionSet="treeOption1"
  styleSet="treeStyle1"

  dataSet="treedata3.json"
  successDataSet="onSuccessDataSet"
  doneDataSet="onDoneDataSet"

  showToolbox="true"
  treeWidth="100%"
  treeHeight="300px" %}
