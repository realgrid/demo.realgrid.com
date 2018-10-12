---
layout: page
title: 피벗 하이차트(HighCharts)
order: 17
devbox: true
devboxfile: PivotHighCharts_devbox.md
published: true
categories:
  - 피벗(RealPivot)
tags: ['pivot', '하이차트', 'highcharts']
---

RealPivot과 HighCharts를 사용하여 연계한 예제입니다. 
Pivot화면의 body영역 클릭 시 제조사 및 모델에 대한 판매 실적을 Highcharts의 그래프로 보이도록 하였습니다.

<script type="text/javascript" src="/lib/highcharts/highcharts.js"></script>

<script>
var onGridSuccessDataSet = function(data, textStatus, jqXHR) {

    pivot.setDisplayOptions({columnHeight:40,rowHeight:40,columnWidth:60,blankFillValue:null,virtualRendering:true, showFocus:true})

    dataProvider.fillJsonData(data);
    pivot.setHeaderOptions({formType:"grid"})
    pivot.drawView();

    pivot.onCurrentChanged = function (grid, index) {

      var attrs = Object.keys(index.columns);
      var level = attrs.filter(function (item) { return item == "__sum" || item == "valueField" ? false : true; }).length;

      if(level == 0){
        level = 1
      } 

      var columnLabels = pivot.getColumnLabels();
      var columnList = getLevelLabels(columnLabels, 1, level)

      var vals = []
      var len = Object.keys(pivot.getRowValues("판매량", index.rows).descendants).length;
      for (var i = 0; i < len; i++){
          if(Object.keys(pivot.getRowValues("판매량", index.rows).descendants)[i].split(":::").length == level){
              var key = Object.keys(pivot.getRowValues("판매량", index.rows).descendants)[i];
              vals.push(pivot.getRowValues("판매량", index.rows).descendants[key])
          }
      }

      setHighChart(dataProvider, vals, index, columnList);
    }

    function getLevelLabels(columnChilds, level, targetLevel) {
        var list = [];
        for (var i = 0, len = columnChilds.length; i < len; i++) {
            if(level == targetLevel){
                list.push(columnChilds[i].label)
            } else if(level < targetLevel && columnChilds[i].hasOwnProperty("childs")) {
                var levelLabels = getLevelLabels(columnChilds[i].childs, level + 1, targetLevel)
                list.push.apply(list, levelLabels);
            }
        }
        return list;
    }
}
var onDoneDataSet = function() {
    
}

var onSuccessColumnSet = function(data, textStatus, jqXHR) {
}  


function setHighChart(provider, vals, index, columnList) {
    var subtitle;

    if(Object.keys(index.rows)[0] == "__sum"){
        subtitle = "전체 요약"
    } else if(index.rows.모델){
        subtitle = index.rows.모델
    } else {
        subtitle = index.rows.제조사
    } 

    var categories = provider.getFieldValues("판매날짜");
    var diVal = provider.getFieldValues("판매량");
    $.each(diVal, function (k, v) {
        if (v == undefined)
            diVal[k] = null;
    });
 
    $('#container').highcharts({
        title: {
            text: '차량 판매 실적',
            x: -20
        },
        subtitle: {
            text: subtitle,
            x: -20
        },
        xAxis: {
            categories: columnList,
            crosshair: true
        },
        yAxis: [{
            title: {
                text: '단위(대)'
            },
            labels: {
                format: '{value}'
            }
        }],
        tooltip: {
            shared: true // 한 로우에 여러 컬럼의 값을 표시
        },
        legend: {
            enabled : false
        },
        series: [{
            name: "판매량",
            data: vals,
            tooltip: {
                valueSuffix: "대"
            }
        }],
        chart: {
            type: 'column',
            events: {
            }
        }
    });
}

</script>

{% include realpivot.html

  pivotVar="pivot"
  dpVar="dataProvider"
  pivotId="realpivot"

  fieldSet="pivotDistinct_setFields"
  fieldMappingSet="pivotDistinct_fieldMapping"
  pivotFieldsSet="pivotDistinct_pivotFields"

  dataSet="pivotCarData.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  pivotWidth="100%"
  pivotHeight="370px" %}

<div id="container" style="height:300px;"></div>