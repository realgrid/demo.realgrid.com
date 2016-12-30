---
layout: page
title: 시리즈 컬럼
order: 1
devbox: true
devboxfile: SeriesColumn_devbox.md
published: true
categories:
  - 시리즈 컬럼
tags: ['시리즈', 'series']
---

시리즈 컬럼은 하나 이상의 데이터 필드 값을 동시에 표시하는 컬럼 입니다.

<script>
var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
	dataProvider.setRows(data);
}
var onDoneDataSet = function() {
	gridView.setStyles({
        border: "#ffff0000,5",
        body: {
            cellDynamicStyles: [{
                criteria: [
                    "value < 0"
                ],
                styles: [
                    "foreground=#ccff0000;fontBold=true"
                ]
            }]
        }
    });
}
</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="seriesField"
  columnSet="seriesColumn"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption1"
  styleSet="style1"

  dataSet="seriesColumnData.json"
  successDataSet="onGridSuccessDataSet" 
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}