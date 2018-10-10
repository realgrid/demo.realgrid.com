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

        var values = pivot.getAllValues(false).판매량;
        // 선택한 행에 대한 값 가져오기
        var rowFields = pivot.getRowFieldNames();
        for (var i = 0; i < rowFields.length; i++) {
            var fld = rowFields[i];

            if (index.rows.hasOwnProperty(fld)) {
                values = values.rows[index.rows[fld]];
            } else {
                break;
            }
        }

        // 키+값을 매칭
        var keys = [];
        var vals = [];
        var columnLabels = [];
        switch(level) {
            case 0:
            case 1:
                $.each(values.cols, function (attr1, obj1) { // 년도 Loop
                    keys.push([attr1]);
                    vals.push(obj1.value);
                });
                columnLabels.push(pivot.getColumnLabels()[0].label);
                break;
            case 2:
                $.each(values.cols, function (attr1, obj1) { // 년도 Loop
                    $.each(obj1.cols, function (attr2, obj2) { // 분기 Loop
                        keys.push([attr1, attr2]);
                        vals.push(obj2.value);
                    });
                });
                for(var i = 0; i < Object.keys(pivot.getColumnLabels()[0].childs).length; i++){
                    columnLabels.push(pivot.getColumnLabels()[0].childs[i].label);
                }
                break;
            case 3:
                $.each(values.cols, function (attr1, obj1) { // 년도 Loop
                    $.each(obj1.cols, function (attr2, obj2) { // 분기 Loop
                        $.each(obj2.cols, function (attr3, obj3) {  // 월 Loop
                            keys.push([attr1, attr2, attr3]);
                            vals.push(obj3.value);
                        });
                    });
                });
                for(var i = 0; i < Object.keys(pivot.getColumnLabels()[0].childs).length; i++){
                    for(var j = 0; j < Object.keys(pivot.getColumnLabels()[0].childs[i].childs).length; j++){
                        columnLabels.push(pivot.getColumnLabels()[0].childs[i].childs[j].label);
                    }
                }
                break;
        }

        setHighChart(dataProvider, vals, index, columnLabels);
    }
}
var onDoneDataSet = function() {
    
}

var onSuccessColumnSet = function(data, textStatus, jqXHR) {
}  


function setHighChart(provider, vals, index, columnLabels) {
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
            categories: columnLabels,
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
  pivotHeight="500px" %}

<div id="container" style="height:400px;"></div>