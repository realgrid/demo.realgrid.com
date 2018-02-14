#### RealGrid와 HighCharts를 연계

HighCharts는 [http://www.highcharts.com/download](http://www.highcharts.com/download) 페이지에서 다운 받을수 있습니다.  

#### 차트 생성 함수

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
                    console.log(e);
                }
            }
        }
    });
}
```

#### 컬럼 헤더 체크 및 데이터 행 변경 이벤트

```js
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
```

#### 헤더 체크 상태에 따른 컬럼 색상 설정

```js
function setColumnColor(name, color, check) {
    var col = gridView.columnByName(name);
    col.styles = check ? { background: color.replace("#", "#39") } : { background: null };
    gridView.setColumn(col);
}
```