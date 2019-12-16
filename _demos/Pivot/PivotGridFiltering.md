---
layout: page
title: 피벗 데이터 디테일
ico: true
order: 18
published: true
devbox: true
devboxfile: PivotGridFiltering_devbox.md
categories:
  - 피벗(RealPivot)
tags: ['pivot', 'grid', '피벗', '필터', 'filter']
---

피벗 데이터의 특정 셀을 그리드에 디테일한 데이터가 출력되 도록 구현한 예제입니다.  
*본 데모는 그리드와 피벗이 조회용으로 구현되어 있으므로 편집 및 속성 변경은 불가능합니다.*

<script type="text/javascript" src="/lib/realgrid/RealGridSkins.js"></script>


<div id="realgrid" style="width:100%;height:250px;"></div><br/>

<script>
var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
    RealGridJS.setTrace(false);
    RealGridJS.setRootContext("/lib/realgrid/realgridjs_eval.1.1.27/");
    gridView = new RealGridJS.GridView("realgrid");
    gridView.setDataSource(dataProvider);

    gridView.setStyles(OfficeBlueSkin);
    gridView.setFilteringOptions({handleVisibility:"hidden"});
    gridView.setEditOptions({editable: false});

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
            text: "국가",
            styles: {
                background: "linear,#22ffd500,#ffffd500,90"
            }
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
            text: "브랜드명",
            styles: {
                background: "linear,#22ffd500,#ffffd500,90"
            }
        }
    },{
        name: "차종",
        fieldName: "차종",
        width: 100,
        header: {
            text: "차종",
            styles: {
                background: "linear,#22ffd500,#ffffd500,90"
            }
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

    pivot.onDblClick = function (pivot, type, index) {
        var colNames = gridView.getColumnNames()

        for(var j = 0; j < colNames.length; j++){
            gridView.clearColumnFilters(colNames[j])
        }



        //rowLabel 값 필터링
        for(var i = 0; i < Object.keys(index.rows).length; i++){
            if(Object.keys(index.rows)[i] !== "__sum"){
                var filters = [{
                    name: Object.keys(index.rows)[i],
                    criteria: "value = '" + index.rows[Object.keys(index.rows)[i]] + "'",
                    active:true
                }];

                gridView.setColumnFilters(Object.keys(index.rows)[i], filters);
            }else{
            }
        }
    }
}

var onDoneDataSet = function() {
    $(".realpivot-title-setup").css("display","none");
}

var onSuccessColumnSet = function(data, textStatus, jqXHR) {
}  

</script>

{% include realpivot.html

  pivotVar="pivot"
  dpVar="dataProvider"
  pivotId="realpivot"

  fieldSet="pivot_setFields"
  fieldMappingSet="pivot_fieldMapping"
  pivotFieldsSet="pivot_pivotFields"

  dataSet="pivotDataSet.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  pivotWidth="100%"
  pivotHeight="500px" 
%}