#### 삽입 / 추가 가능 설정
그리드에서 삽입과 추가를 가능하게 하려면 [setEditOptions()](http://help.realgrid.com/api/GridBase/setEditOptions/){:target="_blank"}을 사용하여 insertable, appendable 속성을 true로 지정하면 됩니다.

<a class="btn primary small round lowercase" id="btnSetEditOptions">설정</a>

```js
gridView.setEditOptions({
  insertable: true,
  appendable: true  
});
```

#### 행 삽입   
[editOptions](http://help.realgrid.com/api/types/EditOptions/){:target="_blank"}.insertable이 true일때 사용자가 `Insert` key로 행을 삽입할 수 있습니다. `Shift` + `Insert` Key로도 행 삽입이 가능하며 이 경우 현재 선택된 행 아래에 행이 추가 됩니다.   

[beginInsertRow()](http://help.realgrid.com/api/GridView/beginInsertRow/){:target="_blank"}를 통한 행 삽입   

<a class="btn primary small round lowercase" id="btnBeginInsertRow">행 삽입(지정행 이전)</a>

```js
var curr = gridView.getCurrent();
gridView.beginInsertRow(Math.max(0, curr.itemIndex), false);
gridView.showEditor();
gridView.setFocus();
```

<a class="btn primary small round lowercase" id="btnBeginInsertRowShift">행 삽입(지정행 이후)</a>

```js
var curr = gridView.getCurrent();
gridView.beginInsertRow(Math.max(0, curr.itemIndex), true);
gridView.showEditor();
gridView.setFocus();
```

#### 행 추가   
[editOptions](http://help.realgrid.com/api/types/EditOptions/){:target="_blank"}.appendable이 true일때 가장 마지막 행에서 사용자가 `Down Arrow` key로 행을 추가할 수 있습니다.

[beginAppendRow()](http://help.realgrid.com/api/GridView/beginAppendRow/){:target="_blank"}를 통한 행 삽입   

<a class="btn primary small round lowercase" id="btnBeginAppendRow">행 추가</a>

```js
gridView.beginAppendRow();
gridView.showEditor();
gridView.setFocus();
```

<script>

  $('#btnSetEditOptions').click(function() {
    gridView.setEditOptions({
      insertable: true,
      appendable: true  
    });
  });

  $('#btnBeginInsertRow').click(function() {
    var curr = gridView.getCurrent();
    gridView.beginInsertRow(Math.max(0, curr.itemIndex));
    gridView.showEditor();
    gridView.setFocus();
  });

  $('#btnBeginInsertRowShift').click(function() {
    var curr = gridView.getCurrent();
    gridView.beginInsertRow(Math.max(0, curr.itemIndex), true);
    gridView.showEditor();
    gridView.setFocus();
  });

  $('#btnBeginAppendRow').click(function() {
    gridView.beginAppendRow();
    gridView.showEditor();
    gridView.setFocus();
  });

</script>
