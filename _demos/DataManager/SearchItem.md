---
layout: page
title: SearchItem
order: 11
devbox: true
devboxfile: SearchItem-devbox.md
published: true
categories:
  - 데이터 관리
tags: ['data', 'SearchItem', '검색']
---

하나 이상의 필드에 대해 행 단위 검색을 할 수 있습니다.  
검색 옵션을 이용하면 "부분 단어", "대소문자 구분" 조건 등으로 검색할 수 있습니다.

<script>
var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
	dataProvider.setRows(data);
}
var onDoneDataSet = function() {
	gridView.setColumnProperty("사진파일명","visible",false)
	gridView.setColumnProperty("사진","visible",false)
	gridView.setColumnProperty("판매월","visible",false)
	dataProvider.setRowCount(200)
	gridView.setOptions({
        select: {
            style: "rows"
        }
    });
}
</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="carFields1"
  columnSet="carColumns1"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption1"
  styleSet="style1"

  dataSet="carData1.json"
  successDataSet="onGridSuccessDataSet"  
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}