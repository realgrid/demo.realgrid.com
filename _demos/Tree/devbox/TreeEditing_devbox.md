
#### 추가

[TreeDataProvider.addChildRow()](http://help.realgrid.com/api/TreeDataProvider/addChildRow/)
[TreeDataProvider.insertChildRow()](http://help.realgrid.com/api/TreeDataProvider/insertChildRow/)

<a class="btn primary small round lowercase" id="addChildRow">추가</a>


```js
// 체크바 보이기/감추기
treeView.addChildRow({});
```

#### 수정

[DataProvider.updateRow()](http://help.realgrid.com/api/DataProvider/updateRow/)
[DataProvider.updateStrictRow()](http://help.realgrid.com/api/DataProvider/updateStrictRow/)


#### 삭제

[DataProvider.clearRows()](http://help.realgrid.com/api/DataProvider/clearRows/)
[GridBase.deleteSelection()](http://help.realgrid.com/api/GridBase/deleteSelection/)
[TreeDataProvider.removeRow()](http://help.realgrid.com/api/TreeDataProvider/removeRow/)
[TreeDataProvider.removeRows()](http://help.realgrid.com/api/TreeDataProvider/removeRows/)


<script>
  $('#addChildRow').click(function() {
    treeView.addChildRow({});
  });
</script>
