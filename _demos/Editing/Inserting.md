---
layout: page
title: 데이터 추가 또는 삽입
order: 2
devbox: true
devboxfile: Inserting-devbox.md
published: true
categories:
  - 그리드 편집
tags: ['editing', '편집', 'inserting']
---

그리드의 [editOptions](http://help.realgrid.com/api/types/EditOptions/){:target="_blank"}.insertable이 true이면 사용자는 Insert키로 행 삽입을 시작할 수 있습니다. [editOptions](http://help.realgrid.com/api/types/EditOptions/){:target="_blank"}.appendable이 true이면 마지막 행에서 아래 화살표 키로 행 추가를 시작할 수 있습니다.  
셀 편집 중 Esc 키를 누르면 셀 편집이 취소되고, 셀 편집 중이 아닌 상태에서 Esc 키를 누르면 행 추가가 취소됩니다.  

또한 개발자가 javascript 메소드를 통해 사용자 삽입/추가를 시작할 수 있습니다.  

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