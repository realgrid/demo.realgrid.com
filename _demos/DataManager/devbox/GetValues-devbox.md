#### 그리드 값을 가져오기 위한 함수들

아래는 `dataProvider`의 값을 가져오기 위한 함수들이 있습니다.

* [getValue(row, field)](http://help.realgrid.com/api/LocalDataProvider/getValue/)
* [getValues(row)](http://help.realgrid.com/api/DataProvider/getValues/)
* [getJsonRow(row)](http://help.realgrid.com/api/LocalDataProvider/getJsonRow/)
* [getRows(startRow, endRow)](http://help.realgrid.com/api/LocalDataProvider/getRows/)
* [getJsonRows(startRow, endRow)](http://help.realgrid.com/api/LocalDataProvider/getJsonRows/)
* [getFieldValues(field, startRow, endRow)](http://help.realgrid.com/api/LocalDataProvider/getFieldValues/)

#### 그리드 값 가져오기

현재 포커스 위치의 `row`와 `field`값에 해당하는 `value` 값을 가져올 수 있습니다.

<a class="btn primary small round lowercase" id="getValue">getValue</a>

```js
var current = gridView.getCurrent();
var value = dataProvider.getValue(current.dataRow, current.fieldName);
alert("row: " + current.dataRow +  "\n" + "field: " + current.fieldName + "\n" + "value: " + value);
```

한 행의 필드값들이 순서대로 들어있는 `Array`로 가져올 수 있습니다.

<a class="btn primary small round lowercase" id="getValues">getValues</a>

```js
var current = gridView.getCurrent();
alert("row: " + current.dataRow + "\n" + dataProvider.getValues(current.dataRow));
```

한 행의 값을 `Json객체`로 가져올 수 있습니다.

<a class="btn primary small round lowercase" id="getJsonRow">getJsonRow</a>

```js
var current = gridView.getCurrent();
var jsonData = dataProvider.getJsonRow(current.dataRow)
alert("row: " + current.dataRow + "\n" + JSON.stringify(JsonData));
```

여러 행의 데이터를 `Array의 Array`로 가져올 수 있습니다.  
`startRow`는 기본 0이며 0보다 작으면 첫번째 행부터 가져옵니다.  
`endRow`는 기본 -1이며 -1이면 마지막 행 까지 가져옵니다.

<a class="btn primary small round lowercase" id="getRows">getRows</a>

```js
alert(dataProvider.getRows(0, -1));
```

여러 행의 데이터를 `Json객체의 Array`로 가져올 수 있습니다.  
`startRow`는 기본 0이며 0보다 작으면 첫번째 행부터 가져옵니다.  
`endRow`는 기본 -1이며 -1이면 마지막 행 까지 가져옵니다.

<a class="btn primary small round lowercase" id="getJsonRows">getJsonRows</a>

```js
alert(JSON.stringify(dataProvider.getJsonRows(0, -1)));
```

현재 포커스 위치의 한 필드 값들을 지정한 행 범위만큼 `Array`로 가져올 수 있습니다.

<a class="btn primary small round lowercase" id="getFieldValues">getFieldValues</a>

```js
var current = gridView.getCurrent();
alert("field: " + current.fieldName + "\n" + "fieldValues: " + dataProvider.getFieldValues(current.fieldName, 0, -1));
```

<script>
$('#getValue').click(function() {
	var current = gridView.getCurrent();
	var value = dataProvider.getValue(current.dataRow, current.fieldName)
	alert("row: " + current.dataRow +  "\n" + "field: " + current.fieldName + "\n" + "value: " + value);
});

$('#getValues').click(function() {
	var current = gridView.getCurrent();
	alert("row: " + current.dataRow + "\n" + dataProvider.getValues(current.dataRow));
});

$('#getJsonRow').click(function() {
	var current = gridView.getCurrent();
	var jsonData = dataProvider.getJsonRow(current.dataRow)
	alert("row: " + current.dataRow + "\n" + JSON.stringify(jsonData));
});

$('#getRows').click(function() {
	alert(dataProvider.getRows(0, -1));
});

$('#getJsonRows').click(function() {
	alert(JSON.stringify(dataProvider.getJsonRows(0, -1)));
});

$('#getFieldValues').click(function() {
	var current = gridView.getCurrent();
	alert("field: " + current.fieldName + "\n" + "fieldValues: " + dataProvider.getFieldValues(current.fieldName, 0, -1));
});
</script>