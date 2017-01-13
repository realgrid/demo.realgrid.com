####  onValidateColumn 이벤트

[onValidateColumn](http://help.realgrid.com/api/GridBase/onValidateColumn/)이벤트의 매개변수로 해당 셀의 field이름, 편집된 값 등이 넘어옵니다.  
셀 편집을 완료하고 다른 셀로 이동할때 javascript를 통한 사용자 validation을 실행합니다.  
해당 컬럼에 문제가 있다면 검증 에러와 에러 메시지를 그리드에 리턴값으로 전달합니다.  

아래 버튼을 클릭해서 onValidateColumn 이벤트를 적용 후 `Quantity`컬럼의 값을 변경해보세요.

<a class="btn primary small round lowercase" id="btnOnValidateColumn">onValidateColumn 적용</a>

```js
gridView.onValidateColumn = function(grid, column, inserting, value) {
    var error = {};
    if (column.fieldName === "Quantity") {
        if (value < 100) {
            error.level = RealGridJS.ValidationLevel.ERROR;
            error.message = "Quantity는 100 이상이어야 합니다.";
        } else if (value > 200) {
            error.level = RealGridJS.ValidationLevel.WARNING;
            error.message = "Quantity는 200보다 작아야 합니다.";
        } else if (value == 150) {
            error.level = RealGridJS.ValidationLevel.INFO;
            error.message = "Quantity 값이 150과 달라야 합니다.";
        }
    };
    return error;
}
```

레벨, 메시지, 에러 상태 등에 대해서는 [셀 Validation](/demo/Validation/ColumnValidation/)을 참조하세요.


<script>
$('#btnOnValidateColumn').click(function() {
	gridView.onValidateColumn = function(grid, column, inserting, value) {
	    var error = {};
	    if (column.fieldName === "Quantity") {
	        if (value < 100) {
	            error.level = RealGridJS.ValidationLevel.ERROR;
	            error.message = "Quantity는 100 이상이어야 합니다.";
	        } else if (value > 200) {
	            error.level = RealGridJS.ValidationLevel.WARNING;
	            error.message = "Quantity는 200보다 작아야 합니다.";
	        } else if (value == 150) {
	            error.level = RealGridJS.ValidationLevel.INFO;
	            error.message = "Quantity 값이 150과 달라야 합니다.";
	        }
	    };
	    return error;
	}
});
</script>