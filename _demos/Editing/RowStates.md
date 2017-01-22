---
layout: page
title: 행 상태
order: 5
devbox: true
devboxfile: RowState-devbox.md
published: true
categories:
  - 그리드 편집
tags: ['editing', '편집', 'rowstate', 'state', '행상태']
---

RealGrid는 행의 상태를 관리할 수 있습니다. 이 행이 편집된 행인지, 추가된 행인지, 삭제된 행인지, 또는 추가된 후 삭제된 행인지를 확인 할 수 있습니다. 행의 상태를 관리하기 위해서는 기본적으로 [dataProviderOptions](http://help.realgrid.com/api/types/DataProviderOptions/){:target="_blank"}의 속성중 checkStates 속성값이 true로 되어 있어야 합니다. 기본값이 true이므로 별다른 설정은 필요 없습니다.

RealGrid는 사용자의 액션(추가, 수정, 삭제)에 따라 자동으로 행 상태를 관리합니다. 또한 RealGrid는 개발자의 의도에 따라 임의로 행 상태를 관리할 수도 있습니다.

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
  gridOptionSet="gridOption_RowState"
  styleSet="style1"

  dataSet="DefaultDataSet.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}