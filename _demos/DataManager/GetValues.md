---
layout: page
title: 그리드의 값 가져오기
order: 6
devbox: true
devboxfile: GetValues-devbox.md
published: true
categories:
  - 데이터 관리
tags: ['data', 'getvalus']
---

LocalDataProvider의 여러 함수를 통해 데이터 셀 및 행들의 값을 가져올 수 있습니다.

<script>
var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
	var data = [
		{"id":"1","userid":"fgray","company":"Dabfeed","first_name":"Jesse","last_name":"Thompson","gender":"Male","email":"jthompson@realcube.com","birthday":"1966/08/13","pay":8792.8},
		{"id":"2","userid":"wcruz","company":"Flipstorm","first_name":"Donna","last_name":"Mason","gender":"Male","email":"dmason@gabspot.biz","birthday":"1965/07/13","pay":19830.69},
		{"id":"3","userid":"creynolds","company":"Divape","first_name":"Antonio","last_name":"Evans","gender":"Female","email":"aevans@dabvine.info","birthday":"1986/08/01","pay":19476.84},
		{"id":"4","userid":"gjackson","company":"Jamia","first_name":"Catherine","last_name":"Watson","gender":"Male","email":"cwatson@pixope.net","birthday":"1983/04/24","pay":8431.58},
		{"id":"5","userid":"cmorrison","company":"Ooba","first_name":"Jerry","last_name":"Russell","gender":"Female","email":"jrussell@topicware.info","birthday":"1950/07/02","pay":31385.36},
		{"id":"6","userid":"rcarr","company":"Gabvine","first_name":"Jennifer","last_name":"Wright","gender":"Female","email":"jwright@bluezoom.com","birthday":"1974/02/20","pay":26488.7},
		{"id":"7","userid":"pcastillo","company":"Avamm","first_name":"Jimmy","last_name":"Hill","gender":"Male","email":"jhill@gigabox.name","birthday":"1958/05/13","pay":25772.22},
		{"id":"8","userid":"wpayne","company":"Shuffletag","first_name":"Victor","last_name":"Price","gender":"Male","email":"vprice@babbleset.info","birthday":"1951/06/07","pay":19590.3},
		{"id":"9","userid":"jthompson","company":"Gigashots","first_name":"Diana","last_name":"Ford","gender":"Female","email":"dford@demizz.name","birthday":"1963/07/15","pay":29945.36},
		{"id":"10","userid":"swallace","company":"Zazio","first_name":"Wanda","last_name":"Nelson","gender":"Male","email":"wnelson@blogtags.net","birthday":"1952/04/10","pay":27895.01}
	];

	dataProvider.setRows(data);
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

  gridWidth="100%"
  gridHeight="300px" %}