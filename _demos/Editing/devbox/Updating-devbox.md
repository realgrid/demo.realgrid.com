#### 편집 가능 설정
그리드에서 편집을 가능하게 하려면 [setEditOptions()](http://help.realgrid.com/api/GridBase/setEditOptions/){:target="_blank"}을 사용하여 editable, updatable 속성을 true로 지정하면 됩니다. 해당 속성의 기본값은 true 입니다.


<a class="btn primary small round lowercase" id="btnSetEditOptions">설정</a>

```js
gridView.setEditOptions({
  editable: true,
  updatable: true  
});
```

#### 편집 

[beginUpdateRow()](http://help.realgrid.com/api/GridView/beginUpdateRow/){:target="_blank"}를 통한 편집   

<a class="btn primary small round lowercase" id="btnBeginUpdateRow">편집</a>

```js
var curr = gridView.getCurrent();
gridView.beginUpdateRow(curr.itemIndex);
gridView.showEditor();
gridView.setFocus();
```

#### DataProvider에 편집 값이 전달된 시점    
그리드에서 편집이 완료되면 편집된 값들은 dataProvider에 전달이 됩니다. 이때 [dataProvider.onRowUpdating()](http://help.realgrid.com/api/LocalDataProvider/onRowUpdating/){:target="_blank"} 이벤트가 발생하며 false를 리턴하면 편집이 취소  됩니다.    


<a class="btn primary small round lowercase" id="btnOnRowUpdating">onRowUpdating</a>

```js
dataProvider.onRowUpdating = function (provider, row) {
  var item = gridView.getEditingItem(); // 현재 편집 중인 행 정보와 값을 가져옵니다.
  if (item) { 
    if (item.values["OrderID"] <= 100) {
      setTimeout(function () { alert('OrderID must be greater than 100 !'); }, 10);
      return false; // false를 리턴하면 DataProvider에 저장되지 않습니다.
    }
  }
  return true;
}
```

#### DataProvider에 편집 값이 저장 완료된 시점   
편집이 완료되면 [dataProvider.onRowUpdating()](http://help.realgrid.com/api/LocalDataProvider/onRowUpdating/){:target="_blank"} 발생 후 dataProvider에 저장이 완료되면 [dataProvider.onRowUpdated()](http://help.realgrid.com/api/LocalDataProvider/onRowUpdated/){:target="_blank"}가 발생 합니다.  

<a class="btn primary small round lowercase" id="btnOnRowUpdated">onRowUpdated</a>

```js
dataProvider.onRowUpdated = function (provider, row) {
  var r = provider.getJsonRow(row);
  alert(JSON.stringify(r));
}
```

<script>

  $('#btnSetEditOptions').click(function() {
    gridView.setEditOptions({
      editable: true,
      updatable: true  
    });
  });

  $('#btnBeginUpdateRow').click(function() {
    var curr = gridView.getCurrent();
    gridView.beginUpdateRow(curr.itemIndex);
    gridView.showEditor();
    gridView.setFocus();
  });

  $('#btnOnRowUpdating').click(function() {
    dataProvider.onRowUpdating = function (provider, row) {
      var item = gridView.getEditingItem(); // 현재 편집 중인 행 정보와 값을 가져옵니다.
      if (item) { 
        if (item.values["OrderID"] <= 100) {
          setTimeout(function () { alert('OrderID must be greater than 100 !'); }, 0);
          return false; // false를 리턴하면 DataProvider에 저장되지 않습니다.
        }
      }
      return true;
    }
  });

  $('#btnOnRowUpdated').click(function() {
    dataProvider.onRowUpdated = function (provider, row) {
      var r = provider.getJsonRow(row);
      alert(JSON.stringify(r));
    }
  });

</script>
