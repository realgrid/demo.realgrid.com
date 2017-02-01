#### 컬럼에 필터 설정  

"CustmerID" 필드에 대한 컬럼 필터 적용 예제입니다.  
<a class="btn primary small round lowercase" id="btnSetFilters">Set Filters</a>

```js
var column = gridView.columnByName('CustomerID');
if (column) {
    var filters = [{
        name: "VINET",
        criteria: "value = 'VINET'"
    }, {
        name: "VICTE",
        criteria: "value = 'VICTE'"
    }, {
        name: "HANAR",
        criteria: "value = 'HANAR'"
    }, {
        name: "'VICTE' or 'HANAR'",
        criteria: "(value = 'VICTE') or (value = 'HANAR')"
    }, {
        name: "HANAR: value > 'HANAR'",
        criteria: "value > 'HANAR'"
    }, {
        name: "SUPRD",
        criteria: "value = 'SUPRD'"
    }, {
        name: "SUPRD: value <> 'SUPRD'",
        criteria: "value <> 'SUPRD'"
    }, {
        name: "not equal CustomerID2",
        criteria: "value <> values['CustomerID2']" // CustomerID와 CustomerID2가 상이한 경우
    }, {
        name: "W: value like 'L%'",
        criteria: "value like 'L%'"
    }, {
        name: "W: value not like 'L%'",
        criteria: "value not like 'L%'"
    }, {
        name: "S: value like '%S'",
        criteria: "value like '%S'"
    }, {
        name: "S: value not like '%S'",
        criteria: "value not like '%S'"
    }, { 
        name: "TC: value match 'TC'",
        criteria: "value match 'TC'" // 문자열에 TC가 포함된 경우
    }, {
        name: "match '^RATTC$|^SUPRD$'",
        criteria: "value match '^RATTC$|^SUPRD$'" //RATTC, SUPRD 중 하나인 경우
    }, { 
        name: "TC: value not match 'TC'",
        criteria: "value not match 'TC'" // 문자열에 TC가 포함되지 않는 경우
    }];

    // 컬럼 필터를 재설정한다.
    gridView.setColumnFilters('CustomerID', filters);

    // 아래와 같이 호출해도 된다.
    //column.filters = filters;
    //gridView.setColumn(column);
};
```

"OrderDate" 필드에 대한 컬럼 필터 적용 예제입니다.  
<a class="btn primary small round lowercase" id="btnSetFilters_datetime">Set Filters(datetime)</a>

```js
var column = gridView.columnByName('OrderDate');
if (column) {
    var filters = [{
        name: "1996년",
        criteria: "year(value) = 1996"
    }, {
        name: "1997년",
        criteria: "year(value) = 1997"
    }, {
        name: "10월",
        criteria: "month(value) = 10"
    }, { 
        name: "8일",
        criteria: "day(value) = 8 "
    }, {
        name: "1시",
        criteria: "hour(value) = 1 "
    }, {
        name: "1996년10월",
        criteria: "datestr(value) like '199610%'"
    }];

    column.filters = filters;
    gridView.setColumn(column);
};
```

#### 필터 지우기

Column에 등록된 ColumnFilter들을 모두 제거한다.  
<a class="btn primary small round lowercase" id="btnClearColumnFilters">ClearColumnFilters</a>

```js
gridView.clearColumnFilters("CustomerID");
```

#### 필터 추가하기

Column에 등록된 ColumnFilter에 추가로 필터를 등록한다.

<a class="btn primary small round lowercase" id="btnAddColumnFilters">AddColumnFilters</a>

```js
var filters = [{
    name: "VINET",
    criteria: "value = 'VINET'",
    active: false
}, {
    name: "VICTE",
    criteria: "value = 'VICTE'",
    active: true
}, {
    name: "HANAR",
    criteria: "value = 'HANAR'"
}];
var overwrite = true; // false면 기존에 같은 이름의 필터가 있을 때 예외 발생.

gridView.addColumnFilters('CustomerID', filters, overwrite);
```

#### 필터 제거하기

Column에 등록된 ColumnFilter의 필터를 일부 제거한다.  
<a class="btn primary small round lowercase" id="btnRemoveColumnFilters">RemoveColumnFilters</a>

```js
gridView.removeColumnFilters('CustomerID', ["VINET", "VICTE"]);
```

#### 필터링 하기

필터 적용하기    
<a class="btn primary small round lowercase" id="btnActivateColumnFilters">ActivateColumnFilters</a>

```js
gridView.activateColumnFilters('CustomerID', ["VINET", "VICTE"], true);
```

필터 해제하기    
<a class="btn primary small round lowercase" id="btnDeactivateColumnFilters">DeactivateColumnFilters</a>

```js
gridView.activateColumnFilters('CustomerID', ["VINET", "VICTE"], false);
```

