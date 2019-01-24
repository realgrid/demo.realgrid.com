---
layout: page
title: 동적 스타일
order: 12
devbox: true
devboxfile: DynamicStyles_devbox.md
published: true
categories:
  - 그리드 스타일
tags: ['style', '스타일', 'dynamicStyles', 'dynamic', '동적']
---

dynamicStyles로 편집여부, 동적커서, 동적편집기, 동적색상 등의 다양한 형태의 스타일을 제공 하고 있습니다.

<script>
  var onGridSuccessDataSet = function(data, textStatus, jqXHR) {
    var data = [
      ["편집가능","편집가능","default","default","법인번호","111111222222"],
      ["편집불가","편집불가","crosshair","crosshair","사업자번호","1112233333"],
      ["편집가능","편집가능","pointer","pointer","법인번호","111111222222"],
      ["편집불가","편집불가","move","move","사업자번호","1112233333"],
      ["편집가능","편집가능","default","default","법인번호","111111222222"],
      ["편집불가","편집불가","crosshair","crosshair","사업자번호","1112233333"],
      ["편집가능","편집가능","pointer","pointer","법인번호","111111222222"],
      ["편집불가","편집불가","move","move","사업자번호","1112233333"],
      ["편집가능","편집가능","default","default","법인번호","111111222222"],
      ["편집불가","편집불가","crosshair","crosshair","사업자번호","1112233333"],
      ["편집가능","편집가능","pointer","pointer","법인번호","111111222222"],
      ["편집불가","편집불가","move","move","사업자번호","1112233333"],
      ["편집가능","편집가능","default","default","법인번호","111111222222"],
      ["편집불가","편집불가","crosshair","crosshair","사업자번호","1112233333"],
      ["편집가능","편집가능","pointer","pointer","법인번호","111111222222"],
      ["편집불가","편집불가","move","move","사업자번호","1112233333"],
      ["편집가능","편집가능","default","default","법인번호","111111222222"],
      ["편집불가","편집불가","crosshair","crosshair","사업자번호","1112233333"],
      ["편집가능","편집가능","pointer","pointer","법인번호","111111222222"],
      ["편집불가","편집불가","move","move","사업자번호","1112233333"],
      ["편집가능","편집가능","default","default","법인번호","111111222222"],
      ["편집불가","편집불가","crosshair","crosshair","사업자번호","1112233333"],
      ["편집가능","편집가능","pointer","pointer","법인번호","111111222222"],
      ["편집불가","편집불가","move","move","사업자번호","1112233333"],
      ["편집가능","편집가능","default","default","법인번호","111111222222"],
      ["편집불가","편집불가","crosshair","crosshair","사업자번호","1112233333"],
      ["편집가능","편집가능","pointer","pointer","법인번호","111111222222"],
      ["편집불가","편집불가","move","move","사업자번호","1112233333"],
      ["편집가능","편집가능","default","default","법인번호","111111222222"],
      ["편집불가","편집불가","crosshair","crosshair","사업자번호","1112233333"],
      ["편집가능","편집가능","pointer","pointer","법인번호","111111222222"],
      ["편집불가","편집불가","move","move","사업자번호","1112233333"]      
    ]
    dataProvider.setRows(data);
  }

  var onDoneDataSet = function() {
    gridView.setColumnProperty("column2","dynamicStyles",function(grid, index, value) {
       var ret = {};
       var col1Value = grid.getValue(index.itemIndex, "field1");
       if (index.column === "column2") {
        switch (col1Value) {
          case '편집가능' :
            ret.editable = true;
            ret.readOnly = false;
            break;
          case '편집불가' :
            ret.editable = false;
            ret.readOnly = false;
            ret.background = "#ffff0000";
       }
       return ret;
      }
    });

    gridView.setColumnProperty("column4","dynamicStyles",function(grid, index, value) {
       var ret = {};
       var cursor = grid.getValue(index.itemIndex, "field3");
       ret["cursor"] = cursor
       return ret;
    });

    gridView.setColumnProperty("column6","dynamicStyles",function(grid, index, value) {
       var kind = grid.getValue(index.itemIndex, "field5");
       var ret = {};
       switch (kind) {
         case '법인번호' :  // 법인번호.
           ret.editor = {
             type:"text", 
             mask:{
               editMask:"000000-000000", allowEmpty:true, includedFormat:false   
             }
           };
           break;
         case '사업자번호' :  // 사업자번호
           ret.editor = {
             type:"text",
             mask:{
               editMask:"000-00-00000", allowEmpty:true, includedFormat:false
             }
           }
       }
       return ret;
    });

    gridView.setColumnProperty("column6","displayCallback", function(grid, index, value) {
      var check = grid.getValue(index.itemIndex, "field5");
      if (check && value) {
        return check === "법인번호" ? value.substr(0,6)+'-'+value.substr(6,6) :
                   check === "사업자번호" ? value.substr(0,3)+'-'+value.substr(3,2)+'-'+value.substr(5,5) : value;
      };
      return value;
    });
  }
</script>

{% include realgrid.html

  gridVar="gridView"
  dpVar="dataProvider"
  gridId="realgrid"

  fieldSet="dynamicStylesFields"
  columnSet="dynamicStylesColumns"
  dpOptionSet="dataProviderOption1"  
  styleSet="style1"

  dataSet="FireDamage.json"
  successDataSet="onGridSuccessDataSet"
  doneDataSet="onDoneDataSet"

  gridWidth="100%"
  gridHeight="300px" %}