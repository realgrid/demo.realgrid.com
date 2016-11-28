---
layout: page
title: 트리뷰의 특별한 체크박스
order: 9
devbox: true
devboxfile: TreeCheckBox_devbox.md
published: true
categories:
  - 트리뷰(TreeView)
tags: ['트리', 'Tree']
---


`트리뷰(TreeView)`는 `그리드뷰(GridView)`와 마찬가지로 [체크바(CheckBar)]({{ '/GridComponent/CheckBar/' | prepend: site.baseurl }})를 이용해 노드(행)을 선택할 수 있습니다.
`트리뷰(TreeView)`는 체크바 대신 조금 특별한 `체크박스(CheckBox)`를 표시할 수 있습니다.

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