모든 필터 적용하기    
<a class="btn primary small round lowercase" id="btnActivateAllColumnFilters">ActivateAllColumnFilters</a>

```js
gridView.activateAllColumnFilters('CustomerID', true);
```

모든 필터 해제하기    
<a class="btn primary small round lowercase" id="btnDeactivateAllColumnFilters">DeactivateAllColumnFilters</a>

```js
gridView.activateAllColumnFilters('CustomerID', false);
```

#### 필터 액션

필터액션을 사용하여 auto filter를 작성하는 방법    
<a class="btn primary small round lowercase" id="btnSetFilterAction">setFilterAction</a>

```js

var actions = [{
  name: "autoFilter",
  text: "Auto Filter",
  description: "100개의 순차 데이터중 선택하여 filter하는 action."
}];

gridView.setColumnFilterActions('CustomerID', actions);
gridView.setColumnFilterActions('OrderID', actions);

$("#btnFilter").attr("disabled", "disabled");
$("#txtFilter").text("'CustomerId' 컬럼에 필터가 설정됐습니다.");  

//////////////////////////////////////////////////////////////////////////////    
gridView.onFilterActionClicked = function (grid, column, action, x, y) {
  console.log("onFilterActionClicked");
  if (action == "autoFilter") {
    var offset = $("#realgrid").offset();

    showAutoFiltering(column, x + offset.left, y + offset.top);
  }
};

var autoFiltercolumn;
var autoFilterItems = [];

function showAutoFiltering(column, x, y) {
  autoFiltercolumn = column;
  var fieldName = gridView.columnByName(column).fieldName;
  var values = dataProvider.getDistinctValues(fieldName, 100);

  var span = $("#spanFilters");
  span.empty();
  values.forEach(function (v) {
    var label = $("<label />").appendTo(span);
    var existsFilter = autoFilterItems.indexOf(v) >= 0;
    $("<input />", { type: "checkbox", name: "chkAutoFilterItem", value: v, checked: existsFilter}).appendTo(label);
    label.append(v);
    span.append("<br/>");
  });

  $("#divAutoFilter").css("left", x);
  $("#divAutoFilter").css("top", y);

  $("#divAutoFilter").show();
}

function applyAutoFilter() {
  var filterExpr = "";
  var filterItems = $('input[name="chkAutoFilterItem"]:checked');
  autoFilterItems = [];
  for (var i = 0; i < filterItems.length; i++) {
    autoFilterItems.push(filterItems[i].value);
    if (filterExpr != "")
      filterExpr += " or ";
    filterExpr += "(value = '" + filterItems[i].value + "')";
  };
  console.log(filterExpr);
  var filters = {
    name: "auto_result",
    criteria: filterExpr,
    active: true,
    hidden:true
  };

  gridView.addColumnFilters(autoFiltercolumn, filters, true);
  $("#divAutoFilter").hide();
};

function closeAutoFilter() {
  $("#divAutoFilter").hide();
}
/////////////////////////////////////////////////////////////////////////////
<div id="divAutoFilter" style="display:none; position:absolute; height:260px; background-color:#eeeeee; border:1px solid black;">
    <span id="spanFilters" style="overflow-y:scroll; display:block; width:100%; height:230px">
    </span>
    <input type="button" id="applyAutoFilter" value="Apply" onclick="applyAutoFilter();" class="button gray medium3" />
    <input type="button" id="cancelAutoFilter" value="Cancel" onclick="closeAutoFilter();" class="button gray medium3" />
</div>
  
```

<script>
var autoFiltercolumn;
var autoFilterItems = [];

function showAutoFiltering(column, x, y) {
  autoFiltercolumn = column;
  var fieldName = gridView.columnByName(column).fieldName;
  var values = dataProvider.getDistinctValues(fieldName, 100);

  var span = $("#spanFilters");
  span.empty();
  values.forEach(function (v) {
    var label = $("<label />").appendTo(span);
    var existsFilter = autoFilterItems.indexOf(v) >= 0;
    $("<input />", { type: "checkbox", name: "chkAutoFilterItem", value: v, checked: existsFilter}).appendTo(label);
    label.append(v);
    span.append("<br/>");
  });

  $("#divAutoFilter").css("left", x);
  $("#divAutoFilter").css("top", y);

  $("#divAutoFilter").show();
}

function applyAutoFilter() {
  var filterExpr = "";
  var filterItems = $('input[name="chkAutoFilterItem"]:checked');
  autoFilterItems = [];
  for (var i = 0; i < filterItems.length; i++) {
    autoFilterItems.push(filterItems[i].value);
    if (filterExpr != "")
      filterExpr += " or ";
    filterExpr += "(value = '" + filterItems[i].value + "')";
  };
  console.log(filterExpr);
  var filters = {
    name: "auto_result",
    criteria: filterExpr,
    active: true,
    hidden:true
  };

  gridView.addColumnFilters(autoFiltercolumn, filters, true);
  $("#divAutoFilter").hide();
};

