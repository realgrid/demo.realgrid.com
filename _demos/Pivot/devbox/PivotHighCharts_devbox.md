#### RealGrid와 HighCharts를 연계

HighCharts는 [http://www.highcharts.com/download](http://www.highcharts.com/download){:target="_blank"} 페이지에서 다운 받을수 있습니다.

#### pivot 데이터, 라벨값 가져오기

포커스 이동 시 [onCurrentChanged](http://help.realgrid.com/pivotApi/RealPivot/onCurrentChanged/){:target="_blank"} 이벤트가 발생하며 [getAllValues](http://help.realgrid.com/pivotApi/RealPivot/getAllValues/){:target="_blank"},
[getRowValues](http://help.realgrid.com/pivotApi/RealPivot/getRowValues/){:target="_blank"} 로 값을 가져올 수 있습니다.

사용 목적에 맞게 가져온 데이터를 원하는 형태로 가공해서 사용할 수 있습니다.

```js
pivot.onCurrentChanged = function (grid, index) {

    var attrs = Object.keys(index.columns);
    var level = attrs.filter(function (item) { return item == "__sum" || item == "valueField" ? false : true; }).length;

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
```


#### 차트 생성 함수

```js
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
```