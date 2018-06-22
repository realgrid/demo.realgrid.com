---
layout: page
title: 피벗 & 그리드
order: 2
published: true
devbox: true
devboxfile: PivotGrid_devbox.md
categories:
  - 피벗(RealPivot)
tags: ['pivot', 'grid', '피벗']
---

동일한 DataProvider로 GridView와 PivotView로 표현한 예제입니다.

<link rel="stylesheet" type="text/css" href="/lib/realpivot/realpivot_eval.0.9.0/css/default_blue.css">
<link rel="stylesheet" type="text/css" href="/lib/css/pivot_demo.css">
<script type="text/javascript" src="/lib/jquery/jquery-1.11.2.min.js"></script>
<script type="text/javascript" src="/lib/realgrid/realgridjs-lic.js"></script>  
<script type="text/javascript" src="/lib/realgrid/realgridjs_eval.1.1.27/realgridjs_eval.1.1.27.min.js"></script>
<script type="text/javascript" src="/lib/realgrid/realgridjs_eval.1.1.27/realgridjs-api.1.1.27.js"></script>
<script type="text/javascript" src="/lib/realpivot/realpivot_eval.1.0.0/messages/realpivot-messages.js"></script>
<script type="text/javascript" src="/lib/realpivot/realpivot_eval.1.0.0/realpivot_eval.1.0.0.min.js"></script>
<script type="text/javascript" src="/lib/realgrid/RealGridSkins.js"></script>

<div id="realgrid" style="width:100%;height:250px;"></div><br/>
<div id="realpivot" style="width:100%;height:500px;"></div>

<script>
var gridView;
var dataProvider;
var pivot;

$(document).ready( function() {
    RealGridJS.setTrace(false);
    RealGridJS.setRootContext("/lib/realgrid/realgridjs_eval.1.1.27/");
    dataProvider = new RealGridJS.LocalDataProvider();
    gridView = new RealGridJS.GridView("realgrid");
    gridView.setDataSource(dataProvider);


    pivot = new RealPivot("realpivot");
    pivot.setDataProvider(dataProvider);

    gridView.setStyles(OfficeBlueSkin)

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

    var columns = [{
        name: "국산/수입",
        fieldName: "국산/수입",
        width: 100,
        header: {
            text: "국산/수입"
        }
    },{
        name: "국가",
        fieldName: "국가",
        width: 70,
        header: {
            text: "국가"
        }
    },{
        name: "브랜드번호",
        fieldName: "브랜드번호",
        width: 70,
        header: {
            text: "브랜드번호"
        },
        styles: {
            numberFormat:"#,##0",
            textAlignment:"far"
        }
    },{
        name: "브랜드명",
        fieldName: "브랜드명",
        width: 100,
        header: {
            text: "브랜드명"
        }
    },{
        name: "모델번호",
        fieldName: "모델번호",
        width: 70,
        header: {
            text: "모델번호"
        },
        styles: {
            numberFormat:"#,##0",
            textAlignment:"far"
        }
    },{
        name: "모델명",
        fieldName: "모델명",
        width: 150,
        header: {
            text: "모델명"
        }
    },{
        name: "색상번호",
        fieldName: "색상번호",
        width: 70,
        header: {
            text: "색상번호"
        },
        styles: {
            numberFormat:"#,##0",
            textAlignment:"far"
        }
    },{
        name: "색상",
        fieldName: "색상",
        width: 100,
        header: {
            text: "색상"
        }
    },{
        name: "판매날짜",
        fieldName: "판매날짜",
        width: 100,
        header: {
            text: "판매날짜"
        }
    },{
        name: "판매수량",
        fieldName: "판매수량",
        width: 70,
        header: {
            text: "판매수량"
        },
        styles: {
            numberFormat:"#,##0",
            textAlignment:"far"
        }
    },{
        name: "차량가격",
        fieldName: "차량가격",
        width: 100,
        header: {
            text: "차량가격"
        },
        styles: {
            numberFormat:"#,##0",
            textAlignment:"far"
        }
    },{
        name: "차종",
        fieldName: "차종",
        width: 100,
        header: {
            text: "차종"
        }
    },{
        name: "연료",
        fieldName: "연료",
        width: 100,
        header: {
            text: "연료"
        }
    }];

    gridView.setColumns(columns);

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
        numberFormat:"#,##0",
        labelEnable: false
    },{
        name: "차량가격",
        sourceField: "차량가격",
        numberFormat:"#,##0",
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