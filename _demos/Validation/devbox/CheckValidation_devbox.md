#### 유효성 설정
Quantity 컬럼과 CustomerID 컬럼에 유효성 설정을 합니다.

<a class="btn primary small round lowercase" id="btnSetValidation">컬럼 유효성 설정</a>

```js
var validations = [{
    criteria: "value < 1000",
    message: "Quantity는 1000보다 작아야 합니다!",
    mode: "always",
    level: "error"
}, {
    criteria: "value < 50",
    message: "Quantity는 50보다 작아야 합니다!",
    mode: "always",
    level: "warning"
}, {
    criteria: "value <> 40",
    message: "Quantity 값은 40과 달라야 합니다!",
    mode: "always",
    level: "info"
}];

var column = gridView.columnByName("Quantity");
column.validations = validations;
gridView.setColumn(column);

validations = [{
    criteria: "value <> 'HANAR'",
    message: "CustomerID는 'HANAR'이면 안됩니다.",
    mode: "always",
    level: "error"
}];
column = gridView.columnByName("CustomerID");
column.validations = validations;
gridView.setColumn(column);
```


#### 일괄 유효성 확인

[gridView.checkValidateCells(itemIndices)](http://help.realgrid.com/api/GridBase/checkValidateCells/)을 사용하여 로드된 데이터에 대하여 일괄 유효성 확인을 할 수 있습니다.  
유효성 확인 후 실패 목록을 반환 합니다.   

전달 인자로 아무것도 입력하지 않으면 모든 행에 대하여 유효성 확인을 수행하고 특정 행 들만 유효성 확인시에는 행 번호들을 배열로 전달하면 됩니다   
<a class="btn primary small round lowercase" id="btnCheckValidateCells">checkValidateCells()</a>

```js
var log = gridView.checkValidateCells();
alert(JSON.stringify(log));
```

#### 유효성 확인 실패 목록

gridView.checkValidateCells(itemIndices)](http://help.realgrid.com/api/GridBase/checkValidateCells/) 후에 오류 값들을 수정하고 잘못된 값들이 있는지 다시 확인할 때 [gridView.getInvalidCellList()](http://help.realgrid.com/api/GridBase/getInvalidCellList/)를 사용 합니다.  
  
유효성 확인 실패된 행을 수정하고 버튼을 클릭하여 수정한 행이 제외되었는지 확인하세요.   

<a class="btn primary small round lowercase" id="btnGetInvalidCellList">getInvalidCellList()</a>

```js
var log = gridView.getInvalidCellList();
alert(JSON.stringify(log));
```

<script>
$('#btnSetValidation').click(function() {
var validations = [{
    criteria: "value < 1000",
    message: "Quantity는 1000보다 작아야 합니다!",
    mode: "always",
    level: "error"
}, {
    criteria: "value < 50",
    message: "Quantity는 50보다 작아야 합니다!",
    mode: "always",
    level: "warning"
}, {
    criteria: "value <> 40",
    message: "Quantity 값은 40과 달라야 합니다!",
    mode: "always",
    level: "info"
}];

var column = gridView.columnByName("Quantity");
column.validations = validations;
gridView.setColumn(column);

validations = [{
    criteria: "value <> 'HANAR'",
    message: "CustomerID는 'HANAR'이면 안됩니다.",
    mode: "always",
    level: "error"
}];
column = gridView.columnByName("CustomerID");
column.validations = validations;
gridView.setColumn(column);
});

$('#btnCheckValidateCells').click(function() {
var log = gridView.checkValidateCells();
alert(JSON.stringify(log));
});

$('#btnGetInvalidCellList').click(function() {
var log = gridView.getInvalidCellList();
alert(JSON.stringify(log));
});
</script>