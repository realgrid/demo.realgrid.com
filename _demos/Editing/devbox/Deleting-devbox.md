#### 삭제 가능 설정
그리드에서 삭제를 가능하게 하려면 [gridBase.setEditOptions()](http://help.realgrid.com/api/GridBase/setEditOptions/){:target="_blank"}을 사용하여 deletable 속성을 true로 지정하면 됩니다.

<a class="btn primary small round lowercase" id="btnSetEditOptions">설정</a>

```js
gridView.setEditOptions({
  deletable: true  
});
```

#### softDeleting   
[dataProvider.options()](http://help.realgrid.com/api/types/DataProviderOptions/){:target="_blank"}의 softDeleting이 true이면 데이터행을 실제로 삭제하지 않고 행의 상태를 [RowState](http://help.realgrid.com/api/types/RowState/){:target="_blank"}.DELETED 나 [RowState](http://help.realgrid.com/api/types/RowState/){:target="_blank"}.CREATE_AND_DELETED 로 변경합니다.     

<a class="btn primary small round lowercase" id="btnSoftDeleting">softDeleting 설정</a>  
<input type="checkbox" id="chkSoftDeleting"> softDeleting  

```js
dataProvider.setOptions({
  softDeleting: $("#chkSoftDeleting").is(":checked")
})
```

#### deleteCreated   
[dataProvider.options()](http://help.realgrid.com/api/types/DataProviderOptions/){:target="_blank"}의 deleteCreated이 true이면 softDeleting이더라도 행의 상태가 [RowState](http://help.realgrid.com/api/types/RowState/){:target="_blank"}.CREATE인 행을 삭제합니다.  

<a class="btn primary small round lowercase" id="btnDeleteCreated">deleteCreated 설정</a>  
<input type="checkbox" id="chkDeleteCreated"> deleteCreated  

```js
dataProvider.setOptions({
  deleteCreated: $("#chkDeleteCreated").is(":checked")
})
```

#### hideDeletedRows   
[gridBase.options](http://help.realgrid.com/api/types/GridOptions/){:target="_blank"}.hideDeletedRows이 true이면 행의 상태가 [RowState](http://help.realgrid.com/api/types/RowState/){:target="_blank"}.DELETED 나 [RowState](http://help.realgrid.com/api/types/RowState/){:target="_blank"}.CREATE_AND_DELETED인 행을 그리드에서 제외 시킵니다.

<a class="btn primary small round lowercase" id="btnHideDeletedRows">hideDeletedRows 설정</a>  
<input type="checkbox" id="chkHideDeletedRows"> hideDeletedRows  

```js
gridView.setOptions({
  hideDeletedRows: $("#chkHideDeletedRows").is(":checked")
})
```

#### 행 삭제   
리얼그리드에서 행을 삭제하는 방법은 몇가지가 있습니다. 각 기능을 확인해보시기 바랍니다.

`1`. 사용자가 `Ctrl`+`Del`키 입력으로 삭제  
`2`. [GridBase.deleteSelection()](http://help.realgrid.com/api/GridBase/deleteSelection/){:target="_blank"}  

<a class="btn primary small round lowercase" id="btnDeleteSelection">deleteSelection()</a>

```js
gridView.deleteSelection(true); // true이면 editOptions.deleteRowsConfirm이 true여도 메세지 확인없이 즉시 삭제한다.
```

`3`. [dataProvider.removeRow()](http://help.realgrid.com/api/LocalDataProvider/removeRow/){:target="_blank"}, [dataProvider.removeRows()](http://help.realgrid.com/api/LocalDataProvider/removeRows/){:target="_blank"}  

<a class="btn primary small round lowercase" id="btnRemoveRow">removeRow()</a>

```js
var curr = gridView.getCurrent();
dataProvider.removeRow(curr.dataRow);
```

<script>

  $('#btnSetEditOptions').click(function() {
    gridView.setEditOptions({
      deletable: true  
    });
  });

  $('#btnSoftDeleting').click(function() {
    dataProvider.setOptions({
      softDeleting: $("#chkSoftDeleting").is(":checked")
    })
  });  

  $('#btnDeleteCreated').click(function() {
    dataProvider.setOptions({
      deleteCreated: $("#chkDeleteCreated").is(":checked")
    })
  });

  $('#btnHideDeletedRows').click(function() {
    gridView.setOptions({
      hideDeletedRows: $("#chkHideDeletedRows").is(":checked")
    })
  });

  $('#btnDeleteSelection').click(function() {
    gridView.deleteSelection(true);
  });

  $('#btnRemoveRow').click(function() {
    var curr = gridView.getCurrent();
    dataProvider.removeRow(curr.dataRow);
  });  

</script>
