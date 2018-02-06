#### STEP 1. dataProvider, pivot 객체 생성 및 연결

```js
dataProvider = new RealGridJS.LocalDataProvider();
//pivot 객체 생성
pivot = new RealPivot("realpivot");
pivot.setDataProvider(dataProvider);
```


#### STEP 2. dataProvider field생성 및 pivot fieldMapping

```js
var fields = [{
    fieldName:"국산/수입"
},{
    fieldName:"국가"
},{
    fieldName:"브랜드번호"
},{
    fieldName:"브랜드명"
},{
    fieldName:"모델번호"
},{
    fieldName:"모델명"
},{
    fieldName:"색상번호"
},{
    fieldName:"색상"
},{
    fieldName:"판매날짜",
    dataType:"datetime",
    datetimeFormat:"yyyy-MM-dd"
},{
    fieldName:"판매수량",
    dataType:"number"
},{
    fieldName:"차량가격",
    dataType:"number"
},{
    fieldName:"차종"
},{
    fieldName:"연료"
}];

dataProvider.setFields(fields);

pivot.setFieldMapping([{
    name: "국가",
    sourceField: "국가"
},{
    name: "브랜드명",
    sourceField: "브랜드명"
},{
    name: "판매분기",
    sourceField: "판매날짜",
    dateType:"quarter",
    fieldHeader:"분기",
    displayFormat: "${value}사분기",
    summaryFormat: "${value}사분기 합"
},{
    name: "판매년도",
    sourceField: "판매날짜",
    dateType: "year",
    fieldHeader: "년도",
    displayFormat: "${value}년도",
    summaryFormat: "${value}년도 합"
},{
    name: "판매월",
    sourceField: "판매날짜",
    dateType: "month",
    fieldHeader: "월",
    displayFormat: "${value}월",
    summaryFormat: "${value}월 합"
},{
    name: "판매수량",
    sourceField: "판매수량",
    numberFormat:"#,##0"
},{
    name: "차량가격",
    sourceField: "차량가격",
    numberFormat:"#,##0"
},{
    name:"차종",
    sourceField:"차종"
}]);

pivot.setPivotFields({
    columns: ["판매분기","판매월"],
    rows: ["브랜드명","차종"],
    values: [{
        name: "차량가격",
        expression: "sum"
    }, {
        name: "판매수량",
        expression: "sum"
    }]
});
```

#### STEP 3. 데이터 불러오기

```js
$.ajax({
    url: "/resource/data/pivotDataSet.json",
    success: function (data) {
        dataProvider.fillJsonData(data,{count:5000});
    },
    complete: function(data){
    }
});
```

#### STEP 4. pivot 그리기

```js
pivot.drawView();
```