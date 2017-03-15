---
layout: page
title: 이미지 렌더러
order: 4
devbox: true
devboxfile: ImageCellRenderer_devbox.md
published: true
categories:
  - 렌더러
tags: ['렌더러', 'renderer', 'image']
---

Image 셀 렌더러는 데이터 셀의 값을 이미지 url로 해석해서 그 이미지를 내려받고 표시합니다.

<script>
var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
	dataProvider.setRows(data);
}
var onDoneDataSet = function() {
	gridView.setDisplayOptions({rowHeight:70});
	gridView.setFooter({visible:false})

  gridView.setColumnProperty("NormalFlag1", "renderer", {type: "image", sommthing: true})
  gridView.setColumnProperty("NormalFlag2", "renderer", {type: "image", sommthing: true})
}
</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="rendererFields"
  columnSet="imageCellRendererColumns"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption1"
  styleSet="style1"

  dataSet="CustomOrders.json"
  successDataSet="onGridSuccessDataSet"  
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}