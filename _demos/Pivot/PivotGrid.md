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

<script type="text/javascript" src="/lib/realgrid/RealGridSkins.js"></script>


<div id="realgrid" style="width:100%;height:250px;"></div><br/>

<script>
var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
    RealGridJS.setTrace(false);
    RealGridJS.setRootContext("/lib/realgrid/realgridjs_eval.1.1.27/");
    gridView = new RealGridJS.GridView("realgrid");
    gridView.setDataSource(dataProvider);

    gridView.setStyles(OfficeBlueSkin);

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

    dataProvider.setRows(data);
    pivot.drawView();
}
var onDoneDataSet = function() {

}

var onSuccessColumnSet = function(data, textStatus, jqXHR) {
}  

</script>

{% include realpivot.html

  pivotVar="pivot"
  dpVar="dataProvider"
  pivotId="realpivot"

  fieldSet="pivotContextMenu_setFields"
  fieldMappingSet="pivotContextMenu_fieldMapping"
  pivotFieldsSet="pivotContextMenu_pivotFields"

  dataSet="pivotDataSet.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  pivotWidth="100%"
  pivotHeight="500px" 
%}