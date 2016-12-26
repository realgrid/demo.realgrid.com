---
layout: page
title: 헤더 높이
order: 1
devbox: true
devboxfile: HeaderHeight_devbox.md
published: true
categories:
  - 헤더와 푸터
tags: ['Header', 'Height', 'item', 'number', '행번호']
---

1.1.17버전부터는 세로 방향으로 그룹핑된 컬럼 헤더들의 높이를 개별적으로 지정할 수 있습니다.
Header의 heightFill 속성을 "fixed"로 지정하고, ColumnHeader.fixedHeight 속성에 원하는 높이를 지정하면 해당 높이는 고정되어 표시되고 지정하지 않은 나머지 컬럼들은 전체 헤더 높이의 나머지 부분을 균등하게 나누어 표시됩니다.
fixedHeight의 합이 Header높이보다 크거나 모든 컬럼 Level이 fixedHeight를 부여할 경우 합이 Header의 높이와 다르면 고정높이는 취소되고 균등분배됩니다.

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

  fieldSet="HeaderHeightField"
  columnSet="HeaderHeightColumn"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption_HeaderHeight"
  styleSet="style1"

  dataSet="CustomOrders.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}
