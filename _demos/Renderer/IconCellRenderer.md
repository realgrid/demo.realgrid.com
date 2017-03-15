---
layout: page
title: 아이콘 렌더러
order: 5
devbox: true
devboxfile: IconCellRenderer_devbox.md
published: true
categories:
  - 렌더러
tags: ['렌더러', 'renderer', 'icon']
---

Icon 셀 렌더러는 컬럼에 지정된 ImageList의 이미지들 중 스타일 값 iconIndex 위치의 이미지를 텍스트와 함께 표시합니다.

<script>
var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
	dataProvider.setRows(data);
}
var onDoneDataSet = function() {
	gridView.setDisplayOptions({rowHeight:50});
  
  var imgs = new RealGridJS.ImageList("images1", "/resource/image/icon/");
    imgs.addUrls([
        "be.png",
        "br.png",
        "fr.png",
        "de.png",
        "us.png"
    ]);

  gridView.registerImageList(imgs);
  gridView.setColumnProperty("left","imageList", "images1");
  gridView.setColumnProperty("left","renderer",{type:"icon"});
  gridView.setColumnProperty("left","styles", {
      textAlignment: "near",
      iconIndex: 0,
      iconLocation: "left",
      iconAlignment: "center",
      iconOffset: 4,
      iconPadding: 4
  });
}
</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="rendererFields"
  columnSet="iconCellRendererColumns"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption1"
  styleSet="style1"

  dataSet="CustomOrders.json"
  successDataSet="onGridSuccessDataSet"  
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}