#### 그리드 값을 넣기 위한 함수들

아래는 `dataProvider`의 값을 넣기 위한 함수들이 있습니다.

* [setValue(row, field, value)](http://help.realgrid.com/api/LocalDataProvider/setValue/)
* [updateRow(row, values)](http://help.realgrid.com/api/DataProvider/updateRow/)
* [updateStricRow(row, values)](http://help.realgrid.com/api/DataProvider/updateStrictRow/)
* [updateRows(row, rows, start, count, rowEvents)](http://help.realgrid.com/api/LocalDataProvider/updateRows/)
* [updateStrictRows(row, rows, start, count, rowEvents)](http://help.realgrid.com/api/LocalDataProvider/updateStrictRows/)

#### 그리드에 값 넣기

데이터 셀(한 행의 한 필드)의 값을 변경할 수 있습니다.

<a class="btn primary small round lowercase" id="setValue">setValue</a>

```js
var current = gridView.getCurrent();
var row = current.dataRow;
var field = current.fieldIndex;

var value = "Cell (" + field + ", " + row + ")";
dataProvider.setValue(row, field, value);
```

지정한 데이터행의 모든 필드 값들을 수정할 수 있습니다.  
values는 `Json`, `Array`형태 또는 `Array of Array`형태로 전달합니다.

<a class="btn primary small round lowercase" id="updateRow">updateRow</a>

```js
var row = gridView.getCurrent().dataRow;
var values = {
    id: "1111",
    userid: "userid1",
    company: "company1",
    first_name: undefined,
    last_name: undefined,
    gender:undefined,
    email: undefined,
    birthday: undefined,
    pay: undefined
};

dataProvider.updateRow(row, values);
```

지정한 데이터행의 필드 값들을 수정합니다.  
`undefined로 지정하거나 명시되지 않은 경우 기존의 값을 유지합니다.`

<a class="btn primary small round lowercase" id="updateStrictRow">updateStrictRow</a>

```js
var row = gridView.getCurrent().dataRow;
var values = {
    id: "1111",
    userid: "userid1",
    company: "company1",
    first_name: undefined,
    last_name: undefined,
    gender:undefined,
    email: undefined,
    birthday: undefined,
    pay: undefined
};
dataProvider.updateStrictRow(row, values);
```

지정한 데이터 행으로부터 한 행 이상의 값을 수정합니다.  
`row`로 설정한 행 위치부터 `rows`에 저장된 배열의 `시작위치(start)`와 `행의 개수(count)`만큼의 데이터로 한 행 이상 값을 수정합니다.

<a class="btn primary small round lowercase" id="updateRows">updateRows</a>

```js
var row = gridView.getCurrent().dataRow;
var rows = [
    ["1234", "userid3", "company3", undefined, undefined, undefined, undefined, undefined, undefined], // Array
    {id:"5678", userid:"userid4", company:"company4", first_name: undefined, last_name: undefined, gender:undefined, email: undefined, birthday: undefined, pay: undefined}, // Object
    {id:"1357", userid:"userid5", company:"company5", first_name: undefined, last_name: undefined, gender:undefined, email: undefined, birthday: undefined, pay: undefined},
    {id:"2468", userid:"userid6", company:"company6", first_name: undefined, last_name: undefined, gender:undefined, email: undefined, birthday: undefined, pay: undefined}
];

dataProvider.updateRows(row, rows, 0, 2, false);
```

지정한 데이터 행으로부터 한 행 이상의 값을 수정합니다.  
`row`로 설정한 행 위치부터 `rows`에 저장된 배열의 `시작위치(start)`와 `행의 개수(count)`만큼의 데이터로 한 행 이상 값을 수정합니다.  
`undefined로 지정하거나 명시되지 않은 경우 기존의 값을 유지합니다.`

<a class="btn primary small round lowercase" id="updateStrictRows">updateStrictRows</a>

```js
var row = gridView.getCurrent().dataRow;
var rows = [
    ["1234", "userid3", "company3", undefined, undefined, undefined, undefined, undefined, undefined], // Array
    {id:"5678", userid:"userid4", company:"company4", first_name: undefined, last_name: undefined, gender:undefined, email: undefined, birthday: undefined, pay: undefined}, // Object
    {id:"1357", userid:"userid5", company:"company5", first_name: undefined, last_name: undefined, gender:undefined, email: undefined, birthday: undefined, pay: undefined},
    {id:"2468", userid:"userid6", company:"company6", first_name: undefined, last_name: undefined, gender:undefined, email: undefined, birthday: undefined, pay: undefined}
];
 
dataProvider.updateStrictRows(row, rows, 0, 3, false);
```


#### 주의사항

DataProvider의 데이터 함수를 호출하는 시점에 그리드가 편집 중이라면 `"Clinet is editing"` 에러가 발생하게 됩니다.  
사용자 편집과 DataProvider 함수 호출을 동시에 진행할 수 없습니다.  
반드시 [gridView.commit()](http://help.realgrid.com/api/GridBase/commit/), [gridView.cancel()](http://help.realgrid.com/api/GridBase/cancel/) 호출로 먼저 사용자 편집을 완료한 후 dataProvider 함수를 호출해야 합니다.

<script>
$('#setValue').click(function() {
	var current = gridView.getCurrent();
	var row = current.dataRow;
	var field = current.fieldIndex;

	var value = "Cell (" + field + ", " + row + ")";
	dataProvider.setValue(row, field, value);
});

$('#updateRow').click(function() {
	var row = gridView.getCurrent().dataRow;
	var values = {
        id: "1111",
	    userid: "userid1",
	    company: "company1",
	    first_name: undefined,
	    last_name: undefined,
	    gender:undefined,
	    email: undefined,
	    birthday: undefined,
	    pay: undefined
	};

	dataProvider.updateRow(row, values);
});

$('#updateStrictRow').click(function() {
	var row = gridView.getCurrent().dataRow;
	var values = {
        id: "1111",
	    userid: "userid1",
	    company: "company1",
	    first_name: undefined,
	    last_name: undefined,
	    gender:undefined,
	    email: undefined,
	    birthday: undefined,
	    pay: undefined
	};
	dataProvider.updateStrictRow(row, values);
});

$('#updateRows').click(function() {
	var row = gridView.getCurrent().dataRow;
	var rows = [
	    ["1234", "userid3", "company3", undefined, undefined, undefined, undefined, undefined, undefined],
	    {id:"5678", userid:"userid4", company:"company4", first_name: undefined, last_name: undefined, gender:undefined, email: undefined, birthday: undefined, pay: undefined},
	    {id:"1357", userid:"userid5", company:"company5", first_name: undefined, last_name: undefined, gender:undefined, email: undefined, birthday: undefined, pay: undefined},
    	{id:"2468", userid:"userid6", company:"company6", first_name: undefined, last_name: undefined, gender:undefined, email: undefined, birthday: undefined, pay: undefined}
	];

	dataProvider.updateRows(row, rows, 0, 2, false);
});

$('#updateStrictRows').click(function() {
	var row = gridView.getCurrent().dataRow;
	var rows = [
	    ["1234", "userid3", "company3", undefined, undefined, undefined, undefined, undefined, undefined], // Array
	    {id:"5678", userid:"userid4", company:"company4", first_name: undefined, last_name: undefined, gender:undefined, email: undefined, birthday: undefined, pay: undefined}, // Object
	    {id:"1357", userid:"userid5", company:"company5", first_name: undefined, last_name: undefined, gender:undefined, email: undefined, birthday: undefined, pay: undefined},
	    {id:"2468", userid:"userid6", company:"company6", first_name: undefined, last_name: undefined, gender:undefined, email: undefined, birthday: undefined, pay: undefined}
	];
	 
	dataProvider.updateStrictRows(row, rows, 0, 3, false);
});
</script>