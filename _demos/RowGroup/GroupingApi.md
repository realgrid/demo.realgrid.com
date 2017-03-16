---
layout: page
title: 그룹핑 API
order: 2
devbox: true
devboxfile: GroupingApi-dbox.md
published: true
categories:
  - 행 그룹
tags: ['grouping','rowGroup','행그룹','그룹']
---

코드를 이용하여 rowGroup을 추가하거나 해제하고 현재 그룹핑된 정보를 찾아올수 있도록 함수들을 제공합니다.

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