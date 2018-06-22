---
layout: page
title: 동적 컬럼 스타일
order: 4
devbox: true
devboxfile: DynamicStylesonColumns_devbox.md
published: true
categories:
  - 그리드 스타일
tags: ['Style', 'Dynamic Styles', '스타일', '동적스타일']
---

컬럼 생성 시 지정하는 고정된 컬럼 스타일 외에, 실행 시간에 변경될 수 있는 값이나 상태에 따라 셀에 적용될 스타일을 다르게 지정할 수 있습니다. 컬럼 단위의 동적 스타일은 두 가지 방식으로 지정할 수 있는데, 먼저 컬럼의 dynamicStyles속성으로 dynamic style 배열을 지정하거나, 그리드 수준에서 모든 컬럼에 적용될 기본 동적 스트일을 grid.body.cellDynamicStyles에 지정합니다. 아래의 예제에서는 구분 컬럼에 "damage" 라는 단어가 들어간 셀의 배경색을 불게 표시하도록 컬럼 동적 스타일을 적용하였고, 두 가지 기본 동적 스타일을 번갈아 지정해볼 수 있도록 하였습니다.
동적 스타일을 포함, 실행 시간에 하나의 데이터셀 렌더링에 사용될 스타일 적용 순서는 Dynamic Styles on Rows을 참조하십시오.
동적 스타일을 활용하면 많은 경우에 코딩없이 훌륭한 결과를 낼 수 있습니다.

<script>
  var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
    dataProvider.setRows(data);
  }

  var onDoneDataSet = function() {
    var cellDefaultStyles = [{
        criteria: "value >= 200",
        styles: "background=#55e3d36b"
    }, {
        criteria: "value >= 500",
        styles: "background=#55cbc060"
    }, {
        criteria: "value >= 2000",
        styles: "background=#5589913d"
    }, {
        criteria: "value >= 10000",
        styles: "background=#5545612c;foreground=#ffffffff"
    }];

    gridView.setStyles({
        body: {
            cellDynamicStyles: cellDefaultStyles
        }
    });    

  }
</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="dynamicStylesonColumnsFields"
  columnSet="dynamicStylesonColumns"
  dpOptionSet="dataProviderOption1"  
  styleSet="style1"

  dataSet="FireDamage.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}
