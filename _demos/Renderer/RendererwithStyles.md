---
layout: page
title: 렌더러 동적 적용
order: 10
devbox: true
devboxfile: RendererwithStyles_devbox.md
published: true
categories:
  - 렌더러
tags: ['렌더러', 'renderer']
---

그리드의 addCellRenderers() 함수로 데이터셀 렌더러 정보들을 미리 추가하고, 컬럼 동적 스타일의 renderer 값을 이용하면, 같은 컬럼에서 값에 따라 다른 렌더러를 사용하여 셀을 표시할 수 있습니다.

<script>
var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
	dataProvider.setRows(data);
}

var onDoneDataSet = function() {
	gridView.setDisplayOptions({rowHeight:30});
	gridView.setFooter({visible: false});
}
</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="rendererFields"
  columnSet="rendererwithStylesColumns"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption1"
  styleSet="style1"

  dataSet="CustomOrders.json"
  successDataSet="onGridSuccessDataSet"  
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}