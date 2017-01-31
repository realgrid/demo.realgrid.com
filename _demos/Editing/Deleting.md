---
layout: page
title: 데이터 삭제
order: 4
devbox: true
devboxfile: Deleting-devbox.md
published: true
categories:
  - 그리드 편집
tags: ['editing', '편집', 'deleting', '삭제']
---

그리드 [editOptions](http://help.realgrid.com/api/types/EditOptions/){:target="_blank"}.deletable이 true이면 사용자는 `Ctrl`+`Del` 키를 눌러 현재 선택된 행을 삭제할 수 있습니다. 실제 삭제하기 전에 사용자 확인을 받을 필요가 있다면 editOptions.deleteRowsConfirm 속성을 true로 지정하면 됩니다. 확인 메시지를 editOptions.deleteRowsMessage로 지정할 수도 있습니다.

<script>
  var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
    dataProvider.setRows(data);
  }
  var onDoneDataSet = function() {
  	dataProvider.setRowStates([2,3,4], "created");
  	dataProvider.setRowStates([7,8], "createAndDeleted");
  }
</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="DefaultField"
  columnSet="DefaultColumn"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption_Deleting"
  styleSet="style1"

  dataSet="DefaultDataSet.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}