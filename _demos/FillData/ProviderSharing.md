---
layout: page
title: Provider 공유하기
order: 9
devbox: true
devboxfile: ProviderSharing_devbox.md
published: true
categories:
  - 데이터 가져오기
tags: ['filldata', 'Provider']
---

<script>

var onSuccessFieldSet1 = function(data, textStatus, jqXHR) {
  var dp = new RealGridJS.LocalDataProvider();
  gridView1.setDataProvider(dp);
}

var onSuccessFieldSet2 = function(data, textStatus, jqXHR) {
  var dp = new RealGridJS.LocalDataProvider();
  gridView2.setDataProvider(dp);
}

</script>


RealGrid는 View-Model과 Data가 서로 독립된 구조를 가지고 있기 때문에 하나의 DataProvider에 여러개의 서로 다른 GridView를 연결하여 보여줄 수 있습니다.

<div class="row">

{% include realgrid.html

  gridVar="gridView1"
  dpVar="dataProvider1"
  gridId="realgrid1"

  fieldSet="economicGrowthField"
  successFieldSet="onSuccessFieldSet1"
  columnSet="economicGrowthColumn1"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption1"
  styleSet="style1"
  dataSet="economicGrowth.json"

  showToolbox=true
  gridWidth="100%"
  gridHeight="200px" %}

</div>
<div class="row">

  {% include realgrid.html

    gridVar="gridView2"
    dpVar="dataProvider2"
    gridId="realgrid2"

    fieldSet="economicGrowthField"
    successFieldSet="onSuccessFieldSet2"
    columnSet="economicGrowthColumn2"
    dpOptionSet="dataProviderOption1"
    gridOptionSet="gridOption1"
    styleSet="style1"

    showToolbox=true
    gridWidth="100%"
    gridHeight="200px" %}
</div>
