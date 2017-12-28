---
layout: page
title: Lookup 트리
order: 6
devbox: true
devboxfile: LookupTree-devbox.md
published: true
categories:
  - 셀 구성요소
tags: ['LookupTree']
---

컬럼에 연결된 데이터 필드의 실제 값 대신 그 값과 연관된 다른 값을 셀에 표시합니다.  
아래 예제는 "country"컬럼 값에 따라 "Customer ID 2"컬럼이 동적으로 룩업트리를 참조하는 드랍다운 편집기를 사용합니다.  
"country"컬럼의 값과 "Customer ID 2"컬럼 값에 따라 "lookupDisplay": "true"로 설정된 "Customer ID 3" 컬럼의 값을 확인해 보세요.
 
<script>
var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
  dataProvider.setRows(data);

  
}

var onDoneDataSet = function() {
  var source = {
    "id": "customers",
    "levels": 2,
    "keys": [
      ["France", "VINET"],
      ["France", "VICTE"],
      ["Germany", "TOMSP"],
      ["Brazil", "HANAR"]
    ],
    "values": [
      "Vins et alcools Chevalier",
      "Victuailles en stock",
      "Toms Spezialitäten",
      "Hanari Carnes"
    ]
  };

  gridView.addLookupSource(source);

  console.log("laddLookupSource")

  gridView.onEditCommit = function (id, index, oldValue, newValue) {
    if (index.field == "Country") {
      lookupDataChange(newValue);
    }
  };

  gridView.onCurrentChanged = function (grid, newIndex) {
    if (newIndex && newIndex.dataRow > -1) {
      var keyValue = grid.getValue(newIndex.itemIndex, "Country");
      lookupDataChange(keyValue);
    }
  };

  var oldKey = null;
  function lookupDataChange(keyValue) {
    if (oldKey != keyValue) {
      var params = { country: keyValue };

      $.getJSON("/resource/data/AllCustomerByCountry.json", function (data) {
        lookupData = [];
        for(var j = 0; j < data.length; j++){
          if (data[j].Country == params.country){
            lookupData.push(data[j])
          }
        } 
        var lookups = [];
        for (var i in lookupData) {
          if (!gridView.existsLookupData("customers", [lookupData[i].Country, lookupData[i].CustomerID])) {
            var lookup = [lookupData[i].Country, lookupData[i].CustomerID, lookupData[i].CompanyName];
            lookups.push(lookup);
          }
        }

        gridView.fillLookupData("customers", {
          rows: lookups
        });
      });

      oldKey = keyValue;
    }
  }
}
</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="cellMergingField"
  columnSet="lookupTreeColumn"
  dpOptionSet="dataProviderOption1"
  gridOptionSet="gridOption1"
  styleSet="style1"

  dataSet="griddata1.json"
  successDataSet="onGridSuccessDataSet"

  doneDataSet="onDoneDataSet"



  gridWidth="100%"
  gridHeight="300px" %}