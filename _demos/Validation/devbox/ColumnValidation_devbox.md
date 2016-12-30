#### 컬럼 유효성 검사

Validation.criteria 수식에 어긋나는 입력이면 Validation.level 에 해당하는 에러 상태가 되고, 그리드 EditOptions.commitLevel 지정에 따라 에러 상태의 행은 편집을 완료(commit)할 수 없게 됩니다.

#### ValidationLevel

Level은 `"error"`, `"warning"`, `"info"` 세 단계로 지정할 수 있습니다. 

* ERROR 
* WARNING
* INFO

에러 상태는 셀의 오른쪽에 `아이콘`으로 표시되고, Validation.`message`에 지정된 메시지를 팝업 시킵니다.

#### ValidationMode

* ALWAYS - 추가, 수정된 행이 Commit될 경우
* INSERT - 추가된 행이 Commit될 경우
* UPDATE - 수정된 행이 Commit될 경우

Valiadtion은 mode 설정에 따라 행 수정 시에만 검사할 지, 새로운 행 추가 시에만 검사할 지 혹은 모든 경우에 검사할 지를 지정할 수도 있습니다.

#### validation 설정

 Validation criteria를 만족하지 않으면 에러가 됩니다.  
 즉, 실패 판정식이 아니고 성공 판정식입니다.  
 Validation 적용시키고 `Quantity컬럼`의 데이터를 수정해서 유효성 검사가 정상적으로 이루어지는지 확인해보세요.


<a class="btn primary small round lowercase" id="btnSetValidation">validation 적용</a>

```js
validations = [{
    criteria: "value > 100",
    message: "Quantity는 100보다 커야 합니다!",
    mode: "always",
    level: "error"
}, {
    criteria: "value < 200",
    message: "Quantity는 200보다 작아야 합니다!",
    mode: "always",
    level: "warning"
}, {
    criteria: "value <> 150",
    message: "Quantity 값은 150과 달라야 합니다!",
    mode: "always",
    level: "info"
}];

var column = gridView.columnByName("Quantity");
column.validations = validations;
gridView.setColumn(column);

validations = [{
    criteria: "value is not empty",
    message: "CustomerID는 반드시 필요합니다.",
    mode: "always",
    level: "error"
}];
column = gridView.columnByName("CustomerID");
column.validations = validations;
gridView.setColumn(column);
```

<script>
$('#btnSetValidation').click(function() {
	validations = [{
	    criteria: "value > 100",
	    message: "Quantity는 100보다 커야 합니다!",
	    mode: "always",
	    level: "error"
	}, {
	    criteria: "value < 200",
	    message: "Quantity는 200보다 작아야 합니다!",
	    mode: "always",
	    level: "warning"
	}, {
	    criteria: "value <> 150",
	    message: "Quantity 값은 150과 달라야 합니다!",
	    mode: "always",
	    level: "info"
	}];

	var column = gridView.columnByName("Quantity");
	column.validations = validations;
	gridView.setColumn(column);

	validations = [{
	    criteria: "value is not empty",
	    message: "CustomerID는 반드시 필요합니다.",
	    mode: "always",
	    level: "error"
	}];
	column = gridView.columnByName("CustomerID");
	column.validations = validations;
	gridView.setColumn(column);
});
</script>