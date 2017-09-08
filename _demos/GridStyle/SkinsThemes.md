---
layout: page
title: 그리드 태마
order: 11
devbox: true
devboxfile: SkinsThemes_devbox.md
published: true
categories:
  - 그리드 스타일
tags: ['Style', '태마', 'theme']
---

<script type="text/javascript" src="/lib/realgrid/RealGridSkins.js"></script>

그리드에 미리 설정한 스타일 속성값으로 원하는 그리드 태마를 동적으로 적용할 수 있습니다.

<script>
  var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
    dataProvider.setRows(data);
  }
  var onDoneDataSet = function() {
    var newDynamicStyles = [{
        criteria: "row mod 2 = 0",
        styles: "background=#F4F4FA"
    }];

    gridView.setStyles({
        body: {
            dynamicStyles: newDynamicStyles
        }
    });    
  }
</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="dynamicStylesonRowsFields"
  columnSet="dynamicStylesonRows"
  dpOptionSet="dataProviderOption1"  
  styleSet="style1"

  dataSet="CountriesByPopulation.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}
