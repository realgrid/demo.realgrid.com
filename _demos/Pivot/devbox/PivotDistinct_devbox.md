#### 고유 값 설정

고유 값표시 설정은 setPivotFields함수의 [값의 유형](http://help.realgrid.com/pivotApi/types/ValueType/){:target="_blank"}을 "distinct"로 설정합니다.

```
pivot.setPivotFields({
    columns: ["대분류", "중분류"],
    rows: ["재질대분류", "설명", "구분"],
    values: [{
        name: "기준치",
        expression: "sum"
    }, {
        name: "N/A",
        expression: "distinct"
    }]
});
```

#### 고유 데이터

HTML태그 형태의 데이터와 이미지를 셀에 표시합니다.  
고유 데이터는 모든 동일 항목의 데이터가 같아야 셀에 표시가 됩니다.  

```
// 이미지 표시
{
    "fieldName": "<img src='images/uncheck.png'>"
    ...
}

// 문자열 표시
{
    "fieldName": "<font color='blue'>▼</font>"
    ...
}
```