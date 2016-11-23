---
layout: page
title: 트리뷰 아이콘 컨트롤하기
order: 10
devbox: true
devboxfile: TreeIcons_devbox.md
categories:
  - 트리뷰(TreeView)
tags: ['트리', 'Tree']
---

`트리뷰(TreeView)`에는 트리컬럼의 왼쪽에 노드마다 서로 다른 아이콘을 표시할 수 있습니다.
또, 아이콘 필드의 값을 변경 하면 노드의 `펼쳐짐`, `접힘`상태에 따라 다른 아이콘을 표시할 수도 있습니다.

<script>
  var onDoneDataSet = function() {
    var imageList = new RealGridJS.ImageList("images", "{{"/resource/image/smallflag/" | prepend: site.baseurl}}");
    imageList.addUrls([
                "icon_male.png",
                "icon_female.png",
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
