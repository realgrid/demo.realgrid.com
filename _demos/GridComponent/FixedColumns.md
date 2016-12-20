---
layout: page
title: 열 고정하기
order: 7
devbox: true
devboxfile: fixedColumn-devbox.md
published: true
categories:
  - 그리드 구성요소
tags: ['FixedColumns', '열고정', '고정컬럼']
---

[FixedOptions](http://help.realgrid.com/api/types/FixedOptions/)를 설정하여 그리드 최상위 컬럼 중 왼쪽이나 오른쪽부터 하나 이상의 컬럼을 고정시킬 수 있습니다. 고정된 컬럼(그룹)은 수평 스크롤 영역에서 제외됩니다. 또한, 고정 영역에 속한 컬럼들을 편집 불가, 이동 불가, 크기 변경 불가 상태로 지정할 수 있습니다.  

행 고정 또한 지정할 수 있습니다.  

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
  dpOptionSet="DefaultDataProviderOption"
  gridOptionSet="DefaultGridOption"
  styleSet="style1"

  dataSet="DefaultDataSet.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}