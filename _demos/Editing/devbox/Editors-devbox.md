#### [라인 편집기](http://help.realgrid.com/api/types/LineCellEditor/){:target="_blank"}
[라인 편집기](http://help.realgrid.com/api/types/LineCellEditor/){:target="_blank"}는 한 줄 텍스트를 입력할 수 있는 기본 에디터입니다.

<input type="radio" name="rbTextCase" value="created" checked="checked"> normal
<input type="radio" name="rbTextCase" value="updated"> upper
<input type="radio" name="rbTextCase" value="deleted"> lower

<a class="btn primary small round lowercase" id="btnTextCase">TextCase
</a>

```js
var textCase = $(':radio[name="rbTextCase"]:checked').val()
gridView.setColumnProperty("OrderID", "editor", {"textCase": textCase});
```

#### [멀티라인 편집기](http://help.realgrid.com/api/types/MultiLineCellEditor/){:target="_blank"}
[멀티라인 편집기](http://help.realgrid.com/api/types/MultiLineCellEditor/){:target="_blank"}는 라인 구분자로 나누어지는 여러 줄의 텍스트를 입력할 수 있습니다. 입력되는 텍스트에 맞춰 편집기의 크기가 조정됩니다. Ctrl+Enter로 줄 나누기를 할 수 있습니다.

styles의 textWrap 속성을 반드시 지정해주어야 하며 `explicit` 인 경우 문자열 내에 명시적으로 행바꿈(\n) 코드가 있을 경우 행바꿈이 이루어지고  `normal`인 경우 문자열이 컬럼의 폭보다 긴 경우 자동으로 줄 행바꿈이 이루어 집니다.  

```js
...
//컬럼설정
{
  "name": "CompanyName",
  "fieldName": "CompanyName",
  "width": "200",
  "editor": {
    "type": "multiline",
    "textCase": "upper"
  },
  "styles": {
    "textAlignment": "near",
    "textWrap": "normal"    //"normal" or "explicit"
  },
  "header": {
      "text": "Multiline Edit",
      "styles": {
          "background": "linear,#22ffd500,#ffffd500,90"
      }
  }
}
...
```

#### [숫자 편집기](http://help.realgrid.com/api/types/NumberCellEditor/){:target="_blank"}
[숫자 편집기](http://help.realgrid.com/api/types/NumberCellEditor/){:target="_blank"}는 숫자를 입력할 수 있는 편집기 입니다.   

천단위 구분기호를 표시하고 싶은 경우 styles.numberFormat을 "#,##0" 로 설정하면 되고, 고정 소수점 사용시에는 필요한 자릿수만큼 소수점 이후에 "0"을 표시, 가변 소수점 사용시에는 "#"을 사용합니다.  
예를 들어 천단위 구분기호를 사용하고 고정 소수점 3자리를 사용할 경우 "#,##0.000" 를 사용하면 됩니다. 

editor.editFormat을 "#,##0.##"로 지정한 경우 소수점이하 자리는 최대 2자릿수만큼만 입력됩니다.

```js
...
//컬럼설정
{
  "name": "Quantity",
  "fieldName": "Quantity",
  "width": "100",
  "sortable": false,
  "editor": {
    "type": "number",
    "textAlignment": "far",
    "editFormat": "#,##0.##",
    "multipleChar": "+",
  },
  "styles": {
    "textAlignment": "far",
    "numberFormat": "#,##0.##"
  },
  "header": {
    "text": "Number Edit",
    "styles": {
        "background": "linear,#22ffd500,#ffffd500,90"
    }
  }
}
...
```

#### [드롭다운 편집기](http://help.realgrid.com/api/types/DropDownCellEditor/){:target="_blank"}   
[드롭다운 편집기](http://help.realgrid.com/api/types/DropDownCellEditor/){:target="_blank"}  는 `values`속성으로 지정된 목록 중 한 값을 선택합니다. 또한, `labels`에 `values` 대신 드롭다운 리스트에 표시될 텍스트들을 지정할 수 있습니다.   
`labels`의 항목 수가 values 항목 수 이상이어야 하고, 에디터에 `values`를 지정하지 않으면 컬럼에 지정된 `values`, `labels` 목록이나 `lookupSource`의 목록을 대신 사용합니다.  

```js
...
//컬럼설정
{
  "name": "CustomerID",
  "fieldName": "CustomerID",
  "width": "150",
  "sortable": false,
  "lookupDisplay": true,  //라벨로 표시
  "values": ["VINET", "HANAR", "SUPRD", "VICTE", "THREE", "SEVEN"],
  "labels": ["<VINET>", "<HANAR>", "<SUPRD>", "<VICTE>", "<THREE>", "<SEVEN>"],
  "editor": {
      "type": "dropDown",
      "dropDownCount": 4
  },
  "styles": {
      "textAlignment": "center"
  },
  "header": {
      "text": "DropDown Edit",
      "styles": {
          "background": "linear,#22ffd500,#ffffd500,90"
      }
  }
}
...
```

`domainOnly`가 true이면 목록에 있는 값들만 선택할 수 있습니다.  
`textReadOnly`가 true이면 키 입력이 안되며 선택만 할 수 있습니다.

```js
...
//컬럼설정
{
  "name": "CustomerID2",
  "fieldName": "CustomerID",
  "width": "150",
  "sortable": false,
  "editor": {
    "type": "dropDown",
    "dropDownCount": 4,
    "domainOnly": true,
    "textReadOnly": true,
    "values": ["VINET", "HANAR", "SUPRD", "VICTE", "THREE", "SEVEN"],
    "labels": ["<VINET>", "<HANAR>", "<SUPRD>", "<VICTE>", "<THREE>", "<SEVEN>"]
  },
  "styles": {
    "textAlignment": "center"
  },
  "header": {
    "text": "Domain Only",
    "styles": {
        "background": "linear,#22ffd500,#ffffd500,90"
    }
  }
}
...
```

#### [검색 편집기](http://help.realgrid.com/api/types/SearchCellEditor/){:target="_blank"}   
[검색 편집기](http://help.realgrid.com/api/types/SearchCellEditor/){:target="_blank"}는 설정된 값 중에 일치되는 값이 드롭다운 목록에 표시되는 에디터 이다. 
검색이 시작되면 [gridView.onEditSearch()](http://help.realgrid.com/api/GridBase/onEditSearch/){:target="_blank"} 이벤트가 발생하며, 이 이벤트 내에서 검색 처리 후 [gridView.fillEditSearchItems()](http://help.realgrid.com/api/GridBase/fillEditSearchItems/){:target="_blank"}을 실행해 드롭다운 목록을 채워준다.  

```js
...
var CustomerNames = ["ALFKI", "ANATR", "ANTON", "AROUT", "BERGS", "BLAUS", "BLONP", "BOLID", "BONAP", "BOTTM", "BSBEV", "CACTU", "CENTC", "CHOPS", "COMMI", "CONSH", "DRACD", "DUMON", "EASTC", "ERNSH", "FAMIA", "FISSA", "FOLIG", "FOLKO", "FRANK", "FRANR", "FRANS", "FURIB", "GALED", "GODOS", "GOURL", "GREAL", "GROSR", "HANAR", "HILAA", "HUNGC", "HUNGO", "ISLAT", "KOENE", "LACOR", "LAMAI", "LAUGB", "LAZYK", "LEHMS", "LETSS", "LILAS", "LINOD", "LONEP", "MAGAA", "MAISD", "MEREP", "MORGK", "NORTS", "OCEAN", "OLDWO", "OTTIK", "PARIS", "PERIC", "PICCO", "PRINI", "QUEDE", "QUEEN", "QUICK", "RANCH", "RATTC", "REGGC", "RICAR", "RICSU", "ROMEY", "SANTG", "SAVEA", "SEVES", "SIMOB", "SPECD", "SPLIR", "SUPRD", "THEBI", "THECR", "TOMSP", "TORTU", "TRADH", "TRAIH", "VAFFE", "VICTE", "VINET", "WANDK", "WARTH", "WELLI", "WHITC", "WILMK", "WOLZA"];

gridView.onEditSearch = function (grid, index, text) {
    console.log("onEditSearch:" + index.itemIndex + "," + index.column + ", " + text);
    var items = CustomerNames.filter(function (str) {
        return str.indexOf(text) == 0;
    });
    console.log(items);
    grid.fillEditSearchItems(index.column, text, items);
};
... 
//컬럼설정
{
  "name": "CustomerID3",
  "fieldName": "CustomerID",
  "width": "150",
  "sortable": false,
  "editor": {
    "type": "search",
    "searchLength": 1,  
    "searchDelay": 1000,
    "useCtrlEnterKey": true,
    "useEnterKey": true
  },
  "styles": {
    "textAlignment": "center"
  },
  "header": {
    "text": "Search Editor ",
    "styles": {
        "background": "linear,#22ffd500,#ffffd500,90"
    }
  }
}
...
```

#### [날짜 편집기](http://help.realgrid.com/api/types/DateCellEditor/){:target="_blank"}   
[날짜 편집기](http://help.realgrid.com/api/types/DateCellEditor/){:target="_blank"}를 사용하면 키보드로 날짜를 입력하거나 달력 팝업을 사용하여 날짜를 선택할 수 있습니다.  

```js
...
//컬럼설정
{
  "name": "OrderDate",
  "fieldName": "OrderDate",
  "width": "180",
  "sortable": false,
  "editor": {
    "type": "date",
    "datetimeFormat": "yyyy.MM.dd"
  },
  "styles": {
    "textAlignment": "center",
    "datetimeFormat": "yyyy.MM.dd"
  },
  "header": {
      "text": "Date Edit",
      "styles": {
          "background": "linear,#22ffd500,#ffffd500,90"
      }
  }
}
...
```

<script>
  $('#btnTextCase').click(function() {
    var textCase = $(':radio[name="rbTextCase"]:checked').val()
    gridView.setColumnProperty("OrderID", "editor", {"textCase": textCase});
  });

  $('#btnSetRowState').click(function() {
    var curr = gridView.getCurrent();
    var state = $(':radio[name="rbRowState"]:checked').val()
    dataProvider.setRowState(curr.dataRow, state, true);
  });

  $('#btnSetRowStates').click(function() {
    var dataRows = gridView.getCheckedRows();
    var state = $(':radio[name="rbRowState"]:checked').val()
    dataProvider.setRowStates(dataRows, state, true);
  });  

  $('#btnRowStateArray').click(function() {
    var rows = null;
    var state = $(':radio[name="rbRowStateArray"]:checked').val();
    if (!state || state == "all") {
      rows = dataProvider.getAllStateRows(); // RowState.NONE은 포함되지 않는다.
    } else {
      rows = dataProvider.getStateRows(state);
    }
    alert(JSON.stringify(rows));
  });

  $('#btnRowStateCount').click(function() {
    var state = $(':radio[name="rbRowStateCount"]:checked').val();
    var count = dataProvider.getRowStateCount(state);
    alert(count);
  });

</script>
