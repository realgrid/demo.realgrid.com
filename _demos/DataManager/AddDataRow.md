---
layout: page
title: 새로운 행 추가
order: 8
devbox: true
devboxfile: AddDataRow-devbox.md
published: true
categories:
  - 데이터 관리
tags: ['data', 'add', '추가']
---

사용자가 입력한 정보 등을 이용하여 DataPrvoider에 한 행을 추가할 수 있습니다.  
DataProvider에 새로운 행이 추가되면 그것과 연결된 그리드들에 바로 반영됩니다.

<script>
var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
	var data = [
		{"id":"1","userid":"fgray","company":"Dabfeed","first_name":"Jesse","last_name":"Thompson","gender":"Male","email":"jthompson@realcube.com","birthday":"1966/08/13","pay":8792.8},
		{"id":"2","userid":"wcruz","company":"Flipstorm","first_name":"Donna","last_name":"Mason","gender":"Male","email":"dmason@gabspot.biz","birthday":"1965/07/13","pay":19830.69},
		{"id":"3","userid":"creynolds","company":"Divape","first_name":"Antonio","last_name":"Evans","gender":"Female","email":"aevans@dabvine.info","birthday":"1986/08/01","pay":19476.84},
		{"id":"4","userid":"gjackson","company":"Jamia","first_name":"Catherine","last_name":"Watson","gender":"Male","email":"cwatson@pixope.net","birthday":"1983/04/24","pay":8431.58},
		{"id":"5","userid":"cmorrison","company":"Ooba","first_name":"Jerry","last_name":"Russell","gender":"Female","email":"jrussell@topicware.info","birthday":"1950/07/02","pay":31385.36}
	];

	dataProvider.setRows(data);
}

var onDoneDataSet = function() {
	gridView.setStyles({
        body: {
            dynamicStyles: [{
                criteria: "state = 'c'",
                styles: "background=#33a1deff"
            }]
        }
    });

    gridView.setStateBar({visible:true})
    gridView.setCheckBar({visible:false})

    function addLog(log) {
	  var prevLog = $("#eventLog").val()
	  $("#eventLog").val(prevLog + log + "\n");
	  $("#eventLog").scrollTop($("#eventLog")[0].scrollHeight);
	};

    dataProvider.onRowInserting = function (provider, row) {
	    addLog("1. onRowInserting이벤트 row: " + row)
	};

	dataProvider.onRowInserted = function (provider, row) {
	    addLog("2. onRowInserted이벤트 row: " + row)
	}

	dataProvider.onRowCountChanged = function (provider, count) {
	    addLog("3. onRowCountChanged이벤트 count: " + count)
	};
}


</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="getValuesField"
  columnSet="getValuesColumn"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption1"
  styleSet="style1"

  dataSet="griddata1.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}