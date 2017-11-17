---
layout: page
title: 주차 선택 달력
order: 12
devbox: true
devboxfile: WeekDateCellEditor_devbox.md
published: true
categories:
  - 그리드 편집
tags: ['editing', '편집', '편집기', 'editor', '달력', '주차']
---

YYYYWW, YYYY-WW, YYYYWW -> YYYY-WW 컬럼은 주차 선택 기능이 설정된 컬럼이며 각 데이터 형태에 따라 바인딩 하는 방식과 그리드에 표시하는 방식을 설정할 수 있습니다.  
YYYYWW -> YYYY-WW 컬럼은 YYYYWW 형태의 데이터를 그리드에서 마스크 편집기 기능을 사용해서 YYYY-WW 형태로 표시합니다.


<script>
  var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
    dataProvider.setRows(data);
  }
  var onDoneDataSet = function() {
    gridView.setColumnProperty("dateTime3","displayRegExp", /^([0-9]{4})([0-9]{2})$/)
    gridView.setColumnProperty("dateTime3","displayReplace", "$1-$2")
  }
</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="weekDateFields"
  columnSet="weekDateColumns"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="DefaultGridOption"
  styleSet="style1"

  dataSet="weekDateData.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}