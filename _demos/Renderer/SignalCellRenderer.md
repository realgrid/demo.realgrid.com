---
layout: page
title: 시그널 렌더러
order: 7
devbox: true
devboxfile: SignalCellRenderer_devbox.md
published: true
categories:
  - 렌더러
tags: ['렌더러', 'renderer']
---

시그널바 셀 렌더러는 컬럼 스타일 figureState 값과 렌더러의 barCount 속성을 이용해 데이터 셀 값을 신호 세기로 표시합니다.  
정확한 값보다는 일정 단계의 상태를 표시하는데 사용돼야 합니다.  

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

  fieldSet="rendererFields"
  columnSet="signalCellRendererColumns"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption1"
  styleSet="style1"

  dataSet="CustomOrders.json"
  successDataSet="onGridSuccessDataSet"  
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}