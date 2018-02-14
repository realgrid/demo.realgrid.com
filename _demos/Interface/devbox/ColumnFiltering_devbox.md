#### RealGrid와 HighCharts를 연계

HighCharts는 [http://www.highcharts.com/download](http://www.highcharts.com/download) 페이지에서 다운 받을수 있습니다.  

#### 그리드 필터 설정

```js
function setFilter() {
    var filters = [];
    var vals = dataProvider.getDistinctValues("year");
    $.each(vals, function (k, v) {
        var filter = {};
        filter.name = v;
        filter.criteria = "value = '" + v + "'";
        filters.push(filter);
    });
 
    var col = gridView.columnByName("Year");
    col.filters = filters;
    gridView.setColumn(col);
}
```

#### 필터 목록 변경 및 데이터 행 변경 이벤트

```js
function gridEvents(grid, provider) {
    provider.onRowCountChanged = function () {
        setHiChart(dataProvider)
    }
 
    grid.onFilteringChanged = function (grid) {
    	setHiChart(provider);
        var count = grid.getItemCount();
        var jArr = [];
        for (var i = 0; i < count; i++) {
            var jObj = grid.getValues(i);
            if (!jObj.Year) jObj.Year = null;
            jArr.push(jObj);
        }
        var chart = $("#container").highcharts();
        if (!chart) return;
        $.each(chart.series, function (k, v) {
            if (this.name == "Year") {
                var cate = $.map(jArr, function () {
                    return this.Year;
                });
                chart.xAxis[0].setCategories(cate);
            } else {
                var data = [];
                $.map(jArr, function (val) {
                    data.push(val[v.name] ? val[v.name] : null);
                })
                this.setData(data);
            }
        });
    }
}
```

#### 차트 생성 함수

```js
function setHiChart(provider) {
    //필터 결과에 맞는 categories 목록 생성
    var categories = [];
    for(var i = 0; i < gridView.getItemCount(); i++){
        categories.push(gridView.getValue(i, "Year"));
    }
	
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
            shared: true // 한 로우에 여러 컬럼의 값을 표시
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
            data: provider.getFieldValues("GDP"),
            tooltip: {
                valueSuffix: "$ ($100 million)"
            }
        }, {
            type: 'spline',
            name: "GNI",
            data: provider.getFieldValues("GNI"),
            tooltip: {
                valueSuffix: "$ ($100 million)"
            }
        }, {
            type: 'spline',
            name: "PGNI",
            data: provider.getFieldValues("PGNI"),
            tooltip: {
                valueSuffix: "$"
            }
        }, {
            type: 'spline',
            name: "DIncome",
            data: diVal,
            tooltip: {
                valueSuffix: "$"
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