function closeAutoFilter() {
  $("#divAutoFilter").hide();
}


$("#btnSetFilters").click(function() { 
var column = gridView.columnByName('CustomerID');
if (column) {
    var filters = [{
        name: "VINET",
        criteria: "value = 'VINET'"
    }, {
        name: "VICTE",
        criteria: "value = 'VICTE'"
    }, {
        name: "HANAR",
        criteria: "value = 'HANAR'"
    }, {
        name: "'VICTE' or 'HANAR'",
        criteria: "(value = 'VICTE') or (value = 'HANAR')"
    }, {
        name: "HANAR: value > 'HANAR'",
        criteria: "value > 'HANAR'"
    }, {
        name: "SUPRD",
        criteria: "value = 'SUPRD'"
    }, {
        name: "SUPRD: value <> 'SUPRD'",
        criteria: "value <> 'SUPRD'"
    }, {
        name: "not equal CustomerID2",
        criteria: "value <> values['CustomerID2']" // CustomerID와 CustomerID2가 상이한 경우
    }, {
        name: "W: value like 'L%'",
        criteria: "value like 'L%'"
    }, {
        name: "W: value not like 'L%'",
        criteria: "value not like 'L%'"
    }, {
        name: "S: value like '%S'",
        criteria: "value like '%S'"
    }, {
        name: "S: value not like '%S'",
        criteria: "value not like '%S'"
    }, { 
        name: "TC: value match 'TC'",
        criteria: "value match 'TC'" // 문자열에 TC가 포함된 경우
    }, {
        name: "match '^RATTC$|^SUPRD$'",
        criteria: "value match '^RATTC$|^SUPRD$'" //RATTC, SUPRD 중 하나인 경우
    }, { 
        name: "TC: value not match 'TC'",
        criteria: "value not match 'TC'" // 문자열에 TC가 포함되지 않는 경우
    }];

    // 컬럼 필터를 재설정한다.
    gridView.setColumnFilters('CustomerID', filters);

    // 아래와 같이 호출해도 된다.
    //column.filters = filters;
    //gridView.setColumn(column);
};
});

$("#btnSetFilters_datetime").click(function() { 
    var column = gridView.columnByName('OrderDate');
    if (column) {
        var filters = [{
            name: "1996년",
            criteria: "year(value) = 1996"
        }, {
            name: "1997년",
            criteria: "year(value) = 1997"
        }, {
            name: "10월",
            criteria: "month(value) = 10"
        }, { 
            name: "8일",
            criteria: "day(value) = 8 "
        }, {
            name: "1시",
            criteria: "hour(value) = 1 "
        }, {
            name: "1996년10월",
            criteria: "datestr(value) like '199610%'"
        }];
 
        column.filters = filters;
        gridView.setColumn(column);
    };
});

$("#btnClearColumnFilters").click(function() { 
  gridView.clearColumnFilters("CustomerID");
});

$("#btnAddColumnFilters").click(function() { 
  var filters = [{
      name: "VINET",
      criteria: "value = 'VINET'",
      active: false
  }, {
      name: "VICTE",
      criteria: "value = 'VICTE'",
      active: true
  }, {
      name: "HANAR",
      criteria: "value = 'HANAR'"
  }];
  var overwrite = true; // false면 기존에 같은 이름의 필터가 있을 때 예외 발생.

  gridView.addColumnFilters('CustomerID', filters, overwrite);
});

$("#btnRemoveColumnFilters").click(function() { 
  gridView.removeColumnFilters('CustomerID', ["VINET", "VICTE"]);
});

$("#btnActivateColumnFilters").click(function() { 
  gridView.activateColumnFilters('CustomerID', ["VINET", "VICTE"], true);
});

$("#btnDeactivateColumnFilters").click(function() { 
  gridView.activateColumnFilters('CustomerID', ["VINET", "VICTE"], false);
});

$("#btnActivateAllColumnFilters").click(function() { 
  gridView.activateAllColumnFilters('CustomerID', true);
});

$("#btnDeactivateAllColumnFilters").click(function() { 
  gridView.activateAllColumnFilters('CustomerID', false);
});

$("#btnSetFilterAction").click(function() { 
    var actions = [{
        name: "autoFilter",
        text: "Auto Filter",
        description: "100개의 순차 데이터중 선택하여 filter하는 action."
    }];
 
    gridView.setColumnFilterActions('CustomerID', actions);
    gridView.setColumnFilterActions('OrderID', actions);
 
    $("#btnFilter").attr("disabled", "disabled");
    $("#txtFilter").text("'CustomerId' 컬럼에 필터가 설정됐습니다.");  
});


</script>

