---
layout: page
title: 체크바
order: 3
devbox: true
devboxfile: checkBar-devbox.md
published: true
categories:
  - 그리드 구성요소
tags: ['CheckBar', '체크', 'check']
---

[체크바(CheckBar)](http://help.realgrid.com/api/types/CheckBar/)는 그리드의 특정 행을 선택하기 위해 사용합니다. CheckBar에 의해 선택된 특정 행들은 복사나 삭제등 명령을 일괄처리 하기위해 사용할 수 있습니다. <br /> 


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
  gridOptionSet="gridOption_checkBar"
  styleSet="style1"

  dataSet="DefaultDataSet.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}