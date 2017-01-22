---
layout: page
title: 데이터 수정
order: 3
devbox: true
devboxfile: Updating-devbox.md
published: true
categories:
  - 그리드 편집
tags: ['editing', '편집', 'updating']
---

그리드의 [gridView.editOptions](http://help.realgrid.com/api/types/EditOptions/){:target="_blank"}.editable이 true이면 사용자는 행 편집을 할 수 있습니다. 편집 중 Esc키로 셀 편집을 취소할 수 있고, 셀 편집 중이 아닌 상태에서 Esc키를 누르면 행 편집이 취소됩니다.  
또, 편집된 값들이 DataProvider에 전달된 시점([dataProvider.onRowUpdating()](http://help.realgrid.com/api/LocalDataProvider/onRowUpdating/){:target="_blank"})과 DataProvider에 저장 완료된 시점([dataProvider.onRowUpdated()](http://help.realgrid.com/api/LocalDataProvider/onRowUpdated/){:target="_blank"})에 각각 callback을 지정할 수 있습니다.  

또한 개발자가 [GridView.beginUpdateRow()](http://help.realgrid.com/api/GridView/beginUpdateRow/){:target="_blank"} 메소드를 통해 사용자가 편집을 시작할 수 있습니다.  

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

  fieldSet="DefaultField"
  columnSet="DefaultColumn"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="DefaultGridOption"
  styleSet="style1"

  dataSet="DefaultDataSet.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}