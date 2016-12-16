#### 데이터를 추가하기 위한 함수들

사용자가 입력한 정보 등을 이용하여 DataPrvoider에 한 행을 추가할 수 있는 함수들 입니다.

* [addRow(values)](http://help.realgrid.com/api/LocalDataProvider/addRow/)
* [insertRow(row, values)](http://help.realgrid.com/api/LocalDataProvider/insertRow/)

#### 데이터 행 추가

LocalDataProvider의 마지막 행 다음에 새로운 행을 추가합니다.

<a class="btn primary small round lowercase" id="addRow">addRow</a>

```js
var values = ["", "addRow", "회사", "이름", "성", "성별", "E-Mail"];
dataProvider.addRow(values);
```

LocalDataProvider의 특정 행 위치에 새로운 행을 추가합니다.

<a class="btn primary small round lowercase" id="insertRow">insertRow</a>

```js
var row = gridView.getCurrent().dataRow;
var values = ["", "insertRow", "회사", "이름", "성", "성별", "E-Mail"];
dataProvider.insertRow(row, values);
```


#### 행 추가 이벤트

행 추가하기 직전에 [onRowInserting()](http://help.realgrid.com/api/LocalDataProvider/onRowInserting/), 호출된 후 [onRowInserted()](http://help.realgrid.com/api/LocalDataProvider/onRowInserted/), [onRowCountChanged()](http://help.realgrid.com/api/LocalDataProvider/onRowCountChanged/) 순서대로 이벤트가 발생합니다.  
행 추가시 발행하는 이벤트들의 순서를 확인하세요.

<textarea id="eventLog" style="width:100%; height:200px"></textarea>

행 추가하기 직전에 발생하는 이벤트입니다.

[onRowInserting()](http://help.realgrid.com/api/LocalDataProvider/onRowInserting/)


```js
dataProvider.onRowInserting = function (provider, row) {
    addLog("1. onRowInserting이벤트 row = " + row)
};
```

행이 추가된 후 발생하는 이벤트입니다.

[onRowInserted()](http://help.realgrid.com/api/LocalDataProvider/onRowInserted/)

```js
dataProvider.onRowInserted = function (provider, row) {
    addLog("2. onRowInserted이벤트 row = " + row)
}
```

행 추가 및 삭제 등으로 행의 개수가 변경됐을 때 발생하는 이벤트입니다.

[onRowCountChanged()](http://help.realgrid.com/api/LocalDataProvider/onRowCountChanged/)

```js
dataProvider.onRowCountChanged = function (provider, count) {
    addLog("3. onRowCountChanged이벤트 count = " + count)
};
```


<script>
	$('#addRow').click(function() {
		var values = ["", "addRow", "회사", "이름", "성", "성별", "E-Mail"];
		dataProvider.addRow(values);
	});

	$('#insertRow').click(function() {
		var row = gridView.getCurrent().dataRow;
		var values = ["", "insertRow", "회사", "이름", "성", "성별", "E-Mail"];
		dataProvider.insertRow(row, values);
	});
</script>