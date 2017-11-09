---
layout: page
title: 피벗 & 그리드
order: 2
published: true
categories:
  - 피벗(RealPivot)
tags: ['pivot', 'grid', '피벗']
---

그리드의 데이터를 Pivot으로 표현합니다.



<script type="text/javascript" src="/lib/realgrid/RealGridSkins.js"></script>
<link rel="stylesheet" type="text/css" href="/lib/realpivot/realpivot_eval.0.0.4/css/default.css">
<link rel="stylesheet" type="text/css" href="/lib/realpivot/realpivot_eval.0.0.4/css/demo_css.css">
<script type="text/javascript" src="/lib/jquery/jquery-1.11.2.min.js"></script>
<script type="text/javascript" src="/lib/realgrid/realgridjs-lic.js"></script>
<script type="text/javascript" src="/lib/realgrid/realgridjs_eval.1.1.25/realgridjs_eval.1.1.25.min.js"></script>
<script type="text/javascript" src="/lib/realgrid/realgridjs_eval.1.1.25/realgridjs-api.1.1.25.js"></script>
<script type="text/javascript" src="/lib/realpivot/realpivot_eval.0.0.4/realpivot_eval.0.0.4.min.js"></script>
<font size="6">RealGrid</font>
<div id="realgrid" style="width:100%;height:500px;"></div><br/>
<font size="6">RealPivot</font>
<div id="realpivot" style="width:100%;height:500px;"></div>

<script>
var gridView;
var dataProvider;
var pivot;

$(document).ready( function() {
    RealGridJS.setTrace(false);
    RealGridJS.setRootContext("/lib/realgrid/realgridjs_eval.1.1.25/");
    dataProvider = new RealGridJS.LocalDataProvider();
    gridView = new RealGridJS.GridView("realgrid");
    gridView.setDataSource(dataProvider);

    gridView.setStyles(OfficeBlueSkin);

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