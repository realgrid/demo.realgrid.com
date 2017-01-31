---
layout: page
title: 기본 편집기
order: 6
devbox: true
devboxfile: Editors-devbox.md
published: true
categories:
  - 그리드 편집
tags: ['editing', '편집', '편집기', 'editor']
---

리얼그리드는 라인, 멀티라인, 드롭다운, 날짜, 검색 등의 다양한 형태의 편집기를 제공 하고 있습니다.

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

  fieldSet="EditorField"
  columnSet="EditorColumn"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption_Editors"
  styleSet="style1"

  dataSet="DefaultDataSet.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}