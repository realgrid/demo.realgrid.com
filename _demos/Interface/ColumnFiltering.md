---
layout: page
title: 하이차트 연동 컬럼 필터링
order: 2
devbox: true
devboxfile: ColumnFiltering_devbox.md
published: true
categories:
  - 차트 및 리포트 연동
tags: ['연동', 'interface']
---

RealGrid와 HighCharts를 사용하여 연계한 예제입니다.   
RealGrid의 Column Filter를 변경하면 발생하는 onFilteringChanged이벤트를 통해 필터링된 데이터를 Highcharts에 적용되도록 구현하였습니다.  
Year 컬럼의 필터를 변경해여 차트가 변경되는것을 확인하세요.

<script type="text/javascript" src="/lib/highcharts/highcharts.js"></script>
<script>
var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
  gridEvents(gridView, dataProvider);
  dataProvider.setRows(data);
  setTimeout(setFilter(), 300);
}

var onDoneDataSet = function() {

}

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

function setHiChart(provider) {
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
                    //console.log(e);
                }
            }
        }
    });
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