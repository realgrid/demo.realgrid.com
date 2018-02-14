#### RealGrid와 HighCharts를 연계

HighCharts는 [http://www.highcharts.com/download](http://www.highcharts.com/download) 페이지에서 다운 받을수 있습니다.  

#### pie 타입 차트 생성

```js
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
                    console.log(e);
                }
            }
        }
    });
}
```

#### 이벤트 설정

```js
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
```

#### setPie 설정 함수

```js
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
```