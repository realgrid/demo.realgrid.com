---
layout: page
title: 피벗 설치하기
order: 1
devbox: true
devboxfile: PivotTutorial_devbox.md
published: true
categories:
  - 피벗(RealPivot)
tags: ['pivot']
---

<link rel="stylesheet" type="text/css" href="/lib/realpivot/realpivot_eval.0.0.4/css/default.css">
<link rel="stylesheet" type="text/css" href="/lib/realpivot/realpivot_eval.0.0.4/css/demo_css.css">
<script type="text/javascript" src="/lib/jquery/jquery-1.11.2.min.js"></script>
<script type="text/javascript" src="/lib/realgrid/realgridjs-lic.js"></script>
<script type="text/javascript" src="/lib/realgrid/realgridjs_eval.1.1.25/realgridjs_eval.1.1.25.min.js"></script>
<script type="text/javascript" src="/lib/realgrid/realgridjs_eval.1.1.25/realgridjs-api.1.1.25.js"></script>
<script type="text/javascript" src="/lib/realpivot/realpivot_eval.0.0.4/realpivot_eval.0.0.4.min.js"></script>

<a class="btn primary small round lowercase" id="btnStep1">1. dataProvider, pivot 객체 생성 및 연결</a>
<a class="btn primary small round lowercase" id="btnStep2">2. dataProvider field생성 및 pivot fieldMapping</a>
<a class="btn primary small round lowercase" id="btnStep3">3. 데이터 불러오기</a>
<a class="btn primary small round lowercase" id="btnStep4">4. pivot 그리기</a>
<div id="realpivot" style="width:100%;height:500px;"></div>

<script>
var dataProvider;
var pivot;
var step = 1;

$('#btnStep2').hide();
$('#btnStep3').hide();
$('#btnStep4').hide();

$('#btnStep1').click(function() {
  if(step == 1){
    dataProvider = new RealGridJS.LocalDataProvider();
    pivot = new RealPivot("realpivot");
    pivot.setOptions({header:{menuButtonVisible:false,setupButtonVisible:false}})
    pivot.setDataProvider(dataProvider);
    pivot.drawView();
    $("#btnStep1").css("background-color","silver");
    $('#btnStep2').show();
    step++
  }else {
    alert("STEP" + step + "을 진행해 주세요.")
  }
});

$('#btnStep2').click(function() {
  if(step == 2){
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

    pivot.drawView();
    $("#btnStep2").css("background-color","silver");
    $('#btnStep3').show();
    step++
  }else {
    alert("STEP" + step + "을 진행해 주세요.")
  }
});

$('#btnStep3').click(function() {    
  if(step == 3){
    $.ajax({
        url: "/resource/data/pivotDataSet.json",
        success: function (data) {
            dataProvider.fillJsonData(data,{count:5000});
        },
        complete: function(data){
          $("#btnStep3").css("background-color","silver");
          $('#btnStep4').show();
          step++
        }
    });
  }else {
    alert("STEP" + step + "을 진행해 주세요.")
  }
});

$('#btnStep4').click(function() {
    pivot.drawView();
});


</script>