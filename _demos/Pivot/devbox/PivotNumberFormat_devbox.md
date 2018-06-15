#### 피벗 숫자포맷

pivot setup화면의 값필드 설정 시 직접 변경할 수 있습니다.<br/>

버튼 클릭 시 소수점 첫째자리 까지 표시됩니다.<br/>
<a class="btn primary small round lowercase" id="btnSetNumberFormat1">소수점 첫째자리 표시</a>

```js
pivot.setFieldMapping([
	{
	    name: "판매수량",
	    sourceField: "판매수량",
	    numberFormat:"#,##0.0",
	    labelEnable: false
	},{
	    name: "차량가격",
	    sourceField: "차량가격",
	    numberFormat:"#,##0.0",
	    labelEnable: false
	},
	...
]);
```


버튼 클릭 시 소수점 첫째자리 까지 표시됩니다.<br/>
<a class="btn primary small round lowercase" id="btnSetNumberFormat2">소수점 둘째자리 표시</a>

```js
pivot.setFieldMapping([
	{
	    name: "판매수량",
	    sourceField: "판매수량",
	    numberFormat:"#,##0.00",
	    labelEnable: false
	},{
	    name: "차량가격",
	    sourceField: "차량가격",
	    numberFormat:"#,##0.00",
	    labelEnable: false
	},
	...
]);
```

<script>
$('#btnSetNumberFormat1').click(function() {
	pivot.setFieldMapping([{
        name: "국가",
        sourceField: "국가",
        valueEnable: false
    },{
        name: "브랜드명",
        sourceField: "브랜드명",
        valueEnable: false
    },{
        name: "판매분기",
        sourceField: "판매날짜",
        dateType:"quarter",
        fieldHeader:"판매분기",
        displayFormat: "${value}사분기",
        summaryFormat: "요약",
        valueEnable: false
    },{
        name: "판매년도",
        sourceField: "판매날짜",
        dateType: "year",
        fieldHeader: "판매년도",
        displayFormat: "${value}년도",
        summaryFormat: "요약",
        valueEnable: false
    },{
        name: "판매월",
        sourceField: "판매날짜",
        dateType: "month",
        fieldHeader: "판매월",
        displayFormat: "${value}월",
        summaryFormat: "요약",
        valueEnable: false
    },{
        name: "판매일",
        sourceField: "판매날짜",
        dateType: "day",
        fieldHeader: "판매일",
        displayFormat: "${value}일",
        summaryFormat: "요약",
        valueEnable: false
    },{
        name: "판매주",
        sourceField: "판매날짜",
        dateType: "weekofmonth",
        fieldHeader: "판매월주차",
        displayFormat: "${value}주차",
        summaryFormat: "요약",
        valueEnable: false
    },{
        name: "half",
        sourceField: "판매날짜",
        dateType: "half",
        fieldHeader: "판매반기",
        displayFormat: "${value}주",
        summaryFormat: "요약",
        valueEnable: false
    },{
        name: "weekofyear",
        sourceField: "판매날짜",
        dateType: "weekofyear",
        fieldHeader: "판매연주차",
        displayFormat: "${value}주",
        summaryFormat: "요약",
        valueEnable: false
    },{
        name: "판매수량",
        sourceField: "판매수량",
        numberFormat:"#,##0.0",
        labelEnable: false
    },{
        name: "차량가격",
        sourceField: "차량가격",
        numberFormat:"#,##0.0",
        labelEnable: false
    },{
        name:"차종",
        sourceField:"차종",
        valueEnable: false
    },{
        name:"연료",
        sourceField:"연료",
        valueEnable: false
    }]);

    pivot.setPivotFields({
        columns: ["판매년도","판매월"],
        rows: ["국가","브랜드명","차종"],
        values: [{
            name: "차량가격",
            expression: "sum"
        }, {
            name: "판매수량",
            expression: "sum"
        }]
    });
});

$('#btnSetNumberFormat2').click(function() {
	pivot.setFieldMapping([{
        name: "국가",
        sourceField: "국가",
        valueEnable: false
    },{
        name: "브랜드명",
        sourceField: "브랜드명",
        valueEnable: false
    },{
        name: "판매분기",
        sourceField: "판매날짜",
        dateType:"quarter",
        fieldHeader:"판매분기",
        displayFormat: "${value}사분기",
        summaryFormat: "요약",
        valueEnable: false
    },{
        name: "판매년도",
        sourceField: "판매날짜",
        dateType: "year",
        fieldHeader: "판매년도",
        displayFormat: "${value}년도",
        summaryFormat: "요약",
        valueEnable: false
    },{
        name: "판매월",
        sourceField: "판매날짜",
        dateType: "month",
        fieldHeader: "판매월",
        displayFormat: "${value}월",
        summaryFormat: "요약",
        valueEnable: false
    },{
        name: "판매일",
        sourceField: "판매날짜",
        dateType: "day",
        fieldHeader: "판매일",
        displayFormat: "${value}일",
        summaryFormat: "요약",
        valueEnable: false
    },{
        name: "판매주",
        sourceField: "판매날짜",
        dateType: "weekofmonth",
        fieldHeader: "판매월주차",
        displayFormat: "${value}주차",
        summaryFormat: "요약",
        valueEnable: false
    },{
        name: "half",
        sourceField: "판매날짜",
        dateType: "half",
        fieldHeader: "판매반기",
        displayFormat: "${value}주",
        summaryFormat: "요약",
        valueEnable: false
    },{
        name: "weekofyear",
        sourceField: "판매날짜",
        dateType: "weekofyear",
        fieldHeader: "판매연주차",
        displayFormat: "${value}주",
        summaryFormat: "요약",
        valueEnable: false
    },{
        name: "판매수량",
        sourceField: "판매수량",
        numberFormat:"#,##0.00",
        labelEnable: false
    },{
        name: "차량가격",
        sourceField: "차량가격",
        numberFormat:"#,##0.00",
        labelEnable: false
    },{
        name:"차종",
        sourceField:"차종",
        valueEnable: false
    },{
        name:"연료",
        sourceField:"연료",
        valueEnable: false
    }]);

    pivot.setPivotFields({
        columns: ["판매년도","판매월"],
        rows: ["국가","브랜드명","차종"],
        values: [{
            name: "차량가격",
            expression: "sum"
        }, {
            name: "판매수량",
            expression: "sum"
        }]
    });
});
</script>