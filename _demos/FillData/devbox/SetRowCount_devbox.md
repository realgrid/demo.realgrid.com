
#### 행의 갯수 지정하기

DataProvider에 행의 갯수를 지정하기 위해 [LocalDataProvider.setRowCount()](http://help.realgrid.com/api/LocalDataProvider/setRowCount/)함수를 사용합니다.

<a class="btn primary small round lowercase" id="setRowCount1">행의 갯수 10개로 지정</a>

```js
dataProvider.setRowCount(10);
```

함수에서 갯수를 지정하기 위한 `newCount`인자는 기존의 데이터를 포함한 전체 행의 갯수를 의미 합니다. 따라서 10개 행으로 지정하면 원래있던 5개행 + 새로추가 된 5개행 이 됩니다.

이 함수는 현재 DataProvider에 있는 데이터의 갯수와 새로 추가될 행의 갯수를 비교하여 실제로 추가될 행의 갯수를 지정합니다. 즉, 지정된 갯수가 현재행 보다 많은 경우 그 차이 만큼만 추가하고, 지정된 갯수가 적은 경우 남은 행의 데이터는 삭제 합니다.

<a class="btn primary small round lowercase" id="setRowCount2">행의 갯수 3개로 지정</a>

```js
dataProvider.setRowCount(3);
```


#### 빈 행 채울때 기본값 적용하기

[LocalDataProvider.setRowCount()](http://help.realgrid.com/api/LocalDataProvider/setRowCount/)함수로 빈 행을 채울때 기본값을 지정하기 위한 두 개의 인자가 있습니다.

- `fillFieldDefaults` - `true`면 [DataField.defaultValue](http://help.realgrid.com/api/types/DataField/)에 지정된 값으로 해당 필드를 초기화 합니다.
- `defaultValues` - 초기화 할 값을 배열로 지정합니다.

<a class="btn primary small round lowercase" id="setRowCount3">제조국 국산으로 기본값 지정, 11개행 추가</a>

```js
dataProvider.setRowCount(11, false, ['', '국산']);
```


<script>
$('#setRowCount1').click(function() {
  dataProvider.setRowCount(10);
});

$('#setRowCount2').click(function() {
  dataProvider.setRowCount(3);
});

$('#setRowCount3').click(function() {
  dataProvider.setRowCount(11, false, ['', '국산']);
});
</script>
