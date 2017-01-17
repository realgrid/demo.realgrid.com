---
layout: page
title: 동적 행 스타일
order: 5
devbox: true
devboxfile: DynamicStylesonRows_devbox.md
published: true
categories:
  - 그리드 스타일
tags: ['Style', 'Dynamic Styles', '스타일', '동적스타일']
---

데이터 셀이 그려질 때 셀 렌더러는 컬럼에 지정된 스타일 속성들을 참조합니다. 컬럼에는 여러 방식으로 스타일 셋이 지정되는데, 적용되는 순서는 아래와 같습니다.
- 컬럼 스타일 - 컬럼 생성 시 styles 속성으로 지정합니다.
- 행 별 동적 스타일 - 행 수준에서 판단해서 지정해야 하는 경우에 사용합니다.
- 컬럼 기본 동적 스타일 - 모든 컬럼에 지정해야 하는 동적 스타일을 지정합니다. 컬럼별 동적 스타일을 참조하십시오.
- 컬럼 동적 스타일- 컬럼별 동적 스타일을 참조하십시오.

즉, 각각의 데이터셀은 아래와 같은 순서대로 적용된 스타일셋으로 그려지게 됩니다.

`grid.styles -> grid.body.styles -> `**`column.styles -> body.dynamicStyles`**` -> body.cellDynamicStyles -> column.dynamicStyles`

하지만 경우에 따라서는 위의 순서보다 다음과 같은 순서가 보다 자연스러울 수 있습니다.

`grid.styles -> grid.body.styles -> `**`body.dynamicStyles -> column.styles`**` -> body.cellDynamicStyles -> column.dynamicStyles`

body.**rowStylesFirst** 속성을 true로 지정하면 위와 같은 순서대로 적용됩니다. 기본값은 false입니다.

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
