---
layout: page
title: amchart 연동 행 선택
order: 9
devbox: true
devboxfile: AmchartRowSelecting_devbox.md
published: true
categories:
  - 차트 및 리포트 연동
tags: ['연동', 'interface']
---

RealGrid와 amchart를 사용하여 연계한 예제입니다.   
그리드에서 포커스를 이동하면 선택된 행의 데이터로 차트값이 구성됩니다.

`※ amchart 관련 문의는 amchart 업체에 문의를 해주시기 바랍니다.`

<script type="text/javascript" src="/lib/amchart/core.js"></script>
<script type="text/javascript" src="/lib/amchart/charts.js"></script>
<script type="text/javascript" src="/lib/amchart/animated.js"></script>
<script>
var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
  setChart();

  dataProvider.setRows(data);
  gridView.refresh();
}

var onDoneDataSet = function() {

}

function setChart(){
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
    }

</script>

<div id="chartdiv" style="width:800px;height:500px"></div>

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