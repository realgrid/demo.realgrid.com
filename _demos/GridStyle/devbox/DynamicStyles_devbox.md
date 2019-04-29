#### 동적 편집 여부 설정

'동적편집여부' 컬럼 값에 따라 동적으로 '동적편집' 컬럼의 값을 수정가능, 수정불가 상태로 지정할 수 있습니다.

```
gridView.setColumnProperty("column2","dynamicStyles",function(grid, index, value) {
   var ret = {};
   var col1Value = grid.getValue(index.itemIndex, "field1");
   if (index.column === "column2") {
    switch (col1Value) {
      case '편집가능' :
        ret.editable = true;
        //ret.readOnly = false;
        break;
      case '편집불가' :
        ret.editable = false;
        //ret.readOnly = true;
        ret.background = "#ffff0000";
   }
   return ret;
  }
});
```

#### 동적 커서 설정

'동적커서설정' 컬럼의 값에 따라 '동적커서' 컬럼의 커서 속성을 변경할 수 있습니다.

```
gridView.setColumnProperty("column4","dynamicStyles",function(grid, index, value) {
   var ret = {};
   var cursor = grid.getValue(index.itemIndex, "field3");
   ret["cursor"] = cursor
   return ret;
});
```


#### 동적 편집기 설정

'편집유형설정' 컬럼 값에 따라 편집유형을 동적으로 설정할 수 있습니다.

```
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
```

#### 동적 보이기 설정

'편집유형설정' 컬럼의 값에 따라 동적으로 출력될 값을 설정할 수 있습니다.

```
gridView.setColumnProperty("column6","displayCallback", function(grid, index, value) {
  var check = grid.getValue(index.itemIndex, "field5");
  if (check && value) {
    return check === "법인번호" ? value.substr(0,6)+'-'+value.substr(6,6) :
               check === "사업자번호" ? value.substr(0,3)+'-'+value.substr(3,2)+'-'+value.substr(5,5) : value;
  };
  return value;
});
```

#### displayCallback 제한 사항

병합 모드에서 제한 되는 부분은 아래와 같습니다.  

* column.styles에 numberFormat, datetimeFormat 등이 있는 경우에는 displayCallback은 무시됩니다.  
* 정규식(column.displayRegExp,displayReplace)이 있는 경우 displayCallback은 무시됩니다.  
* excel로 export하는 경우 exportOptions.numberCallback, datetimeCallback, booleanCallback이 있는 경우 displayCallback은 무시됩니다.