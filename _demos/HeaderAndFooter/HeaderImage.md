---
layout: page
title: 헤더 이미지 사용
order: 1
devbox: true
devboxfile: HeaderImage_devbox.md
published: true
categories:
  - 헤더와 푸터
tags: ['Header Image', 'Header', 'image', '이미지', '헤더 이미지']
---

RealGrid의 컬럼헤더에 이미지를 구현하는 방법을 설명하는 페이지 입니다.

**ColumnHeader.imageLocation** 속성은 이미지의 위치를 지정합니다.   자세한 내용은 Help사이트의 [ColumnHeaderItemLocation](http://help.realgrid.com/api/types/ColumnHeaderItemLocation/){:target="_blank"} 페이지를 참고바랍니다.  
**ColumnHeader.imageUrl** 속성은 불러올 이미지의 경로를 지정합니다.  
**ColumnHeader.itemGap** 속성에 의해 Text와 이미지사이의 간격이 결정됩니다.  

<script>
  var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
    dataProvider.setRows(data);
  }
  var onDoneDataSet = function() {

  }
</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="indicatorField"
  columnSet="headerImageColumn"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption_HeaderImage"
  styleSet="style1"

  dataSet="CustomOrders.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}
