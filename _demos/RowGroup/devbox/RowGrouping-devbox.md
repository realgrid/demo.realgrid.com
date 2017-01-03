#### 그룹핑 하기

 컬럼 헤더를 panel 영역으로 드래깅하면 그 컬럼으로 grouping 합니다.  
 또는 [GridView.groupBy()](http://help.realgrid.com/api/GridView/groupBy/) 함수를 호출해서 grouping할 수도 있습니다.

<div class="checkbox">
  <label>
    <input type="checkbox" id="Country" name="chkFieldName" value="Country"> Country
  </label>
  <label>
    <input type="checkbox" id="CompanyName" name="chkFieldName" value="CompanyName"> CompanyName
  </label>
  <label>
    <input type="checkbox" id="OrderID" name="chkFieldName" value="OrderID"> OrderID
  </label>
  <label>
    <input type="checkbox" id="CustomerID" name="chkFieldName" value="CustomerID"> CustomerID
  </label>
</div>
<a class="btn primary small round lowercase" id="btnOnGrouping">그룹핑 하기</a>

```js
var fieldNames = [];
$("input[name='chkFieldName']:checked").each( function() {
    fieldNames.push($(this).val());
});
gridView.groupBy(fieldNames);
```

#### 그룹핑 이벤트

Row grouping되면 Javascript 그리드의 [onGrouping()](http://help.realgrid.com/api/GridView/onGrouping/), onGroupingChanged() 이벤트가 발생됩니다. 

* [onGrouping()](http://help.realgrid.com/api/GridView/onGrouping/)
* onGroupingChanged()

<a class="btn primary small round lowercase" id="btnOnGroupingChanged">이벤트 적용</a>

```js
gridView.onGrouping = function (grid){
  alert("onGrouping 이벤트가 발생했습니다. true를 반환합니다.");
  return true;
}

gridView.onGroupingChanged = function (grid) {
  alert("onGroupingChanged : isGrouped = " + grid.isGrouped() + ", isMergedGrouped  = " + grid.isMergedGrouped());
};
```

#### 그룹 푸터 값 표시


아래 옵션들의 설정에 따라 각 행 그룹들은 `그룹 푸터`를 표시할 수 있습니다.  
그룹 푸터에 표시하는 텍스트는 GridBase.[setRowGroup](http://help.realgrid.com/api/GridBase/setRowGroup/) 함수에 전달되는 설정 개체의 `footerStatement` 값으로 지정합니다.   
또한, [summary mode](http://help.realgrid.com/api/types/SummaryMode/)를 통해 각 행 그룹의 푸터에 표시할 수 있는 값의 종류를 지정할 수도 있습니다.

footerStatement: 
<select id="selFooterStatement">
  <option selected="selected" value="">null</option>
  <option>${groupValue} 계</option>
  <option>${columnFooter}(${rowCount})</option>
  <option>${groupColumn} - ${groupValue}</option>
</select>
<a class="btn primary small round lowercase" id="btnSetFooterStatement">적용</a>

```js
var statement = $('#selFooterStatement').val();
statement = statement ? statement : null;
gridView.setRowGroup({
  footerStatement: statement
});
```

#### 그룹 헤더 값 표시

아래 옵션들의 설정에 따라 각 행 그룹들은 `그룹 헤더`를 표시할 수 있습니다.  
그룹 헤더에 표시하는 텍스트는 GridBase.[setRowGroup](http://help.realgrid.com/api/GridBase/setRowGroup/) 함수에 전달되는 설정 개체의 `headerStatement` 값으로 지정합니다.   
`headerStatement`의 기본값은 `"${groupField}: ${groupValue} - ${rowCount} rows"` 입니다.

headerStatement: 
<select id="selHeaderStatement">
  <option selected="selected">${groupField}: ${groupValue} - ${rowCount} rows</option>
  <option>${fieldHeader}: ${groupValue} - ${rowCount} rows</option>
  <option>${groupColumn} - ${groupValue}</option>
  <option>${columnHeader} - ${groupValue}</option>
</select>
<a class="btn primary small round lowercase" id="btnSetHeaderStatement">적용</a>

```js
var statement = $('#selHeaderStatement').val();
gridView.setRowGroup({
    headerStatement: statement
});
```

#### 그루핑 옵션 설정

[GroupingOptions()](http://help.realgrid.com/api/types/GroupingOptions/)함수로 RowGrouping시 적용될 옵션을 설정합니다.

<input type="checkbox" id="chkLinear"> lindear(panel영역에 표시되는 column을 일렬로 배치)  
<input type="checkbox" id="chkRemoveIncludeLower"> removeIncludeLower(그룹핑 해제시 하위 그룹까지 해제)  
<input type="checkbox" id="expandWhenGrouping"> expandWhenGrouping(그룹핑시 그룹의 펼침 여부)  

<a class="btn primary small round lowercase" id="btnSetGroupingOptions">Grouping 옵션 적용</a>


```js
gridView.setGroupingOptions({
    enabled: true, 
    prompt: "컬럼 헤더를 이 곳으로 끌어다 놓으면 그 컬럼으로 그룹핑합니다.", 
    linear: false, 
    removeIncludeLower: false,
    expandWhenGrouping: true, 
    toast:{
        visible: true
    }
});
```

[setRowGroup()](http://help.realgrid.com/api/types/RowGroupOptions/)함수로 RowGrouping과 관련된 영역들의 표시 방법 등에 대한 설정합니다.  

* [summaryMode](http://help.realgrid.com/api/types/SummaryMode/): 각 행 그룹의 합계를 구하는 방식입니다.
* expandedAdornments: Row group이 펼쳐진 상태일 때, 그룹 header, footer의 표시 여부를 지정합니다.
* collapsedAdornments: Row group이 펼쳐지지 않은 상태일 때, 그룹 header, footer의 표시 여부를 지정합니다.

summaryMode:
<select id="RowGroupSummaryMode">
  <option value="none">NONE</option>
  <option value="aggregate" selected="">AGGREGATE</option>
  <option value="statistical">STATISTICAL</option>
</select>  
expandedAdornments:
<select id="ExpandedAdornments">
  <option value="both" selected="">BOTH</option>
  <option value="header">HEADER</option>
  <option value="summary">SUMMARY</option>
</select>  
collapsedAdornments:
<select id="CollapsedAdornments">
  <option value="both">BOTH</option>
  <option value="header" selected="">HEADER</option>
</select>

<a class="btn primary small round lowercase" id="btnSetRowGroup1">옵션 적용</a>



* sorting: rowGroup시 자동으로 정렬 여부를 지정합니다.
* footerStatement: 행 그룹핑시 그룹핑된 컬럼 풋터의 텍스트를 지정합니다.
* footerCellMerge: 행 그룹핑시 그룹핑된 컬럼 풋터의 머지 여부를 지정합니다.
* levels: RowGroup헤더나 풋터, 바의 레벨별 스타일을 지정합니다.

<a class="btn primary small round lowercase" id="btnSetRowGroup2">옵션 적용</a>


```js
gridView.setRowGroup({
  summaryMode: "aggregate",
  sorting:true,
  footerStatement: "행 그룹핑된 컬럼의 풋터입니다.",
  footerCellMerge: true
});
```

<a class="btn primary small round lowercase" id="btnSetRowLevels">levels 적용</a>

```js
gridView.setRowGroup({
  levels: [{
    headerStyles: {
      background: "#FF008800",
      foreground: "#FFFFFFFF",
      fontBold: true
    },
    footerStyles: {
      background: "#FF008800",
      foreground: "#FFFFFFFF",
      fontBold: true
    },
    headerBarStyles: {
      background: "#FF008800"
    },
    footerBarStyles: {
      background: "#FF008800"
    },
    barStyles: {
      background: "#FF008800"
    }
  },{
    headerStyles: {
      background: "#FF00CC00"
    },
    footerStyles: {
      background: "#FF00CC00"
    },
    headerBarStyles: {
     background: "#FF00CC00"
    },
    footerBarStyles: {
      background: "#FF00CC00"
    },
    barStyles: {
      background: "#FF00CC00"
    }
  },{
    headerStyles: {
      background: "#FF00FF00"
    },
   footerStyles: {
      background: "#FF00FF00"
   },
    headerBarStyles: {
      background: "#FF00FF00"
   },
   footerBarStyles: {
      background: "#FF00FF00"
    },
    barStyles: {
      background: "#FF00FF00"
   }
  },{
    headerStyles: {
      background: "#4400FF00"
    },
    headerBarStyles: {
      background: "#4400FF00"
   },
    barStyles: {
      background: "#4400FF00"
   }
  }] 
});
```


<script>
$('#btnOnGrouping').click(function() {
  var fieldNames = [];
  $("input[name='chkFieldName']:checked").each( function() {
      fieldNames.push($(this).val());
  });
  gridView.groupBy(fieldNames);
});

$('#btnOnGroupingChanged').click(function() {
  gridView.onGrouping = function (grid){
    alert("onGrouping 이벤트가 발생했습니다. true를 반환합니다.");
    return true;
  }

  gridView.onGroupingChanged = function (grid) {
    alert("onGroupingChanged : isGrouped = " + grid.isGrouped() + ", isMergedGrouped  = " + grid.isMergedGrouped());
  };
});

$('#btnSetFooterStatement').click(function() {
var statement = $('#selFooterStatement').val();
  statement = statement ? statement : null;
  gridView.setRowGroup({
    footerStatement: statement
  })
});

$('#btnSetHeaderStatement').click(function() {
  var statement = $('#selHeaderStatement').val();
  gridView.setRowGroup({
      headerStatement: statement
  });
});

$('#btnSetGroupingOptions').click(function() {
  gridView.setGroupingOptions({
      enabled: true, 
      prompt: "컬럼 헤더를 이 곳으로 끌어다 놓으면 그 컬럼으로 그룹핑합니다.", 
      linear: $("#chkLinear").is(":checked"), 
      removeIncludeLower: $("#chkRemoveIncludeLower").is(":checked"),
      expandWhenGrouping: $("#expandWhenGrouping").is(":checked"), 
      toast:{
          visible: true
      }
  });
});

$('#btnSetRowGroup1').click(function() {
  var summary = $('#RowGroupSummaryMode :selected').val();
  var expanded = $('#ExpandedAdornments :selected').val();
  var collapsed = $('#CollapsedAdornments :selected').val();

  gridView.setRowGroup({
    summaryMode: summary,
    expandedAdornments: expanded,
    collapsedAdornments: collapsed
  });
});

$('#btnSetRowGroup2').click(function() {
  gridView.setRowGroup({
    sorting:true,
    footerStatement: "행 그룹핑된 컬럼의 풋터입니다.",
    footerCellMerge: true
  });
});

$('#btnSetRowLevels').click(function() {
  gridView.setRowGroup({
    levels: [{
      headerStyles: {
        background: "#FF008800",
        foreground: "#FFFFFFFF",
        fontBold: true
      },
      footerStyles: {
        background: "#FF008800",
        foreground: "#FFFFFFFF",
        fontBold: true
      },
      headerBarStyles: {
        background: "#FF008800"
      },
      footerBarStyles: {
        background: "#FF008800"
      },
      barStyles: {
        background: "#FF008800"
      }
    },{
      headerStyles: {
        background: "#FF00CC00"
      },
      footerStyles: {
        background: "#FF00CC00"
      },
      headerBarStyles: {
       background: "#FF00CC00"
      },
      footerBarStyles: {
        background: "#FF00CC00"
      },
      barStyles: {
        background: "#FF00CC00"
      }
    },{
      headerStyles: {
        background: "#FF00FF00"
      },
     footerStyles: {
        background: "#FF00FF00"
     },
      headerBarStyles: {
        background: "#FF00FF00"
     },
     footerBarStyles: {
        background: "#FF00FF00"
      },
      barStyles: {
        background: "#FF00FF00"
     }
    },{
      headerStyles: {
        background: "#4400FF00"
      },
      headerBarStyles: {
        background: "#4400FF00"
     },
      barStyles: {
        background: "#4400FF00"
     }
    }]
  });
});
</script>