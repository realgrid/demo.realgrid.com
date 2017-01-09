#### 데이터 복원함수

[rollback](http://help.realgrid.com/api/DataProvider/rollback/)함수는 [savePoint](http://help.realgrid.com/api/DataProvider/savePoint/)로 저장한 데이터복사본을 이용하여 DataProvider를 복원합니다.  
지정된 `savePoint`로 데이터를 복원하면 이후의 DataProvider savePoint들은 삭제됩니다.   
최초복제된 데이터셋은 rollBack을 이용해서 복원은 할수 있지만 삭제를 할수 없기 때문에 DataProvider [clearSavePoints](http://help.realgrid.com/api/DataProvider/clearSavePoints/) 를 이용하여 삭제합니다.   
`savePoint`를 지정하지 않으면 최초복제로 복원됩니다.

```js
//savePoint 생성
dataProvider.savePoint(true);
//롤백
dataProvider.rollback(savePoint);
//savePoint 초기화
dataProvider.clearSavePoints();
```

#### 데이터 복원하기

<input type="checkbox" id="chkStates" checked="checked">&nbsp;&nbsp;&nbsp;현재 row의 RowState를 함께 저장합니다.  
<a class="btn primary small round lowercase" id="btnSavePoint">복원시점 만들기</a>

<select id="listPoints" style="min-width:80px">
<option value="0">savePoint_0</option></select>  

* 특정한 savePoint로 DataProvider를 복원 시킵니다.  
* 지정한 savePoint 이 후 생성된 복제는 모두 제거됩니다.  

<a class="btn primary small round lowercase" id="btnRollBack">데이터 복원하기</a>  

* clearSavePoints()를 호출해서 최초 복제를 포함 모든 복제를 삭제합니다.  

<a class="btn primary small round lowercase" id="btnClearPoints">savePoint 초기화</a>

```js
//복원시점 만들기
$('#btnSavePoint').click(function() {
    gridView.cancel();
    dataProvider.savePoint($("#chkStates").is(":checked"));
    refreshPoints();
});

//데이터 복원하기
$('#btnRollBack').click(function() {
    var point = $("#listPoints").val();
 
    gridView.cancel();
    dataProvider.rollback(point); // point를 생략하면 최초 복제로 복원
    refreshPoints();
});
 
//savePoint 초기화
$('#btnClearPoints').click(function() {
    dataProvider.clearSavePoints();
    refreshPoints();
});

function refreshPoints() {
    var points = dataProvider.getSavePoints();
    var list = $("#listPoints");
 
    list.empty();
    $.map(points, function (c) {
        $("<option />", { value: c, text: "savePoint_" + c }).appendTo(list);
    });
}
```

<script>

$('#btnRollBack').click(function() {
	var point = $("#listPoints").val();
 
    gridView.cancel();
    dataProvider.rollback(point); // point를 생략하면 최초 복제로 복원
    refreshPoints();
});

$('#btnSavePoint').click(function() {
    gridView.cancel();
    dataProvider.savePoint($("#chkStates").is(":checked"));
    refreshPoints();
});
 
$('#btnClearPoints').click(function() {
    dataProvider.clearSavePoints();
    refreshPoints();
});


function refreshPoints() {
    var points = dataProvider.getSavePoints();
    var list = $("#listPoints");
 
    list.empty();
    $.map(points, function (c) {
        $("<option />", { value: c, text: "savePoint_" + c }).appendTo(list);
    });
}
</script>