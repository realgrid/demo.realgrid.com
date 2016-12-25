
#### 1 DataProvider - 2 GridView

GridView와 DataProvider를 연결하기 위해서는 [GridBase.setDataSource()](http://help.realgrid.com/api/GridBase/setDataSource/) 또는 [setDataProvider()](http://help.realgrid.com/api/GridBase/setDataProvider/)함수를 사용합니다.

<a class="btn primary small round lowercase" id="setDataSource1">첫 번째 그리드에 데이터 연결</a>

```js
// 첫 번째 그리드의 변수는 gridView1
gridView1.setDataProvider(dataProvider1);
```

오른쪽 그리드에도 동일한 DataProvider를 연결해 보겠습니다.

<a class="btn primary small round lowercase" id="setDataSource2">두 번째 그리드에 데이터 연결</a>

```js
// 두 번째 그리드의 변수는 gridView2
gridView2.setDataProvider(dataProvider1);
```

#### 데이터 변경

여려 개의 그리드에 연결된 하나의 DataProvider의 값을 변경하면 연결된 모든 그리드에 모두 변경된 값이 표시 됩니다.

<a class="btn primary small round lowercase" id="setValues">DataProvider의 값 변경하기</a>

```js
dataProvider1.setValue(1,2,10);
dataProvider1.setValue(4,'2001',80);
dataProvider1.setValue(4,'2002',30);
```

<script>
$('#setDataSource1').click(function() {
  gridView1.setDataProvider(dataProvider1);
});

$('#setDataSource2').click(function() {
  gridView2.setDataProvider(dataProvider1);
});

$('#setValues').click(function() {
  dataProvider1.setValue(1,2,10);
  dataProvider1.setValue(4,'2001',80);
  dataProvider1.setValue(4,'2002',30);
});
</script>
