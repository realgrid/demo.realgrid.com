---
layout: page
title: 스파크 라인 렌더러
order: 2
devbox: true
devboxfile: SparkLineRenderer_devbox.md
published: true
categories:
  - 시리즈 컬럼
tags: ['시리즈', 'series', 'SparkLine']
---

Spark line은 기간 등 일정 범위 내의 데이터 흐름을 간략하고 직관적으로 표시하는 데 사용될 수 있습니다.  
시리즈 컬럼에 대한 개요는 [시리즈 컬럼](/demo/Series/SeriesColumn/)을 참조하세요. 

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

  fieldSet="seriesField"
  columnSet="sparkLineRendererColumn"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption1"
  styleSet="style1"

  dataSet="seriesColumnData.json"
  successDataSet="onGridSuccessDataSet" 
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}