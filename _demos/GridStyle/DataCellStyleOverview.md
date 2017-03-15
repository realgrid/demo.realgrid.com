---
layout: page
title: DataCellStyle Overview
order: 7
devbox: true
devboxfile: DataCellStyleOverview_devbox.md
published: true
categories:
  - 그리드 스타일
tags: ['style', '스타일']
---

리얼그리드에서 데이터 셀의 표시 방식은 기본적으로 컬럼 스타일로 지정할 수 있습니다.  
`오른쪽 예제의 버튼을 클릭해서 그리드에 스타일을 추가해 보세요.`

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

  fieldSet="dynamicStylesonColumnsFields"
  columnSet="dynamicStylesonColumns"
  dpOptionSet="dataProviderOption1"  
  styleSet="style1"

  dataSet="FireDamage.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}