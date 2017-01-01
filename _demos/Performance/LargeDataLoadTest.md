---
layout: page
title: Large Data Load Test
order: 3
published: true
categories:
  - 성능
tags: ['성능', 'performance', '스크롤', 'scroll']
---

그리드 생성 시 처음 표시되는 데이터셋은 서버 상에 정적 파일로 존재하거나, URL 요청 시점에 데이터베이스 쿼리 등을 통해 생성되어 반환될 수 있습니다. 그리드가 직접 서버에 요청하여 전달된 Csv 텍스트를 데이터 행들로 변환하여 내부 데이터셋에 추가합니다.

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

  fieldSet="scrollTestField"
  columnSet="scrollTestColumn"
  dpOptionSet="dataProviderOption1"  
  styleSet="style1"

  dataSet="celloData.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}
