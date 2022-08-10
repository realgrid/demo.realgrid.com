#### RealGrid와 amchart 연계

amchart는 [https://www.amcharts.com/](https://www.amcharts.com/) 페이지에서 확인 할 수 있습니다.  

#### amchart 설정

```js
am4core.ready(function() {
    am4core.useTheme(am4themes_animated);

    var chart = am4core.create("chartdiv", am4charts.PieChart);

    var pieSeries = chart.series.push(new am4charts.PieSeries());
    pieSeries.dataFields.value = "litres";
    pieSeries.dataFields.category = "country";

    chart.innerRadius = am4core.percent(30);

    pieSeries.slices.template.stroke = am4core.color("#fff");
    pieSeries.slices.template.strokeWidth = 2;
    pieSeries.slices.template.strokeOpacity = 1;
    pieSeries.slices.template
    .cursorOverStyle = [
        {
        "property": "cursor",
        "value": "pointer"
        }
    ];

    pieSeries.alignLabels = false;
    pieSeries.labels.template.bent = true;
    pieSeries.labels.template.radius = 3;
    pieSeries.labels.template.padding(0,0,0,0);

    pieSeries.ticks.template.disabled = true;

    var shadow = pieSeries.slices.template.filters.push(new am4core.DropShadowFilter);
    shadow.opacity = 0;

    var hoverState = pieSeries.slices.template.states.getKey("hover"); 

    var hoverShadow = hoverState.filters.push(new am4core.DropShadowFilter);
    hoverShadow.opacity = 0.7;
    hoverShadow.blur = 5;

    chart.legend = new am4charts.Legend();

    //그리드 행 변경 이벤트
    gridView.onCurrentRowChanged =  function (grid, oldRow, newRow) {
        var a = dataProvider.getValue(newRow, "GDP")
        var b = dataProvider.getValue(newRow, "GNI")
        var c = dataProvider.getValue(newRow, "PGNI")
        var d = dataProvider.getValue(newRow, "DIncome")

        chart.data = [{
            country: "GDP",
            litres: dataProvider.getValue(newRow, "GDP")
        },{
            country: "GNI",
            litres: dataProvider.getValue(newRow, "GNI")
        },{
            country: "PGNI",
            litres: dataProvider.getValue(newRow, "PGNI")
        },{
            country: "DIncome",
            litres: dataProvider.getValue(newRow, "DIncome")
        }]
    };
});
```