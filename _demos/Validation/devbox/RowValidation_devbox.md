#### 유효성 검사

Validation.criteria 수식에 어긋나는 입력이면 Validation.level 에 해당하는 에러 상태가 되고, 그리드 EditOptions.commitLevel 지정에 따라 에러 상태의 행은 편집을 완료(commit)할 수 없게 됩니다.

#### ValidationLevel

Level은 `"error"`, `"warning"`, `"info"` 세 단계로 지정할 수 있습니다. 

* ERROR 
* WARNING
* INFO

컬럼 validation에서 에러 상태는 셀의 오른쪽에 `아이콘`으로 표시되었지만 RowValidation은 Validation.`message`에 지정된 메시지만 팝업 시킵니다.

#### ValidationMode

* ALWAYS - 추가, 수정된 행이 Commit될 경우
* INSERT - 추가된 행이 Commit될 경우
* UPDATE - 수정된 행이 Commit될 경우

Valiadtion은 mode 설정에 따라 행 수정 시에만 검사할 지, 새로운 행 추가 시에만 검사할 지 혹은 모든 경우에 검사할 지를 지정할 수도 있습니다.

#### validation 설정

행(row) 수준의 편집 EditValidation 목록을 설정합니다.

<a class="btn primary small round lowercase" id="btnSetValidation">RowValidation 적용</a>

```js
validations = [{
    criteria: "value['CustomerID'] is not empty",
    message: "CustomerID는 반드시 필요합니다.",
    mode: "always",
    level: "error"
}, {
    criteria: "(values['Quantity'] >= 100) and (values['UnitPrice'] >= 50)",
    message: "Quantity는 100보다 크고 UnitPrice는 50보다 커야합니다!",
    mode: "always",
    level: "error"
}, {
    criteria: "values['Quantity'] <= 200",
    message: "Quantity는 200보다 작아야 합니다",
    mode: "always",
    level: "warning"
}];

gridView.setValidations(validations);
```

<script>
$('#btnSetValidation').click(function() {
	validations = [{
        criteria: "value['CustomerID'] is not empty",
        message: "CustomerID는 반드시 필요합니다.",
        mode: "always",
        level: "error"
    }, {
        criteria: "(values['Quantity'] >= 100) and (values['UnitPrice'] >= 50)",
        message: "Quantity는 100보다 크고 UnitPrice는 50보다 커야합니다!",
        mode: "always",
        level: "error"
    }, {
        criteria: "values['Quantity'] <= 200",
        message: "Quantity는 200보다 작아야 합니다",
        mode: "always",
        level: "warning"
    }];
 
    gridView.setValidations(validations);
});
</script>