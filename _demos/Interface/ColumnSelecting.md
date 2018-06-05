---
layout: page
title: 하이차트 연동 컬럼 선택
order: 1
devbox: true
devboxfile: ColumnSelecting_devbox.md
published: true
categories:
  - 차트 및 리포트 연동
tags: ['연동', 'interface']
---

RealGrid와 HighCharts를 사용하여 연계한 예제입니다.   
컬럼 해더의 CheckBox를 클릭하면 발생하는 그리드의 이벤트함수 onColumnCheckedChanged를 사용하여 Highcharts의 컬럼을 숨기거나 보이도록 하였습니다.

<script type="text/javascript" src="/lib/highcharts/highcharts.js"></script>
<script>
var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
  var columnNames = ["GDP", "GNI", "PGNI", "DIncome"];

  for (var i = 0; i < columnNames.length; i++){
  	gridView.setColumnProperty(columnNames[i],"header",{
        "checkLocation": "left",
        "checked": true});
    gridView.setColumnProperty(columnNames[i],"checked",true);
  }

  gridEvents(gridView, dataProvider);

  dataProvider.setRows(data);
}
var onDoneDataSet = function() {

}

function setHiChart(provider) {
    var categories = provider.getFieldValues("year");
    var diVal = provider.getFieldValues("DIncome");
    $.each(diVal, function (k, v) {
        if (v == undefined)
            diVal[k] = null;
    });
 
    $('#container').highcharts({
        title: {
            text: '통계청 총생산소득',
            x: -20
        },
        subtitle: {
            text: 'www.realgrid.com',
            x: -20
        },
        xAxis: {
            categories: categories,
            crosshair: true
        },
        yAxis: [{
            title: {
                text: '소득 ($)'
            },
            labels: {
                format: '{value} $'
            }
        }],
        tooltip: {
            shared: true // 한 로우에 여러 컬럼의 값을 표시
        },
        legend: {
            enabled : false
        },
        series: [{
            name: "GDP",
            data: provider.getFieldValues("GDP"),
            tooltip: {
                valueSuffix: "$ ($100 million)"
            }
        }, {
            name: "GNI",
            data: provider.getFieldValues("GNI"),
            tooltip: {
                valueSuffix: "$ ($100 million)"
            }
        }, {
            name: "PGNI",
            data: provider.getFieldValues("PGNI"),
            tooltip: {
                valueSuffix: "$"
            }
        }, {
            name: "DIncome",
            data: diVal,
            tooltip: {
                valueSuffix: "$"
            }
        }],
        chart: {
            type: 'column',
            events: {
                load: function () {
                    var chart = $("#container").highcharts();
                    $.each(chart.series, function () {
                        var col = gridView.columnByName(this.name);
                        col.styles = { background: this.color.replace("#", "#39") };
                        gridView.setColumn(col);
                    });
                },
                click: function (e) {
                    //console.log(e);
                }
            }
        }
    });
}

function setColumnColor(name, color, check) {
    var col = gridView.columnByName(name);
    col.styles = check ? { background: color.replace("#", "#39") } : { background: null };
    gridView.setColumn(col);
}

function gridEvents(grid, provider) {
    grid.onColumnCheckedChanged = function (grid, column, checked) {
        var colName = column.name;
        var chart = $("#container").highcharts();
        $.each(chart.series, function () {
            if (this.name === colName) {
                this.setVisible(checked);
                setColumnColor(this.name, this.color, checked);
            }
        });
    }
 
    provider.onRowCountChanged = function () {
        setHiChart(dataProvider);
    }
}
</script>

<div id="container" style="height:400px;"></div>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="highchartsFields"
  columnSet="highchartsColumns"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption1"
  styleSet="style1"

  dataSet="총생산소득.json"
  successDataSet="onGridSuccessDataSet"  
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}