---
layout: page
title: jQuery ajax() 이용하기
order: 6
devbox: true
devboxfile: TreeJQueryAjax_devbox.md
published: true
categories:
  - 트리뷰(TreeView)
tags: ['트리', 'Tree']
---

[jQuery.ajax()](http://api.jquery.com/jquery.ajax/)는 비동기 HTTP 통신을 위한 함수 입니다.
이 함수를 이용해 비동기로 그리드뷰(GridView) 또는 트리뷰(TreeView)에 원격의 데이터를 가져올 수 있습니다.


<script>
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

    treeDataProvider.clearRows();

  }
</script>

{% include realtree.html
  treeVar="treeView"
  dpVar="treeDataProvider"
  fieldSet="treeFieldset3"
  columnSet="treeColumnset3"
  dpOptionSet="treeDataProviderOption1"
  treeOptionSet="treeOption1"
  styleSet="treeStyle1"
  dataSet="treedata3"
  doneDataSet="onDoneDataSet"
  treeId="realtree"
  treeDataFunc="setJsonRows"
  treeField="rows"
  childrenField=""
  iconField="icon"
  showToolbox="true"
  treeWidth="100%"
  treeHeight="300px" %}
