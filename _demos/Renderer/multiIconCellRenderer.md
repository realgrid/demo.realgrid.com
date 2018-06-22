---
layout: page
title: 다중 아이콘 렌더러
order: 11
devbox: true
devboxfile: multiIconCellRenderer_devbox.md
published: true
categories:
  - 렌더러
tags: ['렌더러', 'renderer', 'icon', '다중', 아이콘]
---

multiIconCellRenderer는 여러 아이콘을 조건에 따라 이미지를 동적으로 보여줄 수 있습니다.

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
  gridView.setColumnProperty("left","header",{text: "다중 아이콘"});
  gridView.setColumnProperty("left","imageList", "images1");
  gridView.setColumnProperty("left","renderer",{
    type:"multiIcon", 
    icons: ['/resource/image/icon/be.png', '/resource/image/icon/br.png']
  });
  gridView.setColumnProperty("left","styles", {
      textAlignment: "near",
      iconIndex: 0,
      iconLocation: "left",
      iconAlignment: "center",
      iconOffset: 4,
      iconPadding: 4
  });

  gridView.setColumnProperty("OrderID","header",{text: "동적 아이콘"});
  gridView.setColumnProperty("OrderID","width",100);
  gridView.setColumnProperty("OrderID","renderer",{
            type:"multiIcon",
            renderCallback:function(grid, index) {
              var value = grid.getValue(index.itemIndex, index.fieldName);
              var ret = [];
              if (value == "10248") {
                ret.push('/resource/image/icon/be.png');
              }else {
                ret.push('/resource/image/icon/br.png');
              }

              return ret
            }
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