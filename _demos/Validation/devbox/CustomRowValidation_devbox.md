#### onValidateRow 이벤트

[onValdateRow](http://help.realgrid.com/api/GridBase/onValidateRow/) 이벤트의 매개변수로 해당 셀의 field이름, 편집된 값 등이 넘어옵니다.   
값을 검증한 후 이벤트의 반환값으로 에러 레벨과 메시지를 넘겨주면 그리드는 편집 완료(commit)하지 못하고 사용자에게 메시지를 표시합니다.

아래 버튼을 클릭해서 onValidateRow 이벤트를 적용 후 `Quantity`와 `UnitPrice`컬럼의 값을 변경해보세요.

<a class="btn primary small round lowercase" id="btnOnValidateRow">onValidateRow 적용</a>

```js
gridView.onValidateRow = function(grid, itemIndex, dataRow, inserting, values) {
    console.log("onValidateRow:" + itemIndex + "," + dataRow + "," + inserting + "," + values.Quantity + "," + values.UnitPrice);
 
    var error = {};
 
    //validate Quantity
    if (values.Quantity < 100) {
        error.level = RealGridJS.ValidationLevel.ERROR;
        error.message = "Quantity는 100 이상이어야 합니다.";
    } else if (values.Quantity > 200) {
        error.level = RealGridJS.ValidationLevel.WARNING;
        error.message = "Quantity는 200보다 작아야 합니다.";
    } else if (values.Quantity == 150) {
        error.level = RealGridJS.ValidationLevel.INFO;
        error.message = "Quantity 값이 150과 달라야 합니다.";
    }
 
    //validate Unit Price
    if (values.UnitPrice < 30) {
        console.log("values.UnitPrice < 30");
        error.level = RealGridJS.ValidationLevel.ERROR;
        error.message = "UnitPrice 30 이상이어야 합니다.'";
    } else if (values.UnitPrice > 70) {
        error.level = RealGridJS.ValidationLevel.WARNING;
        error.message = "UnitPrice 70보다 작아야 합니다.";
    } else if (values.UnitPrice == 50) {
        error.level = RealGridJS.ValidationLevel.INFO;
        error.message = "UnitPrice 값이 50과 달라야 합니다.";
    }
 
    return error;
}
```

레벨, 메시지, 에러 상태 등에 대해서는 [Row Validation](/demo/Validation/RowValidation/)을 참조하세요.


<script>
$('#btnOnValidateRow').click(function() {
	gridView.onValidateRow = function(grid, itemIndex, dataRow, inserting, values) {
	    console.log("onValidateRow:" + itemIndex + "," + dataRow + "," + inserting + "," + values.Quantity + "," + values.UnitPrice);
	 
	    var error = {};
	 
	    //validate Quantity
	    if (values.Quantity < 100) {
	        error.level = RealGridJS.ValidationLevel.ERROR;
	        error.message = "Quantity는 100 이상이어야 합니다.";
	    } else if (values.Quantity > 200) {
	        error.level = RealGridJS.ValidationLevel.WARNING;
	        error.message = "Quantity는 200보다 작아야 합니다.";
	    } else if (values.Quantity == 150) {
	        error.level = RealGridJS.ValidationLevel.INFO;
	        error.message = "Quantity 값이 150과 달라야 합니다.";
	    }
	 
	    //validate Unit Price
	    if (values.UnitPrice < 30) {
	        console.log("values.UnitPrice < 30");
	        error.level = RealGridJS.ValidationLevel.ERROR;
	        error.message = "UnitPrice 30 이상이어야 합니다.'";
	    } else if (values.UnitPrice > 70) {
	        error.level = RealGridJS.ValidationLevel.WARNING;
	        error.message = "UnitPrice 70보다 작아야 합니다.";
	    } else if (values.UnitPrice == 50) {
	        error.level = RealGridJS.ValidationLevel.INFO;
	        error.message = "UnitPrice 값이 50과 달라야 합니다.";
	    }
	 
	    return error;
	}
});
</script>