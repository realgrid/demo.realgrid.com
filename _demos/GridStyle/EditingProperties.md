---
layout: page
title: 편집관련 속성들
order: 8
devbox: true
devboxfile: EditingProperty_devbox.md
published: true
categories:
  - 그리드 스타일
tags: ['style', '스타일']
---

DataCellStyle로 특정 데이터셀의 editable과 readOnly 속성을 지정할 수 있습니다. 

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
  columnSet="EditingPropertiesColumns"
  dpOptionSet="dataProviderOption1"  
  styleSet="style1"

  dataSet="FireDamage.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}