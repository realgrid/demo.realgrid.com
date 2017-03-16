---
layout: page
title: 정규식 표현
order: 7
devbox: true
devboxfile: RegularExpression-devbox.md
published: true
categories:
  - 셀 구성요소
tags: ['RegularExpression', '정규식', '마스킹']
---

정규식을 이용하여 원 데이터를 가공하여 표시할 수 있습니다.  
정규식을 이용한 변환은 보여지는 값에만 영향을 미치고 데이터 자체에는 영향이 없으며 Copy&Paste작업시에는
원 데이터로 처리됩니다. 따라서 마스킹과 같은 경우는 그리드의 복사를 제한하여야 합니다.

<script>
  var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
    dataProvider.fillJsonData(data, {});
  }

  var onSuccessGridOptionSet = function() {
    gridView.setEditOptions({editable:false})
    
    gridView.setColumnProperty("userid","displayRegExp", /^([a-z0-9]{3})([a-z0-9]+)$/)
    gridView.setColumnProperty("userid","displayReplace", "$1***")
    gridView.setColumnProperty("userid", "styles", {background:"#ffffff99"})
  }
</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="regularExpressionField"
  columnSet="regularExpressionColumn"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption1"
  successGridOptionSet="onSuccessGridOptionSet"
  styleSet="style1"

  dataSet="regularExpressionData.json"
  showProgress=true
  successDataSet="onGridSuccessDataSet"

  gridWidth="100%"
  gridHeight="300px" %}

<!-- <script>
var onDoneDataSet = function() {
    var columns = [{
        "fieldName": "id",
        "width": 40,
        "header": { "text": "No" },
        "styles": { "textAlignment": "center", "font": "Tahoma" }
    }, {
        "fieldName": "userid",
        "width": 80,
        "header": { "text": "사용자 Id" },
        "styles": {
            "textAlignment": "near",
            "font": "Tahoma",
            "background": "#ffffffaa"
        },
        "displayRegExp": /^([a-z0-9]{3})([a-z0-9]+)$/,
        "displayReplace": "$1***"
    }, {
        "fieldName": "company",
        "width": 100,
        "header": { "text": "회사" },
        "styles": { "textAlignment": "near", "font": "Tahoma" }
    }, {
        "fieldName": "first_name",
        "width": 80,
        "header": { "text": "이름" },
        "styles": { "textAlignment": "near", "font": "Tahoma" }
    }, {
        "fieldName": "last_name",
        "width": 80,
        "header": { "text": "성" },
        "styles": { "textAlignment": "near", "font": "Tahoma" }
    }, {
        "fieldName": "phone",
        "width": 120,
        "header": { "text": "전화번호" },
        "styles": {
            "textAlignment": "near",
            "font": "arial",
            "background": "#ffffff99"
        },
        "displayRegExp": /^([0-9]+)\(([0-9]+)\)(\d{3})(\d{4})$/,
        "displayReplace": "$1-****-****-$4"
    }, {
        "fieldName": "email",
        "width": 150,
        "header": { "text": "E-Mail" },
        "styles": {
            "textAlignment": "near",
            "font": "arial",
            "background": "#ffffff99"
        },
        "displayRegExp": /^([a-zA-Z0-9._%+-]+)(@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,4})$/,
        "displayReplace":
            function (match, p1, p2, offset, string) {
                return p1.substring(0, 2) + "****" + p2;
            }
    }, {
        "fieldName": "ip_address",
        "width": 100,
        "header": { "text": "IP Address" },
        "styles": {
            "textAlignment": "near",
            "font": "arial",
            "background": "#ffffff99"
        },
        "displayRegExp": /^([0-9]+\.)([0-9]+\.)([0-9]+)(\.[0-9]+)$/,
        "displayReplace":  "$1$2***$4",
    }, {
        "fieldName": "card_number",
        "width": 110,
        "header": { "text": "신용카드" },
        "styles": {
            "textAlignment": "near",
            "font": "arial",
            "background": "#ffffff99"
        },
        "displayRegExp": /^(\d{4})(\d{4})(\d{4})(\d{4})$/,
        "displayReplace": "$1-$2-****-$4"
    }, {
        "fieldName": "card_type",
        "width": 90,
        "header": { "text": "카드종류" },
        "styles": { "textAlignment": "near" }
    }];
    gridView.setColumns(columns);

    gridView.showProgress();

    $.ajax({
        url: "http://demo.realgrid.com/DemoData/defaultloaddata.json?__time__=" + new Date().getTime(),
        success: function (data) {
            dataProvider.fillJsonData(data, {});

            var count = dataProvider.getRowCount();
        },
        error: function (xhr, status, error) {
            $("#loadResult").css("color", "red").text("Load failed: " + error).show();
        },
        complete: function (data) {
            gridView.closeProgress();
            gridView.setFocus();
        },
        xhr: function () {
            var xhr = new window.XMLHttpRequest();
            //Download progress
            xhr.addEventListener("progress", function (evt) {
                if (evt.lengthComputable) {
                    gridView.setProgress(0, evt.total, evt.loaded);
                }
            }, false);
            return xhr;
        }
    });

    gridView.setEditOptions({editable:false})
}
</script>
{ % include realgrid.html
  gridVar="gridView"
  dpVar="dataProvider"
  fieldSet="regularExpressionField"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption1"
  doneDataSet="onDoneDataSet"
  styleSet="style1"
  dataSet="griddata1"
  gridId="realgrid"
  gridWidth="100%"
  gridHeight="300px" % } -->
