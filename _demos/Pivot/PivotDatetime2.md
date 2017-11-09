---
layout: page
title: 피벗 날짜 타입2
order: 7
published: true
categories:
  - 피벗(RealPivot)
tags: ['pivot', 'datetime', '날짜']
---


<link rel="stylesheet" type="text/css" href="/lib/realpivot/realpivot_eval.0.0.4/css/default.css">
<link rel="stylesheet" type="text/css" href="/lib/realpivot/realpivot_eval.0.0.4/css/demo_css.css">
<script type="text/javascript" src="/lib/jquery/jquery-1.11.2.min.js"></script>
<script type="text/javascript" src="/lib/realgrid/realgridjs-lic.js"></script>
<script type="text/javascript" src="/lib/realgrid/realgridjs_eval.1.1.25/realgridjs_eval.1.1.25.min.js"></script>
<script type="text/javascript" src="/lib/realgrid/realgridjs_eval.1.1.25/realgridjs-api.1.1.25.js"></script>
<script type="text/javascript" src="/lib/realpivot/realpivot_eval.0.0.4/realpivot_eval.0.0.4.min.js"></script>

pivot의 날짜 데이터를 판매월 - 판매요일 기준으로 column을 구성하였습니다.
<font size="6">판매월 - 판매요일</font>
<div id="realpivot" style="width:100%;height:500px;"></div>


<script>
var dataProvider;
var pivot;

$(document).ready( function() {
    dataProvider = new RealGridJS.LocalDataProvider();
    pivot = new RealPivot("realpivot");
    pivot.setDataProvider(dataProvider);

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
        name: "판매일",
        sourceField: "판매날짜",
        dateType: "day",
        fieldHeader: "일",
        displayFormat: "${value}일",
        summaryFormat: "${value}일 합"
    },{
        name: "판매주",
        sourceField: "판매날짜",
        dateType: "weekofmonth",
        fieldHeader: "주",
        displayFormat: "${value}주",
        summaryFormat: "${value}주 합"
    },{
        name: "half",
        sourceField: "판매날짜",
        dateType: "half",
        fieldHeader: "주",
        displayFormat: "${value}주",
        summaryFormat: "${value}주 합"
    },{
        name: "weekofyear",
        sourceField: "판매날짜",
        dateType: "weekofyear",
        fieldHeader: "주",
        displayFormat: "${value}주",
        summaryFormat: "${value}주 합"
    },{
        name: "판매요일",
        sourceField: "판매날짜",
        dateType: "weekday",
        fieldHeader: "요일",
        displayLabels: { 
            0: "일요일",
            1: "월요일",
            2: "화요일",
            3: "수요일",
            4: "목요일",
            5: "금요일",
            6: "토요일"
        },
        summaryFormat: "${value}주 합"
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
    },{
        name:"연료",
        sourceField:"연료"
    }]);

    pivot.setPivotFields({
        columns: ["판매월","판매요일"],
        rows: ["차종","연료"],
        values: [{
            name: "차량가격",
            expression: "sum"
        }, {
            name: "판매수량",
            expression: "sum"
        }]
    });

    $.ajax({
        url: "/resource/data/pivotDataSet.json",
        success: function (data) {
            dataProvider.fillJsonData(data,{count:5000});
        },
        complete: function(data){
            pivot.drawView();
        }
    });
});


</script>