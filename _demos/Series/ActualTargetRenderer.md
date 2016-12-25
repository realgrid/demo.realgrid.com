---
layout: page
title: 성과/목표 렌더러
order: 3
devbox: true
devboxfile: ActualTargetRenderer_devbox.md
published: true
categories:
  - 시리즈 컬럼
tags: ['시리즈', 'series', 'target']
---

각각 두 개의 데이터 필드에 저장된 목표값(혹은 기대값)과 실행값을 비교하여 표시하는 시리즈 렌더러들입니다.

<script>
var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
	dataProvider.setRows(data);
}

</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="actualTargetRendererField"
  columnSet="actualTargetRendererColumn"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption1"
  styleSet="style1"

  dataSet="ActualTargetRenderer.json"
  successDataSet="onGridSuccessDataSet" 

  gridWidth="100%"
  gridHeight="300px" %}