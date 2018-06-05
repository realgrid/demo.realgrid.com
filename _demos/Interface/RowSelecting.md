---
layout: page
title: 하이차트 연동 행 선택
order: 3
devbox: true
devboxfile: RowSelecting_devbox.md
published: true
categories:
  - 차트 및 리포트 연동
tags: ['연동', 'interface']
---

RealGrid와 HighCharts를 사용하여 연계한 예제입니다.   
각 행의 Checkbar를 선택/해제하면 선택된 행만 Line Chart에 표시가 됩니다. 또한 Focus된 행을 별도의 Pie Chart로 표시됩니다.

<script type="text/javascript" src="/lib/highcharts/highcharts.js"></script>
<script>
var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
  gridEvents(gridView, dataProvider)
  dataProvider.onRowCountChanged = function () {
    setHiChart(dataProvider);
  }

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
            //center
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
            shared: true
            // 한 로우에 여러 컬럼의 값을 표시
        },
        legend: {
            layout: 'vertical',
            align: 'right',
            verticalAlign: 'middle',
            borderWidth: 0
        },
        series: [{
            type: 'spline',
            name: "GDP",
            //              data : provider.getFieldValues("GDP"),
            tooltip: {
                valueSuffix: "$ ($100 million)"
            }
        }, {
            type: 'spline',
            name: "GNI",
            //              data : provider.getFieldValues("GNI"),
            tooltip: {
                valueSuffix: "$ ($100 million)"
            }
        }, {
            type: 'spline',
            name: "PGNI",
            //              data : provider.getFieldValues("PGNI"),
            tooltip: {
                valueSuffix: "$"
            }
        }, {
            type: 'spline',
            name: "DIncome",
            //              data : diVal,
            tooltip: {
                valueSuffix: "$"
            }
        }, {
            type: 'pie',
            name: 'Total consumption',
            data: [{
                name: 'GDP',
                y: gridView.getValue(gridView.getCurrent().itemIndex, 1),
                color: Highcharts.getOptions().colors[0]
            }, {
                name: 'GNI',
                y: gridView.getValue(gridView.getCurrent().itemIndex, 2),
                color: Highcharts.getOptions().colors[1]
            }, {
                name: 'PGNI',
                y: gridView.getValue(gridView.getCurrent().itemIndex, 3),
                color: Highcharts.getOptions().colors[3]
            }, {
                name: 'DIncome',
                y: gridView.getValue(gridView.getCurrent().itemIndex, 4) == undefined ? null : gridView.getValue(gridView.getCurrent().itemIndex, 4),
                color: Highcharts.getOptions().colors[4]
            }],
            center: [100, 80],
            size: 100,
            showInLegend: false,
            dataLabels: {
                enabled: true
            }
        }],
        chart: {
            events: {
                load: function () {
 
                },
                click: function (e) {
                    //console.log(e);
                }
            }
        }
    });
}

function gridEvents(grid, provider) {
    grid.onCurrentChanged = function (grid, index) {
        var chart = $("#container").highcharts();
        if (!chart)
            return;
        setPie(chart);
    }
 
    provider.onRowCountChanged = function () {
        setHiChart(dataProvider);
    }
 
    grid.onItemChecked = function (grid, itemIndex, checked) {
        var checkItems = grid.getCheckedItems();
        var values = [];
        $.each(checkItems, function () {
            values.push(grid.getValues(this));
        });
        setCheckValueToChart(values);
    }
 
    grid.onItemAllChecked = function (grid, checked) {
        if (checked) {
            setCheckValueToChart(dataProvider.getJsonRows());
        } else {
            setCheckValueToChart([]);
        }
    }
}

function setPie(chart, index) {
    index = index ? index : gridView.getCurrent();
    var rowValue = dataProvider.getJsonRow(index.dataRow);
    var hcData = [];
    $.each(rowValue, function (k, v) {
        if (v == undefined)
            v = null;
        if (k == "Year")
            return true;
        hcData.push(v);
    });
    chart.series[4].setData(hcData);
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