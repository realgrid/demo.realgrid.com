#### [행 상태(RowState)](http://help.realgrid.com/api/types/RowState/){:target="_blank"}의 종류
`none` : 로드된 후 변경이 없는 상태.  
`created` : 새로 추가된 행의 상태.  
`updated` : 로드된 후 하나 이상의 필드 값이 변경된 상태. `created` 행은 값이 변경 되어도 `updated`로 변경되지 않습니다.  
`deleted` : 로드된 후 삭제된 행의 상태.   
`createAndDeleted` : 추가된 후 삭제한 행의 상태.  

`deleted`나 `createAndDeleted` 상태는 dataProvider.options.softDeleting 의 값이 true 일 경우에만 가질 수 있습니다. softDeleting = false 라면 행 삭제시 행 상태를 바꾸지 않고 바로 dataProvider에서 삭제하기 때문 입니다.  

#### 사용자 입력에 의한 행 상태 변경   
그리드에 표시된 값을 수정하거나 아래 키 입력을 통해 행의 상태가 변경 됩니다.   
`Ctrl`+`Del` : 현재 행 혹은 선택 행들 삭제   
`Ins` : 현재 위치에 행 삽입   
`Down Arrow` : 마지막 행에서 행 추가   


#### API에 의한 행 상태 변경
[dataProvider.setRowState](http://help.realgrid.com/api/DataProvider/setRowState/){:target="_blank"}, [dataProvider.setRowStates](http://help.realgrid.com/api/DataProvider/setRowStates/){:target="_blank"}를 사용하여 행의 상태를 변경할 수 있습니다.

**행 상태**  
<input type="radio" name="rbRowState" value="created" checked="checked"> created
<input type="radio" name="rbRowState" value="updated"> updated
<input type="radio" name="rbRowState" value="deleted"> deleted
<input type="radio" name="rbRowState" value="createAndDeleted"> createAndDeleted
<input type="radio" name="rbRowState" value="none"> none

<a class="btn primary small round lowercase" id="btnSetRowState">setRowState
</a>

```js
var curr = gridView.getCurrent();
var state = $(':radio[name="rbRowState"]:checked').val()
dataProvider.setRowState(curr.dataRow, state, true);
```

<a class="btn primary small round lowercase" id="btnSetRowStates">setRowStates(체크바에 체크된 행들을 변경)
</a>

```js
var dataRows = gridView.getCheckedRows();
var state = $(':radio[name="rbRowState"]:checked').val()
dataProvider.setRowStates(dataRows, state, true);
```

#### 행 상태별 행 번호 가져오기   
상태를 가진 행들의 행번호 배열을 가져옵니다.

<input type="radio" name="rbRowStateArray" value="all" checked="checked"> all
<input type="radio" name="rbRowStateArray" value="created"> created
<input type="radio" name="rbRowStateArray" value="updated"> updated
<input type="radio" name="rbRowStateArray" value="deleted"> deleted
<input type="radio" name="rbRowStateArray" value="createAndDeleted"> createAndDeleted
<input type="radio" name="rbRowStateArray" value="none"> none

<a class="btn primary small round lowercase" id="btnRowStateArray">가져오기</a>

```js
var rows = null;
var state = $(':radio[name="rbRowStateArray"]:checked').val();
if (!state || state == "all") {
  rows = dataProvider.getAllStateRows(); // RowState.NONE은 포함되지 않는다.
} else {
  rows = dataProvider.getStateRows(state);
}
alert(JSON.stringify(rows));
```

#### 변경 행의 갯수 가져오기   
상태를 가진 행들의 갯수 가져옵니다.

<input type="radio" name="rbRowStateCount" value="all" checked="checked"> all
<input type="radio" name="rbRowStateCount" value="created"> created
<input type="radio" name="rbRowStateCount" value="updated"> updated
<input type="radio" name="rbRowStateCount" value="deleted"> deleted
<input type="radio" name="rbRowStateCount" value="createAndDeleted"> createAndDeleted
<input type="radio" name="rbRowStateCount" value="none"> none

<a class="btn primary small round lowercase" id="btnRowStateCount">가져오기</a>

```js
var state = $(':radio[name="rbRowStateCount"]:checked').val();
var count = dataProvider.getRowStateCount(state);
alert(count);
```

<script>

  $('#btnSetRowState').click(function() {
    var curr = gridView.getCurrent();
    var state = $(':radio[name="rbRowState"]:checked').val()
    dataProvider.setRowState(curr.dataRow, state, true);
  });

  $('#btnSetRowStates').click(function() {
    var dataRows = gridView.getCheckedRows();
    var state = $(':radio[name="rbRowState"]:checked').val()
    dataProvider.setRowStates(dataRows, state, true);
  });  

  $('#btnRowStateArray').click(function() {
    var rows = null;
    var state = $(':radio[name="rbRowStateArray"]:checked').val();
    if (!state || state == "all") {
      rows = dataProvider.getAllStateRows(); // RowState.NONE은 포함되지 않는다.
    } else {
      rows = dataProvider.getStateRows(state);
    }
    alert(JSON.stringify(rows));
  });

  $('#btnRowStateCount').click(function() {
    var state = $(':radio[name="rbRowStateCount"]:checked').val();
    var count = dataProvider.getRowStateCount(state);
    alert(count);
  });

</script>
