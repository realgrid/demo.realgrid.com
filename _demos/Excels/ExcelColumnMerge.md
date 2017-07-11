---
layout: page
title: Excel - Column Merge
order: 4
devbox: true
devboxfile: ExcelColumnMerge_devbox.md
published: true
categories:
  - 엑셀 내보내기
tags: ['excel', 'export', 'merge']
---

병합된 컬럼셀들을 병합된 채로 출력하거나, ExportOptions.separateRows 속성을 true로 지정해서 풀려진 상태로도 출력할 수 있습니다. 기본값은 false입니다.

<script>
var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
  dataProvider.setRows(data);
}
</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="cellMergingField"
  columnSet="cellMergingColumn"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption1"
  styleSet="style1"

  dataSet="griddata1.json"
  successDataSet="onGridSuccessDataSet"

  gridWidth="100%"
  gridHeight="300px" %}