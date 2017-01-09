---
layout: page
title: 롤백
order: 9
devbox: true
devboxfile: DataRollback-devbox.md
published: true
categories:
  - 데이터 관리
tags: ['data', 'rollback']
---

loadData() 함수 등으로 데이터셋을 처음 가져올 때나 혹은 데이터셋이 변경된 후 특정 시점(savePoint)에, DataProvider에 저장되어 있는 데이터셋의 전체 복사본을 별도로 저장해 두고 이 후에 이 값들로 DataProvider를 복원(rollback) 시킬 수 있습니다.

<script>
var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
	var data = [
		{"id":"1","userid":"jwagner","company":"Mynte","first_name":"Theresa","last_name":"Reynolds","gender":"Female","email":"treynolds@gabspot.net","city":"Sutter Creek","ip_address":"167.206.87.187","birthday":"1990-01-29T15:00:00.000Z","pay":18461.49,"card_number":"4017956479311942","card_type":"visa"},
		{"id":"2","userid":"tphillips","company":"Zazio","first_name":"Raymond","last_name":"Tucker","gender":"Female","email":"rtucker@meejo.mil","city":"Visalia","ip_address":"171.102.222.145","birthday":"1978-08-04T15:00:00.000Z","pay":31811.66,"card_number":"3537454864902429","card_type":"jcb"},
		{"id":"3","userid":"bmendoza","company":"Edgeify","first_name":"Emily","last_name":"Flores","gender":"Female","email":"eflores@mynte.org","city":"Gonzales","ip_address":"32.149.138.138","birthday":"1962-06-09T15:00:00.000Z","pay":23145.71,"card_number":"3574848246092110","card_type":"jcb"},
		{"id":"4","userid":"phicks","company":"Nlounge","first_name":"Johnny","last_name":"Reed","gender":"Female","email":"jreed@blogspan.com","city":"Soledad","ip_address":"247.130.92.101","birthday":"1967-08-10T15:00:00.000Z","pay":10032.74,"card_number":"3571523163079340","card_type":"jcb"},
		{"id":"5","userid":"tbanks","company":"Yodoo","first_name":"David","last_name":"Miller","gender":"Female","email":"dmiller@quatz.info","city":"Stockton","ip_address":"48.31.72.6","birthday":"1972-06-29T15:00:00.000Z","pay":50777.05,"card_number":"374622785310243","card_type":"americanexpress"},
		{"id":"6","userid":"ekennedy","company":"Shufflester","first_name":"Lois","last_name":"Bailey","gender":"Male","email":"lbailey@meemm.name","city":"Los Gatos","ip_address":"147.42.142.19","birthday":"1952-12-08T15:00:00.000Z","pay":22400.54,"card_number":"5602245880215027","card_type":"china-unionpay"},
		{"id":"7","userid":"avasquez","company":"Edgetag","first_name":"Rachel","last_name":"Gonzales","gender":"Male","email":"rgonzales@livepath.com","city":"Atascadero","ip_address":"165.226.157.172","birthday":"1954-12-21T15:00:00.000Z","pay":7952.76,"card_number":"6709735293733863","card_type":"laser"},
		{"id":"8","userid":"belliott","company":"Linklinks","first_name":"Scott","last_name":"Allen","gender":"Female","email":"sallen@wordify.edu","city":"Tracy","ip_address":"0.185.122.187","birthday":"1954-02-13T15:00:00.000Z","pay":12720.97,"card_number":"3573722642979827","card_type":"jcb"},
		{"id":"9","userid":"rwarren","company":"Gabvine","first_name":"Cheryl","last_name":"Schmidt","gender":"Female","email":"cschmidt@nlounge.info","city":"Vacaville","ip_address":"81.68.106.206","birthday":"1980-07-05T15:00:00.000Z","pay":13043.84,"card_number":"6759123799705660","card_type":"switch"},
		{"id":"10","userid":"mparker","company":"LiveZ","first_name":"Bobby","last_name":"Hill","gender":"Female","email":"bhill@yakidoo.net","city":"Pico Rivera","ip_address":"113.203.72.110","birthday":"1980-03-02T15:00:00.000Z","pay":29194.12,"card_number":"201657149050795","card_type":"diners-club-enroute"},
		{"id":"11","userid":"bgriffin","company":"Twitterbridge","first_name":"Judy","last_name":"Jenkins","gender":"Female","email":"jjenkins@fliptune.name","city":"Pismo Beach","ip_address":"104.43.253.168","birthday":"1979-01-01T15:00:00.000Z","pay":42293.38,"card_number":"633110113639811526","card_type":"switch"},
		{"id":"12","userid":"sbowman","company":"Flipstorm","first_name":"Larry","last_name":"Gutierrez","gender":"Female","email":"lgutierrez@yamia.info","city":"Orange Cove","ip_address":"33.51.56.230","birthday":"1986-09-20T15:00:00.000Z","pay":15375.39,"card_number":"3542271042541504","card_type":"jcb"},
		{"id":"13","userid":"hmason","company":"Jayo","first_name":"Lois","last_name":"Pierce","gender":"Female","email":"lpierce@bubblebox.name","city":"Beaumont","ip_address":"195.7.164.200","birthday":"1975-07-03T15:00:00.000Z","pay":13095.55,"card_number":"3551451682164134","card_type":"jcb"},
		{"id":"14","userid":"wryan","company":"Demimbu","first_name":"Tammy","last_name":"Rice","gender":"Male","email":"trice@meejo.com","city":"Pasadena","ip_address":"131.82.224.13","birthday":"1952-11-07T15:00:00.000Z","pay":33343.55,"card_number":"5570824087013365","card_type":"mastercard"},
		{"id":"15","userid":"lpatterson","company":"Meembee","first_name":"Henry","last_name":"Ferguson","gender":"Male","email":"hferguson@ozu.net","city":"Imperialg Beach","ip_address":"123.77.131.1","birthday":"1970-10-10T15:00:00.000Z","pay":32783.46,"card_number":"4405782619325471","card_type":"visa-electron"},
		{"id":"16","userid":"rlong","company":"Meevee","first_name":"Michelle","last_name":"Medina","gender":"Female","email":"mmedina@youopia.gov","city":"Santa Ana","ip_address":"72.204.212.87","birthday":"1961-03-10T15:00:00.000Z","pay":32348.3,"card_number":"633110036509424304","card_type":"switch"},
		{"id":"17","userid":"gphillips","company":"Brightdog","first_name":"Maria","last_name":"Watkins","gender":"Male","email":"mwatkins@flipbug.com","city":"Vernon","ip_address":"172.124.180.159","birthday":"1980-03-18T15:00:00.000Z","pay":5213.96,"card_number":"5010123865129354","card_type":"mastercard"},
		{"id":"18","userid":"gsanders","company":"Jatri","first_name":"Adam","last_name":"Kelly","gender":"Female","email":"akelly@tambee.mil","city":"Chula Vista","ip_address":"193.96.228.128","birthday":"1950-12-29T15:00:00.000Z","pay":36717.96,"card_number":"4913671639548243","card_type":"visa-electron"},
		{"id":"19","userid":"rburns","company":"Kazu","first_name":"Aaron","last_name":"Green","gender":"Female","email":"agreen@feednation.net","city":"Chico","ip_address":"55.157.206.62","birthday":"1976-04-19T15:00:00.000Z","pay":29629.4,"card_number":"3582525119185953","card_type":"jcb"},
		{"id":"20","userid":"jknight","company":"Photobean","first_name":"Mildred","last_name":"Alvarez","gender":"Female","email":"malvarez@mybuzz.info","city":"Healdsburg","ip_address":"75.174.233.128","birthday":"1985-05-25T15:00:00.000Z","pay":49030.98,"card_number":"3573163947300601","card_type":"jcb"}
	];

	dataProvider.setRows(data);

	dataProvider.savePoint();
    refreshPoints();
}

var onDoneDataSet = function() {
	
}


</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="dataRollBackFields"
  columnSet="dataRollBackColumns"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption1"
  styleSet="style1"

  dataSet="griddata1.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}