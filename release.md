---
layout: page
title: '최신버전 1.1.41'
published: true
permalink: /release/
---

{% comment %}
  - 함수 링크는 원본 객체명과 함께 작성해 주세요.
    - 예: GridBase.checkValidateCells()
  - 객체명, 함수명, 옵션명, 속성명의 대소문자 사용에 주의 하세요.
    - 예: PasteOptions.forceColumnValidation 속성
{% endcomment %}

## 1.1.41 (2022년 6월)

### 기능개선
1. [numberEditor](http://help.realgrid.com/api/types/NumberCellEditor/)
  - `numberEditor.maxLengthExceptComma`속성이 true이면 입력된 값에서 `,`를 제외하고 입력된 문자의 길이가 `maxLength`와 같으면 다음 셀로 이동하도록 개선.

1. [TreeView](https://demo.realgrid.com/Tree/TreeDataModel/)
  - 대량의 data를 load시 시간이 오래 걸리는 현상을 개선.

1. [numberEditor](http://help.realgrid.com/api/types/NumberCellEditor/)
  - editor가 표시되지 않는 상태에서 한글 입력시 기존 내용이 지워지는 현상을 개선.
  
### 오류수정
1. [numberEditor](http://help.realgrid.com/api/types/NumberCellEditor/)
  - numberEditor에 `editFormat`이 적용되면 -0으로 시작되는 소수점 값을 입력할수 없는 현상 수정.

1. [editOptions](http://help.realgrid.com/api/types/EditOptions/)
  - `numberEditor`에 한글이 입력된 이후에는 `maxLengthToNextCell`속성이 적용되지 않는 현상 수정.

1. [numberEditor](http://help.realgrid.com/api/types/NumberCellEditor/)
  - `maxIntegerLength`속성이 설정된 셀에서 다른셀로 이동을 해도 해당속성이 계속 적용되는 현상 수정  


## 1.1.40 (2022년 3월)  

### 기능개선
1. [CheckBar](http://help.realgrid.com/api/types/CheckBar/)
  - `exclusive`가 true일때 선택되지 않은 item도 이미지로 표시되도록 하는 `unCheckRadioImageUrl` 속성 추가

### 오류수정
1. [TreeView]({{'/RowGroup/TreeView/' | prepend:site.baseurl}}})
  - `onTreeItemCollapsing`, `onTreeItemExpanding` 이벤트에서 `false`를 return해도 접거나 펼치는 동작이 수행되는 현상 수정

1. [RowGrouping]({{'/RowGroup/RowGrouping/' | prepend:site.baseurl}}})
  - grouping 관련 스타일이 설정된 상태에서 excel로 export하면 발생하는 오류 수정
  - getRowGroup()으로 가져온 값을 다시 setRowGroup했을때 발생하는 오류 수정

1. [TreeView]({{'/RowGroup/TreeView/' | prepend:site.baseurl}}})
  - `onTreeItemCollapsed`이벤트가 발생하지 않는 현상 수정.


## 1.1.39 (2021년 10월)

### 기능개선

1. [ItemModelApi]({{ '/RowGroup/ItemModelApi/' | prepend: site.baseurl}})
  - [expandGroup](http://help.realgrid.com/api/GridView/expandGroup/) 또는 [collapseGroup](http://help.realgrid.com/api/GridView/collapseGroup/)으로 그룹을 접거나 펼칠때 itemIndex에 해당하는 model이 group이 아닌 경우 model의 parent가 접거나 펼쳐지도록 개선.

1. [editOptions](http://help.realgrid.com/api/types/EditOptions/)
  - editOptions.updatable이 false여도 rowState가 `created`인 행은 편집가능하도록 개선

1. `numberFormat`의 소수점 버림/올림시 시 소숫점 이하 표시방식 변경.
  - numberFormat이 `#,##0.####;f`일때 일부 값에서 `0.0000`으로 표시되던 것을 `0`으로 표시되도록 변경

### 오류 수정

1. [TreeView]({{ '/Tree/TreeDataModel/' | prepend: site.baseurl}}')
  - 엑셀로 export시 [footer](http://help.realgrid.com/api/types/ColumnFooter/).callback으로 반환된 문자열이 누락되는 현상 수정

1. `syncHeadCheck`
  - checkBar.syncHeadCheck 가 `true`일때 첫번째 item의 checkBox를 체크하면 checkBar의 header가 체크되는 현상 수정.

  
## 1.1.38 (2021년 06월)

---

### 기능 개선

1. [DataColumn](http://help.realgrid.com/api/types/DataColumn/)
  - [fitRowHeight](http://help.realgrid.com/api/GridBase/fitRowHeight/)로 자동행높이 조절시 일부 컬럼을 제외할수 있도록 exceptRowHeight 속성이 추가되었습니다. default는 `false`입니다.

1. [DisplayOptions](http://help.realgrid.com/api/types/DisplayOptions/)
  - 그리드 Container Div의 style.display 속성이 변경될때 그리드의 크기를 자동으로 변경하는 watchDisplayChange 속성이 추가되었습니다. default는 `true`입니다.

1. [LineCellEditor](http://help.realgrid.com/api/types/LineCellEditor/)
  - 특정 문자들만 입력하거나 입력을 제한하도록 하는 inputCharacters속성과 ignoreCharacters속성이 추가 되었습니다.
  - 특정문자들만 입력받을때는 inputCharacters속성에 입력받을 문자를 입력합니다.
  - 특정문자를 제외하는 경우 ignoreCharacters속성에 제한할 문자를 입력합니다.
  - 자세한 내용은 [문자 입력 제한](http://demo.realgrid.com/Editing/LineCellEditor/)를 참조하세요.  

```js
gridView.setColumn([{
  name: "column1",
  fieldName: "field1",
  editor:{
    type:"line",
    inputCharacters: "A-Za-z"  // alphabet만 입력가능
  }
}, {
  name: "column2",
  fieldName: "field2",
  editor:{
    type:"line",
    ignoreCharacters: "A-Za-z"  // alphabet은 입력 불가.
  }
}]);

```

### 오류 수정

1. IE에서 editable이 fase이면서 값이 없는 셀에서 복사가 되지 않는 현상을 수정하였습니다.

1. [ExcelExport]({{ '/Excels/ExcelExport/' | prepend: site.baseurl}})
  - 그리드 상단 합계 영역에 표시되는 값이 엑셀로 출력되지 않는 현상을 수정하였습니다.
  - groupFooter에 dynamicStyle이 적용되었을때 엑셀로 출력시 적용되지 않는 현상을 수정하였습니다.

1. [DropdownCellEditor](http://help.realgrid.com/api/types/DropDownCellEditor/)
  - dropdown 편집기의 domainOnly가 true이면서 입력된 값이 없는 경우 다른셀을 클릭해도 닫히지 않는 현상을 수정하였습니다.

1. [CheckBar](http://help.realgrid.com/api/types/CheckBar/)
  - syncHeadCheck 속성이 true일때 행의 선택 여부와 상관없이 모든 행의 checkable이 false인 경우 checkBar의 head에 선택이 표시되는 현상이 수정되었습니다.

1. [EditOptioins](http://help.realgrid.com/api/types/EditOptions/)
  - enterToTab과 enterToEdit 가 동시에 적용되었을때 행의 마지막 셀에서 `enter`를 입력했을때 editor가 사라지지 않는 현상을 수정하였습니다.


## 1.1.37 (2021년 02월)

---

### 기능 개선

1. `numberFormat`의 소수점 올림/버림 설정이 소수점 첫번째 자리에도 적용되도록 개선되었습니다.
  - `numberFormat`이 `#,##0;;;f`인 경우 소수점을 버린값으로 출력됩니다.

### 오류 수정

1. [ExcelExport]({{ '/Excels/ExcelExport/' | prepend: site.baseurl}})
  - link 타입 컬럼을 export시 font size가 설정된 스타일과 다른 현상을 수정하였습니다.

1. `fitRowHeight`로 자동행 높이 조절시 일부 글자가 표시안되는 현상을 수정하였습니다.
  - styles.textWrap가 `normal`일때 fitRowHeight로 자동행높이 조절시 일부 글자가 표시되지 않는 현상을 수정하였습니다.

1. [onRowsPasted](https://help.realgrid.com/api/GridBase/onRowsPasted/)
  - 여러줄을 붙여넣기후 발생되는 onRowsPasted의 items인자에 `-1`만 넘어오는 현상을 수정하였습니다.

1. [getItemIndex](https://help.realgrid.com/api/GridBase/getItemIndex/)
  - treeView에서 편집중인 행의 dataRow를 이용해서 getItemIndex를 호출하는 경우 -1이 return되는 현상을 수정하였습니다.


## 1.1.36 (2020년 11월)

---

### 기능 개선

1. [ExcelExport]({{ '/Excels/ExcelExport/' | prepend: site.baseurl}})
  - 숨겨진 column을 excel로 export할때 mergeRule이 설정되어있어도 merge가 되지 않는 현상을 개선하였습니다.
  - 숨겨진 groupColumn을 excel export할때 style이 적용되지 않는 현상을 개선하였습니다.

1. [DataColumn](http://help.realgrid.com/api/types/DataColumn/)
  - ColumnFilter가 설정된 Column의 header에 표시되는 filter-icon을 표시하지 않도록 하는 `filterIconVisible` 속성이 추가되었습니다.
```js
gridView.setColumn([{
  name: "column",
  fieldName: "field",
  filters:[{
      ...
  }],
  filterIconVisible: false
}])
```

1. `Mac의 touch pad`에서 스크롤
  - Mac의 touch pad를 이용해서 스크롤을 했을때 수직/수평 스크롤이 동시에 일어나는 현상을 일부 개선하였습니다.

1. [MobileOptions](http://help.realgrid.com/api/types/MobileOptions/)
  - ColumnHeader를 touch후 drag했을때 범위선택또는 그리드 스크롤을 선택할수 있도록 headerToScroll속성이 추가되었습니다.
  - mobileOptions.headerToScroll을 true로 설정하면 ColumnHeader를 drag시 그리드가 스크롤 됩니다.


### 오류 수정

1. [DataColumn](http://help.realgrid.com/api/types/DataColumn/)
  - 연결된 field의 dataType이 `number`인 컬럼의 required속성을 true로 설정했을때 `0`을 입력하지 못하는 현상이 수정되었습니다.

1. [ColumnFilter](http://help.realgrid.com/api/types/ColumnFilter/)
  - TreeView의 ColumnFilter.criteria에 funtion을 설정후 filtering을 했을때 오류가 발생하는 현상을 수정하였습니다.

1. [fillXmlData](http://help.realgrid.com/api/LocalDataProvider/fillXmlData/)
  - `fillXmlData`를 이용해서 data를 load할때 값이 없는 속성의 경우 false로 변환되는 현상을 수정하였습니다.

1. [PasteOptions](http://help.realgrid.com/api/types/PasteOptions/)
  - pasteOptions.eventEachRow가 true이면서 여러행을 붙여넣기할때 행추가되는 경우 발생하는 오류를 수정하였습니다.

1. [fitRowHeight](http://help.realgrid.com/api/GridBase/fitRowHeight/)
  - displayOptions.fitStyle이 "none"이 아닐때 fitRowHeight를 호출하는 경우 높이가 잘못 계산되는 현상을 수정하였습니다.



## 1.1.35 (2020년 08월)

---

#### 기능 개선

1. [ExcelExport]({{ '/Excels/ExcelExport/' | prepend: site.baseurl}})
  - [LinkCellRenderer](http://help.realgrid.com/api/types/LinkCellRenderer/)를 사용한 셀을 export할때 url도 export하도록 하는 [GridExportOptions](http://help.realgrid.com/api/types/GridExportOptions/).exportLink 속성이 추가되었습니다.
```js
gridView.exportGrid({type:"excel", target:"local", exportLink:true})
```

1. [CheckBar](http://help.realgrid.com/api/types/CheckBar/)
  - checkBar.disableCheckImageUrl속성과 checkbar.disableUnCheckImageUrl 속성이 추가되었습니다.
  - checkable이 false일때 표시되는 이미지의 url을 지정합니다.
```js
grid.setCheckBar({
    disableCheckImageUrl: "./images/disableCheckImage.png",
    disableUnCheckImageUrl: "./images/disableUnCheckImageUrl.png"
})
```  

1. `safari`에서 가상키보드
  - iPad/iPhone safari의 userAgent가 변경됨에 따라 모바일을 체크하는 부분을 변경하였습니다.
  - 모바일 safari에서 그리드를 클릭했을때 가상키보드가 생성되는 현상이 개선되었습니다.

1. [moveRow](http://help.realgrid.com/api/LocalDataProvider/moveRow/)
  - dataProvider.moveRow를 이용해서 행을 이동할때 check상태도 함께 이동되도록 개선되었습니다.

1. [FilterSelectorOptions]http://help.realgrid.com/api/types/FilterSelectorOptions/)
  - filter Selector가 그리드 외부에 생성될수 있도록 viewGridInside속성이 추가되었습니다.
  - enterCallback속성이 추가되었습니다. default는 false입니다.
  - true로 설정하면 search창에서 enter키를 입력했을때 userFilterAddCallback이 실행됩니다.

1. `styles`
  - fontLineThrough속성이 추가되었습니다.

1. [DisplayOptions](http://help.realgrid.com/api/types/DisplayOptions/)
  - liveScroll이 false일때 topItem의 정보를 표시하는 tipView가 추가되었습니다.
  - scrollBar의 thumb를 마우스로 이동시 위치정보를 표시하는 view가 그리드 오른쪽 상단에 표시됩니다.  
```css
.rg-scroll-tip-view {
  border: 1px solid red;
  background: white;
  font-size: 12px;
  white-space: nowrap;
  border-radius: 4px;
}
```
```js
grid.setDisplayOptions({
    scrollMessageCallback:function(grid, vertical, itemIndex) {
      if (vertical === "vertical") {
        var dataRow = grid.getDataRow(itemIndex); 
        if (dataRow >= 0) {
          return "<span style='color:red'>"+grid.getDataSource().getValue(dataRow, "keyFieldName")+"</span>"
        }
      }
    }
});
```

1. [SearchOptions](http://help.realgrid.com/api/types/SearchOptions/)
  - dataComparer속성이 추가되었습니다.
  - 사용자가 검색조건을 작성하고 조건에 해당하면 true를 return합니다.
```js
  grid.grid.searchCell({ 
    fields:["field1", "field2"], 
    value:"검색 조건",
    dataComparer: function(dataRow, fieldIndex, data, search) {
      // dataType에 따라 분리 필요.
      // number/ datetime의 경우 replace/indexOf에서 오류 발생.
      if (value && (search = String(search))) {
        value = value.replace(/[" "]/gi, "");  // 공백제거
        search = search.replace(/[" "]/gi, "");
        return (value.indexOf(search) >= 0 || search.indexOf(value) >= 0);
      }
    }
})
```

1. [TreeView]({{'/Tree/TreeDataModel/' | prepend: site.baseurl}})
  - treeView에서 노드를 접거나 펼칠때 기존에 선택된 행이 유지되도록 수정되었습니다.
  - 선택된 행이 화면에서 사라지는 경우 접거나 펼쳐지는 노드로 포커스가 이동되도록 수정되었습니다.

1. [ImageButtonCellRenderer](http://help.realgrid.com/api/types/ImageButtonCellRenderer/), [ImageButtonsCellRenderer](http://help.realgrid.com/api/types/ImageButtonsCellRenderer/)
  - button에 마우스가 올라가면 tooltip이 표시되도록 개선되었습니다.
```js
grid.setColumns([{
    name:"column1",
    fieldName:"fieldName",
    renderer:{
        type:"imageButtons",
        images:[{
            name:"button1",
            up:"./images/button_up.png",
            tooltip:"버튼을 클릭하세요",
            showTooltip: true
        }]
    }
}]);
```


#### 오류 수정
1. [checkRow](http://help.realgrid.com/api/GridBase/checkRow/)
  - 행이 편집중일때 checkRow를 이용해서 체크를 변경할수 없는 현상을 수정하였습니다.

1. [ColumnFooter](http://help.realgrid.com/api/types/ColumnFooter/)의 excel export
  - footer.groupCallback의 return값이 문자인경우 export되지 않는 현상을 수정하였습니다.

1. [ColumnHeader](http://help.realgrid.com/api/types/ColumnHeader/).subText
  - header.subTextLocation이 "none"이거나 null인경우 export되지 않는 현상을 수정하였습니다.

1. `column.fillWidth`
  - 그룹컬럼의 자식컬럼에 fillWidth가 있을때 그룹컬럼의 헤더경계를 더블클릭했을때 그룹컬럼이 사라지는 현상을 수정하였습니다.

1. [keepNullFocus](http://help.realgrid.com/api/types/GridOptions/)
  - keepNullFocus가 true일때 그리드에 포커스를 주지 않고 스크롤후 checkBar의 check를 변경했을때 첫번째 행으로 포커스가 이동하는 현상을 수정하였습니다.

1. [maxLengthToNextCell](http://help.realgrid.com/api/types/EditOptions/)
  - mask 편집기의 includeFormat이 true일때 editOptions.maxLengthToNextCell이 true로 설정되면 값 입력시 바로 다음셀로 넘어가는 현상을 수정하였습니다.

1. `TreeDataProvider`
  - `restoreMode`가 true일때 dataType이 date인 field를 setVaue를 이용해서 값을 변경시 rowState가 "none"으로 변경되는 현상을 수정하였습니다.
  - dateFormat이 "yyyyMMdd"인 field에 setValue를 이용해서 값을 넣으면 format이 적용되지 않는 현상을 수정하였습니다.

1. [TreeDataProvider.setValue](http://help.realgrid.com/api/TreeDataProvider/setValue/)
  - field의 dataType이 `datetime`일때 format에 상과없이 string으로 값을 입력시 date형태로 변환되지 않는 오류를 수정하였습니다.

1. [ColumnGroup](http://help.realgrid.com/api/types/ColumnGroup/)
  - 컬럼그룹이 있는 경우 rowStylesFirst가 true일때 fixed 속성이 적용안되는 현상을 수정하였습니다.

1. `TreeView`
  - 데이터 재조회한 후 포커스를 이전위치로 이동시킬 때 현재 화면의 포커스 표시 여부에 따라 스크롤 위치가 달라지는 현상을 수정하였습니다.

1. `mobile Focus`
  - mobile의 일부 브라우저에서 가상키보드 생성시 그리드가 포커스를 가져가는 현상을 수정하였습니다.

1. `numberFormat`
  - sytles.numberFormat에 floor을 지정한 경우 일부 잘못된 값이 표시되는 현상을 수정하였습니다.\

1. `editFormat`
  - numberEditor의 editFormat에서 소수점 이하 자릿수가 큰경우 편집시 소수가 일부 짤려서 표시되는 현상을 수정하였습니다.


## 1.1.34 (2019년 10월)

---

#### 기능 개선

1. [ColumnHeader](http://help.realgrid.com/api/types/ColumnHeader/)
  - mobile기기에서 column의 header를 터치하면 tooltip이 보여지도록 개선되었습니다.

1. [Styles]({{ '/GridStyle/StyleProperties/' | prepend: site.baseurl}})
  - gridView.columnByName을 이용해서 Column의 정보를 가져올때 footer, header의 스타일정보도 가져올수 있도록 개선되었습니다.

1. [getStyles](http://help.realgrid.com/api/GridBase/getStyles/)
  - gridView.body에 설정한 dynamicStyles, cellDynamicStyle의 정보를 가져올수 있도록 수정되었습니다.
  - dynamicStyles를 function으로 지정한 경우에는 그리드 내부에서 관리되는 형태로 출력됩니다.

1. [onCellPasting](http://help.realgrid.com/api/GridBase/onCellPasting/)
  - 붙여넣기를 할때 Cell별로 호출되는 onCellPasting event가 추가되었습니다.
  - onCellPasting이벤트에서 true를 return하는 경우 셀이 readOnly여도 붙여넣기가 됩니다.
  - false를 return하는 경우 readOnly에 상관없이 붙여넣기가 되지 않습니다.
  - undefined를 return하면 pasteOptions.checkReadOnly가 true인경우 cell의 editable이 false이거나 readOnly가 true인경우 붙여넣기가 되지 않습니다.
```js
gridView.onCellPasting = function (grid, index, value) {
  if (index.column === 'column2')
  var val1 = grid.getValue(index.itemIndex, 'column1');
  switch (val1) {
      case 1 :
        return false;
      case 2 :
        return true;
  }
}
```

1. [onCopy](http://help.realgrid.com/api/GridBase/onCopy/)
  - 사용자가 ctrl+c 키를 입력했을때 발생하는 onCopy event가 추가 되었습니다.
```js
gridView.onCopy = function(grid, range, event) {
  var data = JSON.stringify(grid.getSelectionData());
  if (data) {
      data = 'onCopy\r\n'+data;
    if (window.clipboardData) {
        window.clipboardData.setData("Text", data);
    } else {
        event.clipboardData.setData('text/plain', data);
    }
  }
  return false;
}
```  
  - false를 return하면 복사를 하지 않습니다.
  - window.clipboardData 또는 event.clipboardData를 이용해서 임의의 data를 입력할수 있습니다.

1. [copyOptions](http://help.realgrid.com/api/types/CopyOptions/)
  - 그리드를 복사할때 Column Header의 Text를 추가할수 있도록 includeHeaderText 속성이 추가되었습니다.

1. [IconCellRenderer](http://help.realgrid.com/api/types/IconCellRenderer/)
  - iconLocation이 RIGHT인경우 text가 icon을 덮었쓰는 현상을 개선하였습니다.

1. `touch scroll`
  - 터치 스크린이 있는 노트북, 테블릿에서 화면터치를 이용한 스크롤이 되도록 개선하였습니다.


#### 오류 수정

1. [EditorOptions](http://help.realgrid.com/api/types/EditorOptions/)
  - editorOptions.applyCellFont가 true일때 동적으로 editable이 변경되는 셀에서 editor가 정상적으로 표시되지 않는 현상을 수정하였습니다.

1. [exportGrid](http://help.realgrid.com/api/GridBase/exportGrid/)
  - Excel로 export시 hideColumns를 이용해서 ColumnGroup의 하위 Column을 모두 숨기는 경우 발생하는 오류를 수정하였습니다.

1. [getDistinctValues](http://help.realgrid.com/api/DataProvider/getDistinctValues/)
  - getDistinctValues를 사용할때 간헐적으로 발생하는 오류를 수정하였습니다.

1. [Sorting](http://help.realgrid.com/api/features/Sorting/)
  - Data가 duplicate된 Column을 정렬시 Stack overflow가 발생하는 현상을 수정하였습니다.

1. [exportGrid](http://help.realgrid.com/api/GridBase/exportGrid/)
  - excelFormulaStatement가 적용된 cell을 export시 cell에 값이 없는 경우 excelFormulaStatement가 적용되지 않는 오류를 수정하였습니다.


## 1.1.33 (2019년 7월)

---

#### 기능 개선

1. [pasteOptions](http://help.realgrid.com/api/types/PasteOptions/)
  - pasteOptions에 convertLookupLabel속성이 추가되었습니다.
  - true로 설정하면 `dropdown`편집기에 label값을 붙여넣는 경우 value로 변환해서 저장됩니다.
  - 자세한 내용은 [데모]({{'http://demo.realgrid.com/Editing/CopyAndPaste/' | prepend:siteurl}})를 참조하세요.

1.  [expression](http://help.realgrid.com/api/features/Expression/)
  - column.footer.expression에 `datacount`와 `dataavg`가 추가되었습니다.
  - `datacount`와 `dataavg`는 data가 있는 cell을 대상으로 계산합니다.
```js
gridView.setColumns([
  {name:"colName1", fieldName:"field1", footer:{expression:"datacount", groupExpression:"datacount"}},
  {name:"colName2", fieldName:"field2", footer:{expression:"dataavg", groupExpression:"dataavg"}}
])
```

1. [getChildColumnNames](http://help.realgrid.com/api/GridBase/getChildColumnNames/)
  - GroupColumn의 하위 컬럼명을 가져오는 getChildColumnNames api가 추가되었습니다.
  - [columnByName](http://help.realgrid.com/api/GridBase/columnByName/)으로 GroupColumn정보를 가져오는 경우 columns속성을 이용해서 하위 컬럼을 확인할수 있습니다.
```js
var childCols = gridView.getChildColumnNames('colGroup');
var groupCol = gridView.columnByName('colGroup');
```

1. [DateCellEditor](http://help.realgrid.com/api/types/DateCellEditor/)
  - dateCellEditor에 휴일을 표시할수 있는 holidays속성이 추가되었습니다.
```js
var holidays = [ {
  type : "day", // 요일을 지정합니다.
  days : [0,6], // 일요일,토요일
  styles : {foreground:"#FFFF00FF"}, // 배경색과 폰트색을 지정합니다.
  tooltips : ["일요일","토요일"], // tooltip
  enabled : true  // false인경우 선택할수 없습니다.
}, {
  type : "date", // 기념일 또는 특정일자를 지정합니다.
  dates : ["01-01","03-01","05-05","08-15"], // 기념일.
  styles:{foreground:"#FF0000FF"},
  tooltips : ["신정","삼일절","어린이날","광복절"]
}, {
  type:"date",  // 동일한 type을 중복해서 지정할수 있습니다.
  dates:["2019-05-06"],
  styles:{foreground:"#FFF0F0FF", background:"#88FF00FF"},
  tooltips:["어린이날 대체휴무"]
}
];
gridView.setColumns([{
  name:"colName",
  field:"dateField",
  editor:{
      type:"date",
      holidays:holidays
  }
}])
```
  - 자세한 내용은 [데모](http://demo.realgrid.com/Editing/Editors/)를 참조하세요.

1. [MultiLineCellEditor](http://help.realgrid.com/api/types/MultiLineCellEditor/)
  - multilineEditor에 altEnterNewLine 속성이 추가되었습니다.
  - altEnterNewLine속성을 true로 설정하면 alt+enter키 입력시 줄바꿈을 합니다.

1. `TreeView`
  - treeView.options에 sortMode속성이 추가되었습니다.
  - "explicit"으로 설정시 정렬된 컬럼의 data를 수정했을때 즉시 정렬되지않습니다.

1. `Mobile Tooltip`
  - mobile기기에서도 tooltip을 사용할수 있도록 [moblieOptions](http://help.realgrid.com/api/types/MobileOptions/).showTooltip 속성이 추가되었습니다.

#### 오류 수정

1. [fitRowHeight](http://help.realgrid.com/api/GridBase/fitRowHeight/)
  - 개별행의 높이를 변경가능할때 fitRowHeight를 이용해서 높이자동계산을 할때 일부 잘못계산되는 현상을 수정하였습니다.

1. 행 추가 후 포커스 이동 시 잔상이 남아있는 현상
  - api를 이용해서 dataProvider.insertRow후 gridView.setCurrent를 실행했을때 간헐적으로 이전행의 data가 보이는 현상을 수정하였습니다.

1. [CellMerging]({{'/CellComponent/CellMerging/' | prepend: site.baseurl}})
  - 병합된 컬럼의 editor가 `dropdown`이거나 `date`인경우 edit button클릭시 다른 행에 dropdown이 표시되는 현상을 수정하였습니다.

1. `TreeView`
  - treeView에서 dynamicStyles로 동적 편집기 설정이 정상적으로 되지 않는 오류를 수정하였습니다.

1. [MergedRowGrouping]({{'/RowGroup/MergedRowGrouping/' | prepend: site.baseurl}})
  - 행병합그룹핑에서 [createFooterCallback](http://help.realgrid.com/api/types/RowGroupOptions/)을 이용해서 footer의 일부만 표시할때 행을 접었다가 다시 펼칠때 펼쳐지지 않는 현상을 수정하였습니다.

1. [hideRows](http://help.realgrid.com/api/DataProvider/hideRows/)
  - 그리드의 filterMode와 sortMode가 "explicit"일때 dataProvider.hideRows를 했을때 일부 정상적으로 작동하지 않는 현상을 수정하였습니다.

1. `Clipboard 복사`
  - IE에서 0 또는 false값을 복시 오류가 발생하는 현상을 수정하였습니다.

1. [NumberCellEditor](http://help.realgrid.com/api/types/NumberCellEditor/)
  - numberCellEditor.numberFormat에 소수점 이하 자리를 지정했을때 일부 데이타가 반올림되어 편집기에 표시되는 현상을 수정하였습니다.

1. [fillCsvData](http://help.realgrid.com/api/LocalDataProvider/fillCsvData/)
  - fillCsvData의 options.fillMode가 "append"일때 발생하는 오류를 수정하였습니다.

1. [ExcelExport]({{'/Excels/ExcelRowGroup/' | prepend:site.baseurl}})
  - column의 dynamicStyles에 function을 설정한 후 RowGrouping상태에서 일부 Group을 접고 export하는 경우 발생하는 오류를 수정하였습니다.

1. [RowGrouping]({{'/RowGroup/RowGrouping/' | prepend:site.baseurl}}})
  - 행그룹핑에서 값이 없는 경우 Grouping 된 Row가 3행이하일때와 3행이상일때 다르게 표시되는 현상을 개선하였습니다.


## 1.1.32 (2019년 4월)

---

#### 기능 개선
1. [DataColumn](http://help.realgrid.com/api/types/DataColumn/)
  - lookupValue 또는 lookupSource를 사용하는 셀에서 Data가 lookup에 없는 경우 지정된 Text로 보여지도록 하는 textOfInvalid 속성이 추가 되었습니다.
  - [expression](http://help.realgrid.com/api/features/Expression/)에 lookupexists가 추가 되었습니다.
```js
gridView.setColumns([{
  name:"colName",
  fieldName:"fieldName",
  lookupDisplay:true,
  values:["1","2","3"],
  labels:["일","이","삼"],
  textOfInvalid:"수정필요",
  dynamicStyles:[{
    criteria:"not lookupexists",
    styles:{foreground:"#FFFFFFFF", background:"#FF919bad"}
  }]
},
...])
```

1. `IE에서 붙여넣기`
  - IE에서 선택된 셀이 readOnly이거나 textReadOnly인 경우에도 붙여넣기가 가능하도록 개선되었습니다.

1. [CheckCellRenderer](http://help.realgrid.com/api/types/CheckCellRenderer/)
  - CheckCellRenderer를 편집기로 이용할때 컬럼의 readOnly가 true인 경우 수정되지 않도록 변경되었습니다.
```js
gridView.setColumns([{
  name:"colName",
  fieldName:"fieldName",
  editable:false,
  renderer:{type:"check", editable:true},
  dynamicStyles:function(grid, index, value) {
    if (grid.getValue(index.itemIndex, "fieldName") === "test") {
      return {readOnly:true}
    }
  }
},
...])
```  

1. [GridExportOptions](http://help.realgrid.com/api/types/GridExportOptions/)
  - displayOptions.fitStyle이 지정되었을때 실제 화면에 보이는 컬럼너비대로 출력하는 `applyFitStyle` 속성이 추가되었습니다.

1. [panel](http://help.realgrid.com/api/types/Panel/)
  - 그리드 Group Panel의 `borderBottom`과 `paddingLeft`가 적용되도록 수정되었습니다.
```js
gridView.setStyles({panel:{paddingLeft:20, borderBottom:"#FF828282,2px"}});
```

1. `ScrollBar Styles`
  - scrollBar의 스타일을 변경할수 있도록 개선되었습니다.
```js
gridView.setStyles({"scrollBar":{
    "background":"#fff0f0f0",
    "thumb":{
      "background":"#ffc0c0c0",
      "hoveredBackground":"#ffa0a0a0",
      "selectedBackground":"#ff808080"
    },
    button:{
      "background":"#fff0f0f0",
      "hoveredBackground":"#ffd0c0d0",
      "selectedBackground":"#ff808080",
      "foreground":"#ff333333",
      "hoveredForeground":"#ff333333",
      "selectedForeground":"#ffffffff"
    }
  }
});
gridView.setOptions({"scrollThumbRadius":8});
```

1. [EditMask](http://help.realgrid.com/api/types/Mask/)
  - Editor에 mask가 설정되어있는 경우 한글입력이 제한되도록 변경되었습니다.
  - editMask에 해당하지 않는 문자는 붙여넣기에서 제외되도록 하는 `applyEditMask` 속성이 추가되었습니다. 
  - dynamicStyles를 이용해서 mask를 변경하는 경우 append되는 셀의 editMask는 적용되지 않습니다.
```js
gridView.setColumnProperty("colName", "editor", {
  type:"text",
  mask:{
    editMask:"0000-0000-0000",
    allowEmpty:true      
  }
});
gridView.setPasteOptions({applyEditMask:true});
```  

1. [ColumnFilter](http://help.realgrid.com/api/types/ColumnFilter/)
  - 그리드에 정해진 criteria변수만으로 filtering이 어려운 경우 사용자함수를 이용해서 filtering을 할수 있도록 개선되었습니다.
```js
var filterFunc = function(dataProvider, dataRow, fieldName , filter, value) {
  function checkSocialNumber(gubun , socialNo) {
      // 주민번호/사업자번호 검증로직.
  };
  var tag = filter.tag;
  switch (tag) {
      case 1 : return checkSocialNumber(1, value);
      case 2 : return checkSocialNumber(2, value);
      case 3 : return !checkSocialNumber(1, value);
      case 4 : return !checkSocialNumber(2, value);
  }
}
```
```js
var filters = [
  { 
    name: "filter1",
    text:"주민번호 정상",
    tag:1,
    criteria:filterFunc
  }, {
    name:"filter2",
    text:"사업자번호 정상",
    tag:2,
    criteria:filterFunc
  }, { 
    name: "filter3",
    text:"주민번호 오류",
    tag:3,
    criteria:filterFunc
  }, {
    name:"filter4",
    text:"사업자번호 오류",
    tag:4,
    criteria:filterFunc
  }
]
grid.setColumnFilters("socialNo", filters)
```  
  - 자세한 내용은 [데모](http://demo.realgrid.com/Columns/ColumnFiltering/)를 참조하세요.

1. [getContainer](http://help.realgrid.com/api/GridBase/getContainer/)
  - 그리드의 DIV를 가져오는 `getContainer`함수가 추가되었습니다.

1. [checkValidateCells](http://help.realgrid.com/api/GridBase/checkValidateCells/)
  - checkValidateCells를 이용해서 전체데이타를 검증할때 보이지 않는 행도 검사할수 있도록 `visibleOnly` 인자가 추가되었습니다.
  - checkValidateCells의 itemIndices 인자는 `null`, visibleOnly는 true인경우 전체행을 대상으로 오류를 확인합니다.
```js
  gridView.checkValidateCells(null, true);
```

1. [ExportGrid](http://help.realgrid.com/api/GridBase/exportGrid/)
  - 그리드를 excel로 export할때 data가 없는 셀은 data를 출력하지 않도록 변경되었습니다. 

1. [fitColumnWidth](http://help.realgrid.com/api/GridBase/fitColumnWidth/)
  - gridView.fitColumnWidth를 이용해서 컬럼의 너비를 변경할때 summary가 있는 경우 summary의 너비도 포함하도록 변경하였습니다.

1. [fillEditSearchItems](http://help.realgrid.com/api/GridBase/fillEditSearchItems/)
  - [SearchCellEditor](http://help.realgrid.com/api/types/SearchCellEditor/)에 검색된 자료가 많은 경우 editor가 느리게 생성되는 경우 일부만 표시하여 editor를 빠르게 생성할수 있도록 수정되었습니다.
  - 서버에서 모든 자료를 가져온후 list에 보여지는 건수만 제한합니다.
  - initCount:최초 화면에 보여질 Data 건수
  - moreItemCount: 더보기 버튼을 클릭했을때 추가할 건수
  - moreText: 더보기 버튼의 caption
  - reInquery: 사용자가 editor에 문자를 추가했을때 다시 검색하지 않고 list에서 찾기
```js
var searchEditor = {
  type:"search", 
  initCount:50, 
  moreItemCount:50,
  moreText:"more",
  reInquery:false}
};
gridView.setColumnProperty("colName", "editor", searchEditor)
```

1. [pasteOptions](http://help.realgrid.com/api/types/CellEditor/)
  - editor에 maxLength가 지정된 경우 maxLength만큼만 붙여넣기가 되도록 하는 applyMaxLength 속성이 추가 되었습니다.
  - 붙여넣기 하는 data의 길이가 editor의 maxLength보다 긴경우 maxLength이후의 문자는 붙여넣기가 되지 않습니다.


#### 오류 수정
1. [removeRow](http://help.realgrid.com/api/LocalDataProvider/removeRow/)
  - onItemChecked 이벤트 또는 onCellButtonClicked 이벤트 내부에서 마지막 행을 삭제시 오류가 발생하는 현상을 수정하였습니다.

1. [HeaderSummary](http://help.realgrid.com/api/types/HeaderSummary/)
  - 그리드가 생성된 이후 headerSummary의 mergeCells를 변경했을때 즉시 갱신되지 않는 현상을 수정하였습니다.

1. [RowGrouping](http://help.realgrid.com/api/features/Row%20Grouping/)
  - rowGrouping을 한 상태에서 rowGrouping이 된 컬럼을 수정시 간헐적으로 발생하는 오류를 수정하였습니다.

1. [붙여넣기]({{'/Editing/CopyAndPaste/' | prepend: site.baseurl}})
  - pasteOptions.checkReadOnly가 true일때 추가중인 행에 붙여넣기를 하면 오류가 발생하는 현상을 수정하였습니다.

1. [ExportGrid](http://help.realgrid.com/api/GridBase/exportGrid/)
  - rowGroup.mergeMode가 true이고 모든 컬럼이 rowGrouping된 상태일때 excel로 export하면 excel 파일을 열때 발생하는 오류를 수정하였습니다.

1. [CellMerging]({{'/CellComponent/CellMerging/' | prepend: site.baseurl}})
  - column.mergeRule의 criteria가 "value"가 아닐때 간헐적으로 발생하는 오류를 수정하였습니다.

1. [Footer](http://help.realgrid.com/api/types/Footer/)
  - [grid.setFooter](http://help.realgrid.com/api/GridBase/setFooter/)를 이용해서 Footer의 mergeCells를 포함하여 두가지 이상의 속성을 변경하는 경우 즉시 갱신되지 않는 오류를 수정하였습니다.



## 1.1.31 (2019년 1월)

---

#### 기능 개선
1. [DynamicStyle](http://help.realgrid.com/api/types/DynamicStyle/)
  - dynamicStyle에서 셀의 editable과 readOnly를 지정할수 있도록 개선되었습니다.
  - 셀의 cursor를 변경할수 있도록 개선되었습니다.
```js  
gridView.setColumns([{
  name:"columnName",
  fieldName:"fieldName",
  dynamicStyles:function(grid, index, value) {
    var ret = {};
    var s = grid.getValue(index.itemIndex, "column1");
    ret["editable"] = s === "1" || s === "2";
    ret["readOnly"] = s === "2";
    ret["cursor"] = s === "3" ? "move" : "auto";
    return ret;
  }
}]);
```
  - editor의 속성을 변경할수 있도록 개선되었습니다.
  - 아래의 코드는 "kind" field의 값에 따라 법인번호 또는 사업자번호형식으로 입력받도록 editor의 속성을 변경합니다.
```js
gridView.setColumns([{
  name:"columnName",
  fieldName:"fieldName",
  dynamicStyles:function(grid, index, value) {
    var kind = grid.getValue(index.itemIndex, "kind");
    var ret = {};
    switch (kind) {
      case '0' :  // 법인번호.
        ret.editor = {
          type:"text", 
          mask:{
            editMask:"000000-000000", allowEmpty:true, includedFormat:false   
          }
        };
        break;
      case '1' :  // 사업자번호
        ret.editor = {
          type:"text",
          mask:{
            editMask:"000-00-00000", allowEmpty:true, includedFormat:false
          }
        }
        break;
    }
    return ret;
  }
}]);
```
  - 자세한 내용은 [동적 스타일 데모](/GridStyle/DynamicStyles/)를 참조하세요.

1. [DataColumn](http://help.realgrid.com/api/types/DataColumn/)
  - 그리드에 표시되는 값을 변경할수 있는 displayCallback이 추가되었습니다.
  - column.styles에 numberFormat, datetimeFormat 등이 있는 경우에는 displayCallback은 무시됩니다.
  - 정규식(column.displayRegExp,displayReplace)이 있는 경우 displayCallback은 무시됩니다.
  - excel로 export하는 경우 exportOptions.numberCallback, datetimeCallback, booleanCallback이 있는 경우 displayCallback은 무시됩니다.
```js
gridView.setColumns([{
  name:"columnName",
  fieldName:"fieldName",
  displayCallback:function(grid, index, value) {
    var kind = grid.getValue(index.item, "kind");
    switch(kind) {
      case "0" :
        return value && value.length > 6 ? value.substr(0,6)+'-'+value.substr(6,7) : value;
      case "1" :
        return value && value.length == 10 ? value.substr(0,3)+'-'+value.substr(3,2)+'-'+value.substr(5,5) : value;
    }
    return value;
  }
}])
```
  - 자세한 내용은 [동적 스타일 데모](/GridStyle/DynamicStyles/)를 참조하세요.

1. [Excel Export]({{'/Excels/ExcelExport/' | prepend: site.baseurl}})
  - excel Export시 컬럼을 화면에 보이는 컬럼을 export하지 않거나 또는 화면에 보이지 않는 컬럼을 export할수 있도록 [GridExportOptions](http://help.realgrid.com/api/types/GridExportOptions/)에 showColumns, hideColumns속성이 추가되었습니다.
  - `showColumns`에는 visible이 false이지만 excel로 export하고자 하는 컬럼을 배열로 지정합니다.
  - `hideColumns`에는 화면에 보이지만 excel로 export하지 않을 컬럼을 지정합니다.
```js
gridView.exportGrid({
  type:"excel",
  target:"local",
  showColumns:["column1"],
  hideColumns:["column2"]
});
```

1. [CheckBar](http://help.realgrid.com/api/types/CheckBar/)
  - 그리드 행을 체크했을때 checkBar.head의 체크상태를 연동시킬수 있는 syncHeadCheck속성이 추가되었습니다.
  - 모든 행이 체크된 경우 checkBar.head도 체크상태로 변경됩니다.
  - 체크가 해제되는 경우 head의 check상태가 해제됩니다.

1. [NumberCellEditor](http://help.realgrid.com/api/types/NumberCellEditor/)
  - numberCellEditor에서 space key를 입력시 입력값을 삭제할수 있도록 하는 `blankWhenSpace`속성이 추가되었습니다.

1. [CheckableExpression](http://help.realgrid.com/api/GridBase/setCheckableExpression/)
  - 그리드의 [setPaging](http://help.realgrid.com/api/GridView/setPaging/)을 이용하여 Paging모드로 변경하고 checkableExpression을 사용했을때 그리드의 현재 페이지에만 적용되되는 현상을 개선하였습니다.
  
1. [getRowHeight](http://help.realgrid.com/api/GridBase/getRowHeight/)
  - 그리드 행의 높이를 확인할수 있는 getRowHeight api가 추가되었습니다.

1. [RowGroupOptions](http://help.realgrid.com/api/types/RowGroupOptions/)
  - MergedRowGroup시 일부 그룹에만 footer를 표시할수 있도록 createFooterCallback 속성이 추가되었습니다.
  - createFooterCallback의 return값이 true인경우에만 해당 group의 footer를 화면에 표시합니다.
  - RowGroup.mergeMode가 true인경우에만 사용할수 있습니다.
```js
gridView.setRowGroup({
  mergeMode:true,
  createFooterCallback: function(grid, group) {
    if (group.level === 1) {
      return true; // 그룹의 level이 1인경우 footer를 표시.
    };
    if (group.level === 2) {
      return false; // 그룹의 level이 2인경우 footer를 표시하지 않음.
    };
    if (group.level === 3) {
      var division = grid.getDataSource().getValue(group.firstItem.dataRow, "division");
      return division === "1"  // field값에 따라 footer를 표시하거나 표시하지 않음.
    };
    return true;  // 그외의 경우 표시함.
  }
});
```

1. [DisplayOptions](http://help.realgrid.com/api/types/DisplayOptions/)
   - 그리드의 테두리를 일부만 그릴수 있도록 drawBorderLeft, drawBorderRight, drawBorderTop, drawBorderBottom속성이 추가되었습니다.
   - drawBorderLeft 속성을 false로 지정시 왼쪽테두리를 그리지 않습니다.  
```js
  gridView.setStyles({grid:{border:"#FF0FCFCF,2"}});
  gridView.setDisplayOptions({
    drawBorderLeft:false,
    drawBorderRight:false
  })
```   

#### 오류 수정
1. [ColumnGroup](({{ '/Columns/ColumnGrouping/' | prepend: site.baseurl }})
  - ColumnGroup의 하위 컬럼에 MergeRule이 적용되어있고 column.styles.background의 alpha값이 FF가 아닌 경우 셀의 잔상이 보여지는 현상이 수정되었습니다.

1. [fitColumnWidth](http://help.realgrid.com/api/GridBase/fitColumnWidth/)
  - Column.styles.textWrap이 "normal"일때 grid.fitColumnWidth를 이용해서 컬럼의 너비를 변경했을때 줄바꿈이 정상적으로 되지 않는 현상이 수정되었습니다.

1. [DataColumn](http://help.realgrid.com/api/types/DataColumn/)
  - Column.mergeRule에 의해서 병합된 column을 rowGrouping한 상태에서 첫번째 그룹의 셀을 선택후 그룹을 접었을때 merge된 셀의 잔상이 보여지는 현상이 수정되었습니다.

1. [CellButton]({{'/CellComponent/CellButton/' | prepend: site.baseurl}})
  - Column.buttonVisibility가 `always`이면서 그리드의 마지막행이 일부만 보여지고 있을때 마지막행의 버튼을 클릭하는 경우 [onImageButtonClicked](http://help.realgrid.com/api/GridBase/onImageButtonClicked/)이벤트의 itemIndex에 잘못된 index가 전달되는 현상을 수정하였습니다.

1. [LinkCellRenderer](http://help.realgrid.com/api/types/LinkCellRenderer/)
  - LinkCellRenderer가 적용된 컬럼의 경우 fitColumnWidth를 이용한 자동 너비변경이 안되는 오류를 수정하였습니다.

1. [exportGrid]({{ '/Excels/ExcelMultiExport/' | prepend: site.baseurl }})
  - RealGridJS.exportGrid를 이용해서 여러개의 그리드를 export한 파일을 최초 편집시 선택된 시트 외 다른 시트의 값이 동시에 변경되는 현상이 수정되었습니다.
  - 여러개의 그리드를 하나의 엑셀파일로 export한경우 Mac OS에서 읽지 못하는 현상을 수정하였습니다.
  - [LookupTree]({{ '/CellComponent/LookupTree/' | prepand: site.baseurl }})를 사용한 컬럼이 있는 그리드에서 rowGrouping한후 그룹을 접은 상태에서 export할때 발생하는 오류를 수정하였습니다.
  - Merged RowGroup에서  ExcelExport시 footerCellMerge를 사용했을때 footer의 merge가 잘못되는 현상을 수정하였습니다.

1. [Styles]({{ '/GridStyle/StyleProperties/' | prepend: site.baseurl}})
  - style의 fontUnderline을 true로 설정했을때 셀 MouseOver후 underline이 사라지는 현상을 수정하였습니다.

1. [HeaderSummary](http://help.realgrid.com/api/types/HeaderSummary/)
  - header.summary의 높이가 변경되지 않는 현상을 수정하였습니다.

1. `readOnly 상태의 컬럼이 스페이스바 키로 편집이 되는 현상`
  - readOnly인 셀을 선택한후 스페이스키를 입력하면 편집이 되는 현상을 수정하였습니다.



## 1.1.30 (2018년 10월)

---

#### 기능 개선
1. [GridOptions.resizeDelay](http://help.realgrid.com/api/types/GridOptions/#resizeDelay)
  - 그리드 DIV의 넓이 또는 높이가 '100%'일때 IE에서 Browser의 크기변경시 resetSize가 실행되면서 깜박거리는 현상이 줄이기 위한 gridOptions.resizeDelay속성이 추가되었습니다.
  - default는 undefined이며 resizeDelay가 설정되면 resize가 종료된후 resizeDelay에 지정된 시간이후에 resetSize가 실행됩니다.
```js
gridView.setOptions({resizeDelay:250});  
```

1. [GridOptions.keepNullFocus](http://help.realgrid.com/api/types/GridOptions/#keepNullFocus)
  - dataProvider에 setRows를 하거나 그리드를 refresh했을때 첫번째 셀에 자동으로 포커스가 생기지 않도록 하는 `keepNullFocus`속성이 추가되었습니다.
  - 그리드가 activeElement인 경우 keepNullFocus가 true여도 포커스가 표시됩니다.
```js
gridView.setOptions({keepNullFocus:true});
```

1. [getLeftPos](http://help.realgrid.com/api/GridBase/getLeftPos/), [setLeftPos](http://help.realgrid.com/api/GridBase/setLeftPos/)
  - 그리드의 가로위치를 가져올수 있는 getLeftPos 함수와 그리드의 가로위치를 변경할수 있는 setLeftPos함수가 추가되었습니다.

1. [Filtering](http://help.realgrid.com/api/features/Filtering/)
  - [setColumnFilters](http://help.realgrid.com/api/GridBase/setColumnFilters/) 또는 [clearColumnFilters](http://help.realgrid.com/api/GridBase/clearColumnFilters/) 등 컬럼 필터가 재지정될때 itemCount가 변경되지 않는 경우 선택된 셀이 변경되지 않도록 수정되었습니다.

1. [DataColumn.equalBlankExpression](http://help.realgrid.com/api/types/DataColumn/#equalBlankExpression)
  - 컬럼의 이전행과 동일한 값을 가지는 셀을 하나로 묶을때 다른 컬럼의 값을 참조할수 있도록 [equalBlankExpression] 조건이 추가되었습니다.
```js
gridView.setColumnProperty("columnnName", "equalBlankExpression","values['col1']+value");
```

1. [ColumnFilter](http://help.realgrid.com/api/types/ColumnFilter/)
  - [FilterSelector](http://help.realgrid.com/api/types/selector/)의 검색창에서 ctrl+enter를 입력시 호출되는 [userFilterAddCallback](http://help.realgrid.com/api/types/selector/#userFilterAddCallback) 속성이 추가되었습니다.
  - 전달되는 인자는 grid, column, text입니다.
  - column: 현재 filter selector가 popup된 컬럼입니다.
  - text: 사용자 입력한 문자열입니다.
```js
gridView.setFilteringOptions({
    selector:{
            userFilterAddCallback: function(grid, column, text) {
                return {
                    name: "filter_"+column.name+"_"+text,
                    text: text,
                    criteria: "value like '"+text+"%'",
                    active: true,
                }
            }
    }
});
```

1. [mergeRule]({{ '/CellComponent/CellMerging/' | prepend: site.baseurl }})
  - mergeRule을 이용해서 셀 병합시 선행컬럼을 참조할수 있는 'prevvalues' 수식이 추가 되었습니다.
```js
gridView.setColumn({
    name:"columnName",
    fieldName:"fieldName",
    mergeRule:{
            criteria:"prevvalues+value"
    }
})
```
  - 병합될 컬럼의 왼쪽에 있는 컬럼들의 값이 동일한 경우에 병합됩니다.

1. [GridOptions.backgroundImage](http://help.realgrid.com/api/types/GridOptions/#backgroundImage)
  - 그리드에 배경이미지를 그릴수 있는 기능이 추가되었습니다.
```js
gridView.setOptions({
  backgroundImage:{
      imageUrl:"./image/realgrid.jpg", 
      alpha:0.2, 
      location:"center", 
      padding:2
  }
})
```
  - imageUrl: 배경으로 사용할 이미지의 url을 입력합니다.
  - alpha: 투명도를 지정합니다.
  - location: 배경의 위치를 지정합니다. [BackgroundImageLocation](http://help.realgrid.com/api/types/BackgroundImageLocation/) 참조
  - padding: 여백을 지정합니다. padding 또는 paddingLeft, paddingRight, paddingTop, paddingBottom을 이용해서 지정합니다.

1. [CellRenderer](http://help.realgrid.com/api/features/Cell%20Renderer/)
  - mouse hover시 text에 밑줄을 표시하는 hoveredUnderline 속성이 추가되었습니다.
```js
gridView.setColumns([{
  name:"columnName",
  fieldName:"fieldName",
  renderer:{
      type:"text",
      hoveredUnderline:true
  }
}])
```

1. [fitStyle](http://help.realgrid.com/api/types/GridFitStyle/)
  - grid의 fitStyle을 "fill"로 변경했을때 그룹컬럼에 속해있는 컬럼들의 경우 fillWidth가 지정되어있어도 모든컬럼의 넓이가 배분되던것을 fillWidth가 지정된 컬럼의 넓이만 배분되도록 변경되었습니다.

1. [Mask](http://help.realgrid.com/api/types/Mask/#restrictNull)
  - 에디터에 mask가 설정되어있을때 앞자리를 입력하지 않으면 다음으로 이동할수 없도록 하는 `restrictNull` 속성이 추가되었습니다.
```js
    gridView.setColumnProperty("columnName","editor", {type:"text", mask:{editMask:"0000-99-00",restrictNull:true, allowEmpty:true}})
```

1. [onValidateColumn](http://help.realgrid.com/api/GridBase/onValidateColumn/#itemIndex)
  - onValidateColumn 이벤트에서 다른 field의 값을 확인 할수 있도록 itemIndex인자가 추가되었습니다.

1. [DateCellEditor](http://help.realgrid.com/api/types/DateCellEditor/#defaultShowDate)
  - Date Editor가 popup될때 선택되는 날짜를 지정하는 defaultShowDate 속성이 추가되었습니다.
  - "normal": 기존과 동일하게 셀에 data가 있는 경우 해당하는 날짜가 표시되고 data가 없는 경우 이전에 표시된 날짜가 선택된 상태로 popup됩니다.
  - "today": 항상 현재일자가 선택된 상태로 popup됩니다.
  - "todayWhenNull": 셀에 data가 있는 경우 해당하는 날짜가 표시되고 data가 없는 경우 현재일자가 표시됩니다.
  - defaultShowDate에 일자를 지정하면 data가 없는 셀에서 지정된 날짜로 popup됩니다.

1. [EditValidation](http://help.realgrid.com/api/features/Edit%20Validation/)
  - columnValidation의 criteria에서 다른 컬럼을 참조할수 있도록 [values](http://help.realgrid.com/api/features/Expression/#values) 조건이 추가 되었습니다.
```js
gridView.setColumnProperty("columnName", "validations", [{
  criteria:"((values['test1'] = 'A') and (value >= 10)) or (values['test1'] <> 'A') ",
  level:"error",
  message:"test1이 'A'인 경우 10 이상의 값을 입력해야 합니다."
}])
```

1. [DropdownCellEditor](http://help.realgrid.com/api/types/DropDownCellEditor/#displayLabels)
  - dropdownEditor의 dropdownList에서 value와 label을 동시에 보여줄수 있도록 displayLabels속성이 변경되었습니다.
```js
gridView.setColumnProperty("columnName", "editor", {
    type:"dropdown",
    separator: " ",
    itemColumned: false,
    displayLabels: "valueLabel"
})
```
  - separator: value와 label을 구분하는 문자열을 입력합니다. default는 " - " 입니다.
  - itemColumned: 처음 항목의 넓이를 동일하게 표시하도록 합니다.
  - [DropDownValueLabel](http://help.realgrid.com/api/types/DropDownValueLabel/): dropdownList에 표시될 항목을 지정합니다.


#### 오류 수정
1. [ImageButtonsCellRenderer](http://help.realgrid.com/api/types/ImageButtonsCellRenderer/)
  - 컬럼의 buttonVisibility가 "hidden"이어서 버튼이 숨겨져 있을때 버튼의 위치에서 커서가 변경되고 클릭이 발생되는 현상이 수정되었습니다.
  
1. [onShowTooltip](http://help.realgrid.com/api/GridBase/onShowTooltip/)
  - 그룹컬럼에 속한 컬럼에 mergeRule이 적용되어 있을때 onShowTooltip 이벤트의 Arguments중 index의 column이 GroupColumn으로 넘어오는 현상이 수정되었습니다.

1. `iFrame내에서 그리드가 스크롤되는 현상`
  - iFrame내에서 그리드를 사용할때 iFrame이 그리드보다 작거나 스크롤 되어 그리드가 일부만 보이는 상태에서 그리드를 클릭하면 그리드의 위치가 변경되는 현상이 개선되었습니다.

1. [setCellStyle](http://help.realgrid.com/api/GridBase/setCellStyle/)
  - setCellStyle(s) 등으로 적용된 스타일이 moveRow 사용시 잘못된 위치에 표시는 현상이 수정되었습니다.

1. [DropdownCellEditor](http://help.realgrid.com/api/types/DropDownCellEditor/)
  - dropdown Editor에서 dropdownList가 popup되지 않은 상태에서 Data를 삭제후 commit했을때 Data가 삭제되지 않는 현상이 수정되었습니다.

1. `화면 갱신시 오류`
  - dataProvider.setValue 또는 gridView.setValue시 일부 셀이 갱신되지 않고 이전 값이 표시되는 현상이 수정되었습니다.

1. [editMask](http://help.realgrid.com/api/types/Mask/)
  - chrome Browser에서 editor에 Mask속성을 설정한 상태에서 편집시 backspace키를 계속 입력시 caret의 위치가 끝으로 이동하는 현상이 수정되었습니다.



## 1.1.29 (2018년 8월)

---

#### 기능 개선
1. [ColumnFilter](http://help.realgrid.com/api/types/ColumnFilter/)
  - ColumnFilter를 화면에서 보이지 않도록 하는 hideColumnFilters 함수가 추가되었습니다.
  - ColumnFilter.visible 속성이 추가되었습니다. default는 true이며 false로 설정시 화면에서 보여지지 않습니다.
  - filter의 active는 visible상태에 상관없이 적용됩니다.
```js
gridView.hideColumnFilters("columnnName", ["filterNames"], true);
gridView.addColumnFilters("columnName", 
[ 
  {
      name:"filter1", 
      text:"filter1", 
      criteria:"value like 'test%'", 
      visible:true
  }, {
      name:"filter2",
      text:"filter2",
      criteria:"value like 'aaa%'",
      visible:false,
      active:true
  }
]
);
```
  - hideAllColumnFilters 함수가 추가되었습니다.
  - 자세한 내용은 [[데모]]({{ '/Columns/ColumnFiltering/' | prepend: site.baseurl }}) 를 참조하세요.

1. [DisplayOptions](http://help.realgrid.com/api/types/DisplayOptions/)
  - 그리드의 WheelEvent를 외부로 전파하지 하지 않도록 하는 wheelEventPropagate 속성이 추가되었습니다.
  - DisplayOptions.wheelEventPropagate 속성을 false로 설정시 그리드 외부로 스크롤이 전달되지 않습니다.
  - 그리드의 처음행 또는 마지막행이 보여지는 상태에서 스크롤을 했을때 브라우저 스크롤을 막는 경우 사용합니다.

1. [FilterSelectorOptions](http://help.realgrid.com/api/types/FilterSelectorOptions/)
  - ColumnFilter를 검색할수 있는 showSearchInput 속성이 추가되었습니다.
  - ColumnFilter를 선택시 여러개의 filter를 선택후 filtering이 실행되도록 하는 accept버튼이 추가되었습니다.
  - [FilteringOptions](http://help.realgrid.com/api/types/FilteringOptions/) filter를 검색후 선택했을때 화면에 보이지 않는 filter의 check를 유지하도록 하는 clearWhenSearchCheck 속성이 추가되었습니다.
  - clearWhenSearchCheck속성이 true인경우 FilterSelector화면에 보이지 않는 filter는 check가 해제됩니다.
```js
  gridView.setFilteringOptions({
    clearWhenSearchCheck: true,
    selector:{
      showSearchInput: true,
      showButtons: true, 
      acceptText:"선택",
      cancelText:"취소"
    }
  })
```  
  - 자세한 내용은 [[데모]]({{ '/Columns/ColumnFiltering/' | prepend: site.baseurl }}) 를 참조하세요.

1. [isFiltered](http://help.realgrid.com/api/GridBase/isFiltered/)
  - Column의 filter가 실행중인지 확인하는 isFiltered 함수가 추가되었습니다.
```js
  var isFiltered = gridView.isFiltered("columnName");
  var isFiltered = gridView.isFiltered();
```

1. [setEditValue](http://help.realgrid.com/api/GridBase/setEditValue/)
  - 그리드 편집기가 활성화 된 상태일때 editor의 값을 변경할수 있는 setEditValue 함수가 추가되었습니다.
  - 셀이 readOnly이거나 editable이 false인경우 editor의 값이 변경되지 않습니다.
  - editor가 표시되지 않는 checkCellRenderer인경우 사용할수 없습니다.
```js
  gridView.setEditValue("test", startEdit);
```
  - startEdit 인자가 true인경우 편집중인 아닌경우 편집상태로 변경하고 editor의 값을 변경합니다.

1. [LinkCellRenderer](http://help.realgrid.com/api/types/LinkCellRenderer/)
  - LinkeCellRenderer를 사용하는 셀에 url값이 없는 경우 마우스 포인터가 변경되지 않도록 수정되었습니다.

1. [DataColumn](http://help.realgrid.com/api/types/DataColumn/)
  - DataColumn.lookupDisplay가 true일때 해당컬럼을 화면에 보여지는 값으로 정렬하도록 하는 sortByLabel속성이 추가되었습니다.
```js
  gridView.setColumn({
    name: "columnName",
    fieldName: "fieldName",
    lookupDisplay: true,
    values: ['1','2','3','4','5','6'],
    labels: ['일','이','삼','사','오','육'],
    sortByLabel: true
  })
```
  - value값으로 정렬할때보다 약간의 속도 저하가 있을수 있습니다.

1. [onCurrentChanging](http://help.realgrid.com/api/GridBase/onCurrentChanging/)
  - 셀이 편집중인 경우 포커스의 이동을 제한할수 있도록 onCurrentChanging Event의 발생순서를 변경할수 있는 grid.changingMode 속성이 추가 되었습니다.
  - default는 ChangingMode.NORMAL 이며 기존과 동일하게 editCommit후 onCurrentChanging Event가 발생됩니다.
  - changingMode가 ChangingMode.BEFORE_EDITCOMMIT인 경우 editor commit이전에 onCurrentChaning이벤트가 호출됩니다. 이벤트의 결과값으로 false를 return하면 포커스 이동은 취소되고 편집중인 셀의 편집상태는 유지됩니다.
```js
  function validationValue(grid, index, value) {
    // value값 검증.
    return value검증 ? true : false;
  }
  gridView.setOptions({changingMode:RealGridJS.ChangingMode.BEFORE_EDITCOMMIT});
  gridView.onCurrentChanging = function(grid, oldIndex, newIndex) {
    if (grid.isEditing()) {
      var editValue = grid.getEditValue();
      return validationValue(grid, newIndex, editValue);
    }
  }
```

1. [ActualTargetBulletRenderer](http://help.realgrid.com/api/types/ActualTargetBulletRenderer/)
  - actualTargetBulletRenderer의 actual, target값에 numberFormat이 적용되도록 개선되었습니다.

1. [DisplayOptions](http://help.realgrid.com/api/types/DisplayOptions/)
  - 그리드의 스크롤바를 숨길수 있는 DisplayOptions.hscrollBar, DisplayOptions.vscrollBar 속성이 추가 되었습니다.

1. [StateBar](http://help.realgrid.com/api/types/StateBar/)
  - 행의 상태를 표시하는 StateBar 상태에 따른 이미지를 표시할수 있도록 stateImages 속성이 추가되었습니다.
```js
  gridView.setStateBar({
    mark:"image",
    stateImages:{
      "updated":"./images/state_updated.png",
      "created":"./images/state_created.png",
      "deleted":"./images/state_deleted.png",
      "createAndDeleted":"./images/state_createAndDeleted.png"
    }
  });
```
  - 행의 편집상태를 표시하는 [Indicator](http://help.realgrid.com/api/types/Indicator/)에 stateImages속성과 mark속성이 추가 되었습니다.
```js
  gridView.setIndicator({
    mark:"image",
    stateImages:{
      "focused":"./images/indicator_focused.png",
      "inserting":"./images/indicator_inserting.png",
      "updating":"./images/indicator_updating.png",
      "appending":"./images/indicator_appending.png"
    }
  });
```

1. [BTDateCellEditor](http://help.realgrid.com/api/types/BTDateCellEditor/)
  - BTDateCellEditor.commitOnSelect 속성이 추가 되었습니다.

1. `NumberFormat`
  - DataColumn.displayMinusZero 속성이 추가 되었습니다. 
  - displayMinusZero 속성이 false인 경우 numberFromat의 소수점이하 자리수가 Data의 소수점이하 자리수보다 작아서 "-0.00"으로 표시되는 경우 "0.00"으로 표시합니다.

1. [ImageButtonCellRenderer](http://help.realgrid.com/api/types/ImageButtonCellRenderer/)
  - cursor속성이 추가되었습니다.
  - mouse hover시 underline이 표시되지 않도록 하는 hoveredUnderline 속성이 추가되었습니다.

1. [onFilteringChanged](http://help.realgrid.com/api/GridBase/onFilteringChanged/)
  - onFilteringChanged 이벤트의 인자에 column이 추가되었습니다.
  - gridView.setColumns시 발생되는 onFilteringChanged 이벤트의 경우 column의 값이 undefined입니다.
```js
  gridView.onFilteringChanged = function(grid, column) {
    console.log(column && column.name);
    if (column && column.name == "maker") {
      var activeFilters = grid.getActiveColumnFilters("maker");
      var modelFilters = grid.getColumnFilters("model");
      var filter, makers = [];
      var hideFilters = [];
      var visibleFitlers = [];
      for (var i = 0, cnt = activeFilters.length; i < cnt ; i++) {
        filter = activeFilters[i];
        makers.push(filter.text);
      }
      grid.beginUpdate();
      try {
        for (var i = 0, cnt = modelFilters.length; i < cnt ; i++) {
          filter = modelFilters[i];
          if (makers.length > 0 && makers.indexOf(filter.description) < 0) {
            hideFilters.push(filter.name);
          } else {
            visibleFitlers.push(filter.name);
          }
        }
        grid.activateAllColumnFilters("model", false);
        grid.hideColumnFilters("model", hideFilters, true);
        grid.hideColumnFilters("model", visibleFitlers, false);
      } finally {
        grid.endUpdate();
      }
    }
  }
```
  - "maker"컬럼의 Filter를 변경했을때 선택된 maker의 model만 "model"컬럼의 Filter에 표시되도록 하는 샘플 코드입니다.

#### 오류 수정
1. [lookupColumn]({{ '/CellComponent/LookupColumn/' | prepend: site.baseurl }})
  - column.values에 공백('')이 입력되지 않는 오류가 수정되었습니다.

1. [checkBar]({{ '/GridComponent/CheckBar/' | prepend: site.baseurl }})
  - checkBar Head와 Cell의 check이미지의 위치가 1px틀어지는 것을 수정하였습니다.

1. [excelFormat](http://help.realgrid.com/api/types/DataColumn/)
  - setCellStyle 또는 dynamicStyle이 적용되어있는 Cell을 excel로 export할때 excelFormat이 사라지는 현상을 수정하였습니다.

1. [rowHeight](http://help.realgrid.com/api/GridBase/setRowHeight/)
  - 그리드의 넓이가 그리드의 높이보다 작은경우 setRowHeight를 실행했을때 넓이보다 커지지 않는 오류를 수정하였습니다.

1. [editor]({{ '/Editing/Editors/' | prepend: site.baseurl }})
  - 현재 선택된 Cell의 값이 null일때 gridView.setValue를 하고 키보드를 이용해서 delete키 입력후 enter키를 입력했을때 setValue로 입력한 값이 보이는 현상이 수정되었습니다.

1. `TreeView`
  - 트리그리드에서 최상위 노드가 1개인 경우 Sort가 안되는 현상이 수정되었습니다.
  - 트리그리드에서 첫번째행에 포커스가 있는 상태에서 Data를 다시 Load했을때 onCurrentRowChanged이벤크가 발생하지 않는 오류를 수정하였습니다.

1. [orderBy](http://help.realgrid.com/api/GridBase/orderBy/)
  - gridView.orderBy api에서 sortDirs인자값이 잘못된 경우 아이콘 표시가 반대로 되는 현상을 수정하였습니다.

1. [getDistinctValues](http://help.realgrid.com/api/DataProvider/getDistinctValues/)
  - dataProvider.getDistinctValues의 count인자를 1로 넘겼을때 2건의 자료가 return되는 오류를 수정하였습니다.

1. [dataField](http://help.realgrid.com/api/types/DataField/)
  - dataProvider.addField를 이용해서 추가한 dataField의 calculateExpression또는 calculateCallback이 적용되지 않는 오류가 수정되었습니다.

1. [filtering](http://help.realgrid.com/api/features/Filtering/)
  - focus가 첫번째 행에 있는 상태에서 columnFiltering을 하면 filter Selector화면이 닫히는 현상을 수정하였습니다.


## 1.1.28 (2018년 6월)

---

#### 기능 개선

1. `numberFormat` 
  - 숫자를 절대값으로 표현할수 있는 기능이 추가 되었습니다.
```js
gridView.setColumns([{
    name:"colName",
    fieldName:"fieldName",
    dynamicStyles:[{
        criteria:"value < 0",
        styles:{prefix:"[", suffix:"]", foreground:"#FFFF0000", numberFormat:"#,##0;.;,;a" // 또는 numberFormat:"#,##0;a"}
    }]
}])
```
  - 값이 음수인경우 글자색과 prefix, suffix를 지정하고 보여지는 값은 절대값으로 보여지도록 사용할수 있습니다.

1. [CheckBar](http://help.realgrid.com/api/types/CheckBar/)
  - CheckBar의 check표시를 Image를 이용해서 할수 있도록 개선되었습니다.
  - CheckBox.drawCheckBox 속성이 추가 되었습니다. `false`이면 CheckBox의 테두리를 그리지 않습니다.
```js
  gridView.setCheckBar({checkImageUrl:"./images/check.png", unCheckImageUrl:"./images/unCheck.png", drawCheckBox:false});
```

1.  [EditOptioins](http://help.realgrid.com/api/types/EditOptions/)
  - 그리드의 첫번째 컬럼에 해당하는 셀에 포커스가 있는 상태에서 Shift+Tab키를 입력하면 이전행의 마지막 셀로 포커스가 이동하도록 개선되었습니다.
  - editOptions.crossWhenExitLast가 true인경우 적용됩니다.

1. [DropDownCellEditor](http://help.realgrid.com/api/types/DropDownCellEditor/)
  - DataColumn의 values와 labels의 값을 별도로 입력하던것을 한번에 입력가능하도록 `lookupData`속성이 추가되었습니다.
```js
var lookupDatas = [
    {value:"001", label:"일"},
    {value:"002", label:"이"},
    {value:"003", label:"삼"}
];
gridView.setColumns([{
    name:"colName",
    fieldName:"fieldName",
    lookupData:{value:"value", label:"label", list:lookupDatas},
    // 또는 
    lookupData:lookupDatas,
    editor:{type:"dropdown"}
}])
```
  - value와 label에 해당하는 JSON객체의 name을 지정합니다.
  - value에 해당하는 JSON객체의 name이 "value" 또는 "code"이고 label에 해당하는 JSON객체의 name이 "label" 또는 "text"인 경우에는 "value"와 "label"속성을 생략하고 lookupData에 JSON 배열을 지정할수 있습니다.

1. [DynamicStyle](http://help.realgrid.com/api/types/DynamicStyle/)
  - dynamicStyles.criteria를 RealGrid의 판정식이 아닌 javascript function으로 사용할수 있도록 개선되었습니다.
  - 하나의 셀이 그려지기 직전에 호출되기 때문에 화면에 셀이 많고 function내에서 실행되는 코드가 느린경우 그리드의 실행속도도 느려지게 됩니다.
```js
gridView.setColumns([{
    name:"colName",
    fieldName:"fieldName",
    dynamicStyles:function(grid, index, value) {
        if (value === "1" || value === "2") {
            var gubun = grid.getValue(index.itemIndex, "gubunField");
            if (gubun === "A") {
                return {foreground:"#FFFF0000"}
            }
        }
    }
}]);
```
  - column.footer.dynamicStyles의 criteria를 function으로 지정하는 경우 index에 footerIndex가 추가됩니다.
  - 자세한 내용은 [데모]({{ '/GridStyle/DynamicStylesonColumns/' | prepend: site.baseurl }})를 참조하세요

1.  [IconRenderer](http://help.realgrid.com/api/types/IconCellRenderer/)
  - iconCellRenderer의 icon을 지정하는 styles.iconIndex에 url을 입력할수 있도록 개선되었습니다.
```js
gridView.setColumns([{
    name:"colName",
    fieldName:"fieldName",
    styles:{iconIndex:'./images/icon.png'},
    renderer:{type:"icon"}
}])
```
  - dynamicStyles를 이용하여 조건에 따라서 iconUrl을 변경할수 있습니다.
```js
var func = function(grid, index, value) {
    switch(value) {
    case "1" : return {iconIndex:"./images/case1.png"};
    case "2" : return {iconIndex:"./images/case2.png"};
    case "3" : return {iconIndex:"./images/case3.png"};
    ...
    }
};
gridView.setColumns([{
    name:"colName",
    fieldName:"fieldName",
    dynamicStyles:func,
    renderer:{type:"icon"}
}])
```

1. [RowGroupOptions](http://help.realgrid.com/api/types/RowGroupOptions/)
  - RowGroupOptions.headerCallback의 인자에 grid가 추가되었습니다.
```js  
  gridView.setRowGroup({headerCallback:function(groupModel, grid) { console.log(arguments) }});
```

1. `CSV Export`
  - Grid를 Excel csv파일로 export시 column의 정규식을 적용하여 export되도록 수정되었습니다.

1. [GridExportOptions](http://help.realgrid.com/api/types/GridExportOptions/)
  - `Text` 필드를 Excel로 Export시 수행되는 Callback함수가 추가 되었습니다.
```js
gridView.exportGrid({
    type:"excel",
    target:"local",
    textCallback: function(itemIndex, column, value) {
        return value;
    }
});
```
  - exportOptions.lookupDisplay가 true인경우 lookup이 적용된 text가 `value`로 전달됩니다.
  - column.displayRegExp가 설정되어 있는 경우 정규식이 적용된 text가 `value`로 전달됩니다.

1.  [MultiIconCellRenderer](http://help.realgrid.com/api/types/MultiIconCellRenderer/)
  - 셀에 여러개의 icon과 Text를 표시할수 있는 Renderer가 추가되었습니다.
```js
gridView.setColumns([{
    name:"colName",
    fieldName:"fieldName",
    renderer:{
      type:"multiIcon",
      renderCallback:function(grid, index, value) {
          var icons = [];
          if (value === "1") {
              icons.push('./images/icon1.png');
          };
          if (value === "2") {
              icons.push('./images/icon2.png');
          }
      }
    }
}])
```
  - 자세한 내용은 [데모]({{ '/Renderer/MultiIconCellRenderer/' | prepend: site.baseurl }})를 참조하세요
  
1. `TreeView Check`
  - TreeView의 Check가 Column Filtering시 해제되는 현상이 개선되었습니다.
  - TreeView를 정렬하거나 Filtering했을때 Checkable이 유지되지 않고 재 설정되는 현상을 수정하였습니다.

1.  [fitColumnWidth](http://demo.realgrid.com/Columns/GridFitting/)
  - TreeView의 첫번째 컬럼의 너비를 자동조정했을때 TreeExpander의 넓이가 계산되지 않는 현상이 개선되었습니다.

1. `TreeView의 개별행높이 지정`
  - treeView에서도 개별행높이를 변경할수 있도록 개선되었습니다.

1. [EditMask](http://help.realgrid.com/api/types/Mask/)
  - editMask가 설정된 셀편집기에 붙여넣기를 할때 복사된 문자열에 상관없이 editMask에 따라 붙여넣기가 되도록 개선되었습니다.

1. [fitRowHeight](http://help.realgrid.com/api/GridBase/fitRowHeight/)
  - gridView.fitRowHeight를 이용해서 row의 높이를 변경할때 IconRenderer를 사용하는 Column을 제외하고 높이가 계산되는 현상이 개선되었습니다.

1.  [fillCsvData](http://help.realgrid.com/api/LocalDataProvider/fillCsvData/)
  - csv의 data에 줄바꿈이 있는 경우에도 data를 정상적으로 가져오도록 수정되었습니다.

1.  [ExportGrid](http://help.realgrid.com/api/GridBase/exportGrid/)
  - DataType이 Number인 컬럼을 Excel로 Export할때 값이 없는 경우 공백문자가 출력되지 않도록 변경되었습니다.

1.  [ColumnFilter](http://help.realgrid.com/api/types/ColumnFilter/)
  - ColumnFilter의 criteria에 데이터행의 상태를 가지는 "state"변수가 추가되었습니다.

#### 오류 수정

1. [mask](http://help.realgrid.com/api/types/Mask/)
  - editor.mask에 placeHolder가 설정되고 includedFormat이 true일때 입력된 값이 placeHolder와 동일한경우 입력값이 사라지는 현상을 수정하였습니다.
  
1. [fitRowHeightAll](http://help.realgrid.com/api/GridBase/fitRowHeightAll/)
  - Grid에 컬럼을 설정하기 전에 gridView.fitRowHeightAll를 호출하는 경우 오류가 발생하는 현상을 수정하였습니다.

1. [RowGrouping]({{ '/RowGroup/RowGrouping/' | prepend: site.baseurl }})
  - RowGrouping 상태에서 dataProvider.removeRow(1)를 실행하여 row를 삭제하는 경우 간헐적으로 오류가 발행하는 현상을 수정하였습니다.

1. [ColumnGroup](http://help.realgrid.com/api/types/ColumnGroup/)
  - ColumnGroup에 포함되어있는 컬럼의 넓이를 마우스를 이용하여 변경할때 컬럼의 넓이가 0이하로 줄어들면 사라지는 현상을 수정하였습니다.

1. [PopupMenu](http://demo.realgrid.com/CellComponent/PopupMenu/)
  - popupMenu 또는 contextMenu가 열린상태에서 선택된 menuItem이 없는 상태에서 Enter또는 Space키를 입력하면 오류가 발생하는 현상을 수정하였습니다.

1. [ColumnHeader.tooltip](http://help.realgrid.com/api/types/ColumnHeader/)
  - column.header.tooltip의 높이가 그리드 영역보다 크고 row가 없는 경우 발행하는 오류를 수정하였습니다.

1. [LookupTree]({{ '/CellComponent/LookupTree/' | prepend: site.baseurl}})
  - LookupTree설정시 ordered가 true이고 LookupTree의 level이 3인경우 3level의 Label값이 중복되서 나오는 현상을 수정하였습니다.
  - ordered속성은 dropdown에 보여지는 값이 입력된 순서대로 보여지도록 하는 속성입니다.

1. `TreeView Filtering일때 insertChildRow`
  - TreeView가 Filtering상태일때 treeDataProvider.insertChildRow를 사용하여 row를 추가하는 경우 발생하는 오류를 수정하였습니다.
  - 추가된 Node가 Filtering에의해서 TreeView에서 보이지 않는 경우 발생하는 오류 입니다.

1. `column.header.text`
  - column.header.text가 문자가 아닌 숫자인 경우 화면에 표시되지 않는 현상을 수정하였습니다.
  - excel로 export할때 정상적으로 export되지 않는 오류를 수정하였습니다.

1.  [DataColumn](http://help.realgrid.com/api/types/DataColumn/)
  - Column의 셀을 병합할때 200행 이후의 셀들은 병합되지 않는 현상을 수정하였습니다.

1.  [CheckBar](http://help.realgrid.com/types/CheckBar/)
  - checkBar에 check를 한후 dataProvider.setRowCount를 실행하는 경우 check가 지워지는 현상을 수정하였습니다.

1.  [setColumn](http://help.realgrid.com/api/GridBase/setColumn/)
  - gridView.columnByName("colName")으로 가져온 column의 editor를 변경후 gridView.setColumn(colInfo)을 사용했을때 column의 editor가 변경되지 않는 오류를 수정하였습니다.

1.  [onCurrentChanging](http://help.realgrid.com/api/GridBase/onCurrentChanging/)
  - gridView.onCurrentChanging event에서 false를 return한후 그리드를 스크롤 했을때 선택영역이 사라지는 현상을 수정하였습니다.

## 1.1.27 (2018년 2월)

---

#### 기능 개선

1. `dataProvider Export`
  - dataProvider의 Data를 csv파일로 생성할수 있는 기능이 추가되었습니다.
  - dataProviderExportOptions
    target: "remote" | "local"
    url: remote를 이용해서 파일을 생성하는 경우 url을 지정합니다.  
    fileName: 저장하는 file명을 지정합니다.  
    start: 시작 dataRow를 지정합니다. (LocalTreeDataProvider의 경우 전체행만 가능)  
    count: export하려는 건수를 지정합니다.  
    lfText: data에 줄바꿈이 있는 경우 변경할 문자를 지정합니다.  
    crText: data에 줄바꿈이 있는 경우 변경할 문자를 지정합니다.  
    exportFields: export할 field를 배열로 지정합니다.  
    hideFileds: export하지 않을 field를 배열로 지정합니다.  
    includeFieldName: fieldName을 포함할것인지 지정합니다. default는 false입니다.  
  - exportFields가 지정된 경우 hideFields는 무시됩니다.  
```js
dataProvider.exportToCsv({
  target:"local",
  fileName:"dataProvider.csv",
  exportFields:['field1','field2','field3'],
  includeFieldNames:true
})
````
  - 자세한 내용은 [ExportToCsv](http://demo.realgrid.com/Excels/ExportToCsv/)데모를 참조하세요.

1. [TreeOptions](http://help.realgrid.com/api/types/TreeOptions/)
  - Expander가 표시되는 형태를 사용자의 이미지로도 표시할수 있도록 expandImage, collapseImage속성이 추가되었습니다.
```js
treeVeiw.setTreeOptions({
  expandImage:"./images/treeExpand.png", 
  collapseImage:"./images/collapseImage.png", 
  lineVisible:false
});
```

1. [CheckCellRenderer](http://help.realgrid.com/api/types/CheckCellRenderer/)
  - CheckCellRenderer의 shape속성이 `box`일때 테두리의 색상을 변경할수 있도록 수정되었습니다.
  - styles.line에 색상을 지정하여 checkBox의 색상을 변경할수 있습니다.
```js
gridView.setColumns([{
  fieldName:"fieldName", 
  name:"colName", 
  editable:false,
  renderer:{
      type:"check", 
      shape:"box", 
      editable:true
  },
  styles:{
      line:"#FF00FF00"
  }
}]);
```

1. [SparkLineRenderer]({{ '/Series/SparkLineRenderer/' | prepend: site.baseurl }})
  - SparkLineColumn이 있는 그리드를 Excel로 Export시 SparkLineColumn도 정상적으로 Export되도록 수정되었습니다.
  - GridExportOptions.exportSeriseColumn 속성이 추가되었습니다. true로 설정시 sparkLineColumn이 Excel로 export되며 false로 설정시 sparkLineColumn이 공백으로 export됩니다. 
    default는 false입니다.
  - `Excel2010`부터 사용가능한 기능이기 때문에 이전버전의 엑셀에서는 빈 컬럼으로 보여집니다.
```js
gridView.exportGrid({
  type:"excel",
  target:"local",
  exportSeriseColumn:true
})
```

1. [PasteOptions](http://help.realgrid.com/api/types/PasteOptions/)
  - Validation이 설정된 그리드에서 여러행을 붙여넣기시 Validation Error가 발생하는 경우 console에 표시되는 error를 표시하지 않도록 하는 `throwValidationError` 속성이 추가되었습니다.
  - 기본값은 true이며 false로 설정시 Validation Error가 발생하여도 console에 Error가 표시되지 않습니다.

1. [CheckBar](http://help.realgrid.com/api/types/CheckBar/)
  - checkBar에서 checkItem을 선택후 shift를 누른상태에서 다른 checkItem을 클릭하면 범위내에 있는 checkItem의 check상태가 처음선택된 checkItem의 선택되도록 수정되었습니다.

1. [GroupingOptions](http://help.realgrid.com/api/types/GroupingOptions/)
  - GroupPanel의 ColumnView 왼쪽에 표시되는 removeButton과 Text의 간격을 변경하는 `buttonGap`속성이 추가되었습니다.
```js
  gridView.setGroupingOptions({removeBotton:{visible:true, buttonGap:4}})
```
  - text가 ColumnView의 넓이보다 긴 경우에만 적용됩니다.

1. [HideRow](http://demo.realgrid.com/DataManager/hideRow/)
  - dataProvider의 dataRow를 그리드에서 표시하지 않도록 하는 기능이 추가되었습니다.
  - dataProvider.hideRows함수를 이용하여 특정 dataRow를 화면에 표시되지 않도록 하거나 dataProvider.showHiddenRows함수를 이용하여 다시 화면에 표시되도록 할수 있습니다.
  - dataProvider.getHiddenRows 또는 dataProvider.isHiddenRow함수를 이용하여 숨겨진 dataRow들을 확인할수 있습니다.
  - dataProvider.resetHiddenRows함수를 이용하여 hideRows를 초기화 할수 있습니다.
```js
/* dataRow를 숨길때 */
dataProvider.hideRows([0,1]);
/* dataRow를 다시 표시할때 */
dataProvider.showHiddenRows([0,1]);
/* 숨겨진 dataRow확인 */
dataProvider.getHiddenRows(); 
/* 숨겨진 dataRow확인 */
dataProvider.isHiddenRow(0);
/* 숨겨진 dataRow를 모두 다시 표시 */
dataProvider.resetHiddenRows();
```
  - options.sortMode:"explicit"인경우 또는 options.filterMode:"explicit"인경우에는 showDataRows를 실행하면 sort또는 filter가 실행됩니다.
  - 자세한 내용은 [HideRow](http://demo.realgrid.com/DataManager/hideRow/)데모를 참조하세요

1. [ExportGrid](http://help.realgrid.com/api/GridBase/exportGrid/)
  - 그리드를 Excel로 Export시 현재 행높이가 적용되도록 수정되었습니다.

1. [ToolTip]({{'/CellComponent/Tooltip/' | prepend: site.baseurl }})
  - 컬럼의 너비보다 Text의 길이가 긴 경우에만 tooltip이 표시되도록 하는 tooltipEllipseTextOnly 속성이 추가되었습니다.
```js
gridView.setColumns([{
  fieldName:"fieldName",
  name:"colName",
  renderer:{
      type:"text", 
      showTooltip:true, 
      tooltipEllipseTextOnly:true
  }
}]);
```

1. Styles.numberFormat
  - styles.numberFormat을 이용해서 소수를 표시할때 반올림하여 표시되는 것을 절사 또는 올림으로 표시할수 있도록 개선되었습니다.
  - "f": 지정된 소수점이하 자리를 절사, "c": 지정된 소수점이하 자리를 올림하여 표시합니다.
  - 실제 Data는 변경되지 않고 보여지는 값만 변경됩니다. 
```js
gridView.setColumns([
  {fieldName:"fieldNmae", name:"columnName", styles:{numberFormat:"#,##0.00;.;,;f"}}
  또는 
  {fieldName:"fieldName", name:"columnName", styles:{numberFormat:"#,##0.00;f"}}
])
```
1. 일부 브라우저에서 BackSpace입력시 이전페이지로 이동하는 현상을 개선하였습니다.
  - readOnly인 셀에서 backSpace를 입력시 IE 브라우저의 기본동작인 "이전페이지 이동"이 실행되지 않도록 변경되었습니다.

1. [ImageButtonsCellRenderer](http://help.realgrid.com/api/types/ImageButtonsCellRenderer/)
  - button을 위아래로 배치할수 있는 lineAlignment속성이 추가되었습니다.
  - button의 높이가 다르면서 lineAlignment가 far또는 near인경우 높이를 지정할수 있는 height속성이 추가되었습니다. 

```js
var imageButtons = [ {
  name:"팝업",
  up:"./image/popup_normal.png",
  hover:"./image/popup_hover.png",
  down:"./image/popup_click.png",
  cursor:"pointer",
  width:25
},{
  name:"조회",
  up:"./image/search_normal.png",
  hover:"./image/search_hover.png",
  down:"./image/search_click.png",
  width:25
}];

gridView.setColumns([{
  fieldName:"fieldName",
  name:"colName",
  renderer:{
    type:"imageButtons",
    images:imageButtons,
    height:20
  }
}]);
```

#### 오류 수정

1. [Footer](http://help.realgrid.com/api/types/Footer/)
  - 그리드 Footer의 셀을 merge할때 10개 이상의 컬럼이 merge되지 않는 현상을 수정하였습니다.

1. [ColumnGrouping]({{ '/Columns/ColumnGrouping/' | prepend: site.baseurl }})
  - ColumnGrouping상태에서 숨겨진 컬럼이 있는 경우 복사, 붙여넣기를 하면 숨겨진 컬럼까지 복사되거나 붙여넣기 되는 현상을 수정하였습니다.

1. [ColumnFooter](http://help.realgrid.com/api/types/ColumnFooter/)
  - ColumnFooter에 date가 표시되는 그리드를 excel로 export할때 발생하는 오류를 수정하였습니다.

1. [SeriesTextCellRenderer](http://help.realgrid.com/api/types/SeriesTextCellRenderer/)
  - 시리즈 컬럼에 값이 즉시 반영되지 않는 오류가 수정되었습니다.

1. [CheckBar]({{ '/GridComponent/CheckBar/' | prepend: site.baseurl }})
  - Paging되어있는 그리드에서 gridView.checkRow, gridView.checkRow로 CheckBar의 체크를 변경시 현재 페이지가 아닌 DataRow를 지정시 체크가 변경되지 않는 오류가 수정되었습니다.
  - 현재 페이지가 아닌 경우에도 gridView.isCheckedRow를 이용해서 체크여부를 가져올수 있도록 수정되었습니다.

1. [ExcelMultiExport](http://demo.realgrid.com/Excels/ExcelMultiExport/)
  - RealGridJS.exportGrid를 이용해서 여러개의 그리드를 excel로 export할때 lookupDisplay 속성을 true로 해도 적용되지 않는 현상이 수정되었습니다.

1. [RestoreMode](http://help.realgrid.com/api/types/RestoreMode/)
  - Tree그리드에서 restoreMode가 "explicit" 또는 "auto"인 상태에서 데이터를 변경후 restoreUpdatedRows를 이용해서 이전 값으로 복구하는 경우 자식행도 이전 값으로 복구되는 현상을 수정하였습니다.

1. `크롬브라우저에서 클릭시 스크롤 위치 오류`
  - 크롬브라우저에서 그리드의 `div`태그를 감싸고 있는 `div`가 여러개 중첩되어있고 overflow가 발생한 경우 그리드를 클릭하면 그리드의 스크롤 위치가 변경되는 현상이 개선되었습니다.

1. [DateCellEditor](http://help.realgrid.com/api/types/DateCellEditor/)
  - dateEditor에서 잘못된 날짜를 입력했을때 공백이 표시되지 않고 원하지 않는 날짜가 입력되는 현상을 수정하였습니다.


## 1.1.26 (2017년 11월)

---

#### 기능 개선
1. [contextMenu]({{ '/GridComponent/ContextMenu/' | prepend: site.baseurl }})
  - contextMenu 또는 PopupMenu의 item이 많은 경우 화면에 보여지는 item의 갯수를 변경할수 있도록 displayOptions.popupDropdownCount 속성이 추가 되었습니다.

1. [copyOptions](http://help.realgrid.com/api/types/CopyOptions/)
  - Ctrl+C를 이용해서 복사할때 화면에 보여지는 대로 복사할수 있는 copyOptions.copyDisplayText속성이 추가 되었습니다.

1. [CheckBar](http://help.realgrid.com/api/types/CheckBar/)
  - checkBar Cell의 styles을 동적으로 변경할수 있도록 dynamicStyles 속성이 추가 되었습니다.

1. [exportGrid](http://help.realgrid.com/api/GridBase/exportGrid/)
  - 여러개의 그리드를 excel로 Export할수 있도록 RealGridJS.exportGrid 함수가 추가되었습니다.
```js
RealGridJS.exportGrid({
  type:"excel",
  target:"local",
  fileName:"test.xlsx",
  showProgress:false,
  done: function() {
  },
  exportGrids:[
  {
      grid:grid1,
      sheetName:"test1"
  }, {
      grid:grid2,
      sheetName:"test2"
  }
  ]
})
```
  - [GridExportOptions](http://help.realgrid.com/api/types/GridExportOptions/)에 "sheetName" 속성이 추가되었습니다.
  - 자세한 내용은 [ExcelMultiExport]({{ '/Excels/ExcelMultiExport/' | prepend: site.baseurl }})를 참조하세요.

1. [BTDateCellEditor]({{ '/Editing/BTDateCellEditor/' | prepend: site.baseurl }})
  - [BootStrap DatePicker](https://bootstrap-datepicker.readthedocs.io/en/latest/)를 이용한 Editor가 추가되었습니다.
```js
<script type="text/javascript"  src="./scripts/bootstrap-datepicker.js"></script>
<script type="text/javascript"  src="./scripts/bootstrap-datepicker.ko.min.js"></script>
```
```js
var btOptions = {
    startView: 1,
    minViewMode: 1,
    todayBtn: "linked",
    todayHighlight: true,
    language:"ko",
}
```
```js
gridView.setColumns([
  { 
    name:"column1",
    fieldName:"field1",
    editor:{
        type:"btDate",
        btOptions:btOptions,
        datetimeFormat:"yyyy-MM-dd"
    }
  }
])
```

1. [getColumnProperty](http://help.realgrid.com/api/GridBase/getColumnProperty/)
  - getColumnProperty함수를 이용해서 column의 editor속성을 가져올수 있도록 개선되었습니다.
  - 기존함수와의 호환성을 위해서 "editorOptions"를 이용하여 editor의 속성을 가져올수 있습니다.
```js
  var editor = gridView.getColumnProperty("columnName", "editorOptions");
```
  - getColumns함수와 columnByName함수 등에서도 editorOptions속성으로 column Editor정보를 가져올수 있습니다.

1. [mask](http://help.realgrid.com/api/types/Mask/)
  - column Editor의 editMask를 "0000-00-00" 등과 같이 공백을 허용하지 않는 형식으로 지정했지만 data가 없는 경우 null로 처리하기 위해서 allowEmpty속성 추가
```js
gridView.setColumns([
{ 
  name:"columnName", fieldName:"fieldName",
  editor:{
      type:"date",
      mask:{editMask:"0000-00-00", allowEmpty:true}
  }
}
])
```

1. div element를 이용한 그리드 생성
  - div element의 id를 이용해서 그리드를 생성하는 것 외에 div element를 전달하여 그리드를 생성할수 있도록 개선되었습니다.
```js
var gridView, dataProvider;
window.onload = function() {
  var div = document.getElementById("divId");
  // 또는 
  var div = $("#bizPageName #gridView");
  div = div.length > 0 div[0] : null;
  if (div) {
    gridView = new RealGridJS.GridView(div);
  }
}
```

1. [buttonVisibility](http://help.realgrid.com/api/types/ButtonVisibility/)
  - button의 visible을 function의 결과값으로 변경할수 있도록 개선 되었습니다.
```js
gridView.setColumns([
{ 
  name:"columnName",
  field:"fieldName",
  button:"action",
  buttonVisibility:function(grid, index, focused, mouseEntered) {
      var value = grid.getValue(index.itemIndex, index.column);
      return value == "버튼" && (focused || mouseEntered)
  }
}])
```

1. [ColumnFooter](http://help.realgrid.com/api/types/ColumnFooter/)
  - ColumnFooter.callback함수의 인자에 grid가 추가되었습니다.
  - ColumnFooter.groupCallback함수의 인자에 grid와 groupModel이 추가 되었습니다.
```js
gridView.setColumns([
{ 
  name:"column",
  fieldName:"field",
  footer:{
      callback:function(column, footerIndex, grid) {
      },
      groupCallback:function(itemIndex, column, grid, groupModel) {
      }
  }
}
])
```

1. [SeriesColumn]({{ '/Series/SeriesColumn/' | prepend: site.baseurl }})
  - SeriesColumn에 표시되는 데이터의 구분자를 변경할수 있도록 valueSeparator 속성이 추가되었습니다.
```js
gridView.setColumns([
{ 
  name:"colSeries",
  fieldNames:"field1,field2,field3,field4",
  renderer:{
      type:"seriesText",
      valueSeparator:"~"
  } 
}])
```

1. [getCheckedRows](http://help.realgrid.com/api/GridView/getCheckedRows/)
  - [paging](http://help.realgrid.com/api/features/Paging/)어 있는 그리드에서 현재 보여지고 있는 페이지 아닌 다른 페이지에 있는 Item이 체크되어있는 경우 체크되어있는 전체 dataRow를 가져올수 있도록 allRows인자가 추가되었습니다.

1. [onColumnHeaderClicked](http://help.realgrid.com/api/GridBase/onColumnHeaderClicked/)
  - 컬럼 헤더를 클릭했을때 마우스 좌, 우 클릭을 구분할수 있도록 onColumnHeaderClicked함수의 인자로 rightClicked가 추가 되었습니다.

1. [DateCellEditor](http://help.realgrid.com/api/types/DateCellEditor/)
  - dateEditor에 년주차를 표시할수 있도록 showWeeks 속성이 추가되었습니다.
  - 년주차를 선택할수 있는 weekSelectable속성이 추가되었습니다.
  - dateEditor에서 시작 요일을 변경할수 있는 startWeek 속성이 추가되었습니다.
```js
dataProvider.setFields([
  {name:"text", dataType:"text"}
]);
gridView.setColumns([
{ 
  name:"column",
  fieldName:"text",
  editor:{
      type:"date",
      showWeeks:true,
      weekSelectable:true
  }
}
]);
```
  - dataType이 "date"인 컬럼의 경우 weekSelectable을 true로하여도 년주차를 선택할수 없습니다.
  - dataType이 "text"이고 editor의 weekSelectable이 true인경우 년주차 또는 일자를 선택하면 "201742"와 같은 형태로 선택값이 return됩니다.
  - CSS를 이용하는 경우 년주차Cell의 style을 변경할수 있도록 "rg-cal-year-weeks" class가 추가 되었습니다.

1. [searchCell](http://help.realgrid.com/api/GridBase/searchCell/)
  - field의 순서와 컬럼의 순서가 다르거나 하나의 필드가 여러개의 컬럼에 연결된 경우 지정된 컬럼의 순서대로 cell을 검색할수 있도록 [SearchOptions](http://help.realgrid.com/api/types/SearchOptions/)에 columns가 추가되었습니다.
  - option에 fields가 있는 경우 columns는 무시됩니다.
```js
  var columns = gridView.getColumnNames(true,true,true);
  var current = gridView.getCurrent();
  var startFieldIndex = columns.indexOf(current.column)+1;
  var startItemIndex = current.itemIndex;
  var value = "검색조건";
  gridView.searchCell({columns:columns, value:value, startItemIndex:startItemIndex, startFieldIndex:startFieldIndex});
```

1. [exportGrid](http://help.realgrid.com/api/GridBase/exportGrid/)
  - gridView의 data를 csv파일로 내보낼수 있는 기능이 추가되었습니다.
```js
  gridView.exportGrid({type:"csv", target:"local", fileName:"test.csv"});
```
  - csv파일로 export할때 columnGroup은 해제되어 표시됩니다.
  - "remote"를 이용하는 경우 response header의 "Context-Type"을 "text/csv"로 변경하여야 합니다.

1. [ImageButtonsCellRenderer](http://help.realgrid.com/api/types/ImageButtonsCellRenderer/)
  - imageButtonsCellRenderer가 표시하는 버튼의 위치를 변경할수 있도록 alignment속성이 추가되었습니다.
  - button별로 cursor를 변경할수 있도록 cursor속성이 추가되었습니다.
```js
  var imageButtons = [
    { name:"조회",
      up:"./image/search_normal.png",
      hover:"./image/search_hover.png",
      down:"./image/search_click.png",
      cursor:"pointer",
      width:45
    }
  ];
  gridView.setColumns([
    { name:"column",
      fieldName:"fieldName",
      renderer:{type:"imageButtons", editable:false, alignment:"center"}
    }
  ])
```
  - alignment가 "near"또는 "center"인경우는 editor를 사용할수 없습니다.

1. [DataColumn](http://help.realgrid.com/api/types/DataColumn/)
  - column button의 cursor를 변경할수 있도록 buttonCursor 속성이 추가되었습니다.
```js
  gridView.setColumns([
    { name:"column",
      fieldName:"fieldName",
      button:"action",
      buttonCursor:"pointer"
    }
  ])
```

1. [getColumnNames](http://help.realgrid.com/api/GridBase/getColumnNames/)
  - 화면에 보이는 컬럼만 가져오도록 하는 visibleOnly인자가 추가되었습니다.
  - 사용자가 컬럼의 순서를 변경한 경우 화면에 보이는 순서대로 컬럼명을 가져올수 있도록 ordered인자가 추가 되었습니다.

1. [PasteOptions](http://help.realgrid.com/api/types/PasteOptions/)
  - 대량데이터를 붙여넣기 할때 gridView가 refresh되면서 시간이 오래 걸리는 현상을 개선하기 위해서 noDataEvent속성이 추가 되었습니다.
  - pasteOptions.noDataEvent를 true로 설정하고 여러줄의 Data를 붙여넣기 하는 경우 붙여넣기를 하는 중에는 refresh되지 않습니다.

1. [NumberCellEditor](http://help.realgrid.com/api/types/NumberCellEditor/)
  - numberCellEditoir에서 정수부의 최대길이를 지정할수 있는 maxIntegerLength 속성이 추가되었습니다.
```js
gridView.setColumns([
{ 
    name:"column",
    fieldName:"field",
    editor:{  
          type:"number",
          editFormat:"#,##0.00",
          maxIntegerLength:5
    }
}
]);
```

#### 오류 수정 
1. [HeaderSummary](http://help.realgrid.com/api/types/HeaderSummary/)
  - headerSummary의 속성을 설정하는 순서에 따라 일부 속성이 적용되지 않는 오류를 수정하였습니다.
```js
  gridView.setHeader({
    summary:{
      visible:true,
      mergeCells:["column1","column2","column3"],
      styles:{background:"#40c0c000"}
    }
  })
```

1. [DateCellEditor](http://help.realgrid.com/api/types/DateCellEditor/)
  - dataType이 "text"인 column의 editor가 dateEditor이면서 mask가 설정되어있을때 정상적으로 입력되지 않는 오류를 수정하였습니다.
```js
  gridView.setColumns([
    { name:"column",
      fieldName:"textField",
      editor:{
        type:"date",
        mask:{
          editMask:"9999-99-99"
        },
        datetimeFormat:"yyyyMMdd"
      }
    }
  ])
```

1. [CheckCellRenderer](http://help.realgrid.com/api/types/CheckCellRenderer/)
  - 하나의 셀을 선택후 shift키를 누른상태에서 checkCellRenderer를 가지는 컬럼의 셀을 마우스로 클릭하는 이전에 선택된 셀의 값이 변경되는 현상을 수정하였습니다.

1. [SaveColumnLayout](http://help.realgrid.com/api/GridBase/saveColumnLayout/)
  - 첫번째 컬럼이 숨겨져있을때 컬럼의 위치를 이동하고 saveColumnLayout함수를 이용하여 column정보를 가져오면 컬럼의 순서가 달라지는 현상을 수정하였습니다.

1. 모바일그리드 
  - 모바일 그리드에서 마지막 행이 표시될때 스크롤 하면 페이지가 스크롤 되도록 개선되었습니다.

1. [Cell Editor](http://help.realgrid.com/api/features/Cell%20Editor/)
  - Chrome Brower에서 searchEditor가 활성화 된 상태에서 엔터키 입력시 onEditSearch 이벤트의 text인자에 비정상적인 값이 넘어오는 현상을 수정하였습니다.

1. [DataColumn](http://help.realgrid.com/api/types/DataColumn/)
  - [displayOptions](http://help.realgrid.com/api/types/DisplayOptions/).hintDuration이 설정된 상태에서 column.cursor를 지정하여 컬럼별로 커서를 변경하는 경우 hintDuration만큼 지연되어 변경되는 현상을 수정하였습니다.

1. [ColumnFooter](http://help.realgrid.com/api/types/ColumnFooter/)
  - rowGrouping상태이면서 rowGroup이 접혀져 있는 그리드를 엑셀로 export시 footer.groupCallback 함수의 footerIndex가 -1로 전달되어 footer를 찾지못하는 현상이 있습니다.
  - footer의 GroupModel을 groupCallback의 인자로 추가 하여 group의 값을 참조할수 있도록 수정하였습니다.

## 1.1.25 (2017년 8월)

---

#### 기능 개선
1. [searchCell](http://help.realgrid.com/api/GridBase/searchCell/)  
  - gridView.searchCell을 이용해서 date형식의 자료를 찾을 때 일부만 입력하여 검색가능하도록 개선되었습니다.
  - 구분자는 ".", "-", "/"를 사용할 수 있으며 구분자 없이 "201708"형태로도 검색 가능합니다.
```js
  gridView.serachCell({fields:["dateField1", "dateField2"], value:"2017-08", partialMatch:true})
```

1. [NumberCellEditor](http://help.realgrid.com/api/types/NumberCellEditor/)
  - numberCellEditor에서 숫자 중간에 입력하는 경우 caret이 끝으로 이동하지 않도록 개선되었습니다.

1. [clearInvalidCellList](http://help.realgrid.com/api/GridBase/clearInvalidCellList/)
  - validation이 실패한 셀의 목록을 초기화 할 수 있는 clearInvalidCellList함수가 추가되었습니다.

1. [ColumnHeader](http://help.realgrid.com/api/types/ColumnHeader/)
  - ColumnHeader의 image를 클릭 시 발생하는 onColumnHeaderImageClicked 이벤트가 추가되었습니다.

1. [onBodyEmptyClicked](http://help.realgrid.com/api/GridBase/onBodyEmptyClicked/)
  - 그리드의 빈 영역을 클릭했을 때 발생하는 onBodyEmptyClicked 이벤트와 onBodyEmptyDblClicked이벤트가 추가되었습니다.

1. [DynamicStyle](http://help.realgrid.com/api/types/DynamicStyle/)
  - 변경된 cell의 style을 변경할 수 있도록 [Expression](http://help.realgrid.com/api/features/Expression/)에 "changedcell" 조건이 추가되었습니다.
  - changedcell조건을 사용하기 위해서는 DataProvider.restoreMode속성이 "explicit"이거나 또는 "auto"이어야 합니다.
```js
dataProvider.setOptions({restoreMode:"explicit"});
gridView.setStyles({
    body:{
      cellDynamicStyles:[{criteria:"changedcell", styles:{figureName:"leftTop", figureBackground:"#FF00ebeb", figureSize:"20%"}}];
    }
});
```
  - Column별로 style을 변경하는 경우 column.dynamicStyles를 이용합니다.
```js
  gridView.setColumnProperty("columnName", "dynamicStyles", [{criteria:"changedcell", styles:{figureName:"leftTop", figureBackground:"#FF00ebeb", figureSize:"20%"}}]);
```
  - 자세한 내용은 [DynamicStylesonColumns]({{ '/GridStyle/DynamicStylesonColumns/' | prepend: site.baseurl }})데모를 참조하세요.

1. [GridExportOptions](http://help.realgrid.com/api/types/GridExportOptions/)
  - 그리드를 Excel로 Export할 때 checkBar에 체크된 행만 Export할수 있도록 `GridExportOptions.onlyCheckedItems` 속성이 추가되었습니다.
  - 그리드가 RowGrouping상태이거나 TreeGrid의 경우에는 적용되지 않습니다.
  - Column.Header.subText가 있는 경우 subText도 출력되도록 수정되었습니다. (subTextStyle의 경우는 적용되지 않습니다)

1. [GridView.collapseAll](http://help.realgrid.com/api/GridView/collapseAll/)
  - 그리드가 rowGrouping상태일때 모든 Group을 접도록 하는 collapseAll 함수가 추가되었습니다.
```js
  gridView.collapseAll(true);
```
  - 특정 Level까지의 Group을 펼치도록 하는 expandAll함수가 추가되었습니다.
```js
  var fieldName = gridView.getCurrent().fieldName;
  var level = gridView.getGroupFieldNames().indexOf(fieldName.toUpperCase());
  level >= 0 && gridView.expandAll(level+1);
```

1. [DataColumn](http://help.realgrid.com/api/types/DataColumn/)
  - DataColumn.equalBlank가 true이고 셀이 merge된 상태에서 세로스크롤시 텍스트가 사라지지 않고 계속 표시되도록 수정되었습니다.

1. `Mobile Edit`
  - MobileGrid에서도 제한적인 편집이 가능하도록 수정되었습니다.
  - MobileGrid의 setEditOptions.editable의 Default값은 false입니다.(true설정 시 Mobile편집 가능)
  - cell을 doubleTouch하면 편집상태로 변경이 됩니다.
  - dropdownEditor, dateEditor의 경우 cell을 선택후 editButton을 touch하면 편집상태로 변경됩니다.

1. [DisplayOptions](http://help.realgrid.com/api/types/DisplayOptions/)
  - DisplayOptions.rowFocusOption 속성이 추가되었습니다.
```js
gridView.setDisplayOptions({
    rowFocusOption:{
      visible:true,
      rowFocusMask:"row",
      styles:{
            background:"11008484",
            border:"#441212Fb,2"
      }
    }
});
```
  - 이전버전의 `DisplayOptions.rowFocusVisible`, `DisplayOptions.rowFocusMask`, `DisplayOptions.rowFocusBackground`를 대체하는 속성입니다.

1. [DisplayOptions](http://help.realgrid.com/api/types/DisplayOptions/)
  - progressView의 스타일을 사용자가 지정할수 있도록 DisplayOptions.useCssStyleProgress 속성이 추가되었습니다.
  - progressView가 생성되기전에 useCssStyleProgress를 true로 설정해야 적용됩니다.
```js
  gridView.setDisplayOptions({useCssStyleProgress:true});
  gridView.showProgress();
  gridView.setProgress(min, max, position, "progress Message");
```
- 자세한 내용은 [CSSStyles]({{ '/GridStyle/CSSStyles/' | prepend: site.baseurl }})데모를 참조하세요.

1. [onGridActivated](http://help.realgrid.com/api/GridBase/onGridActivated)
  - 그리드를 클릭하거나 gridView.setFocus()를 이용하여 그리드에 포커스를 이동시키면 발생하는 onGridActivated 이벤트가 추가되었습니다.
```js
gridView.onGridActivated = function(grid) {
    window.activeGrid = grid;
}
```
  - RealGridJS.getActiveGrid 함수가 추가되었습니다. 화면에 여러개의 그리드가 있는 경우 마지막으로 포커스를 가진 그리드를 반환합니다.
  - div tag를 이용해서 tab화면을 구성한 경우 tab을 변경하여도 그리드가 focus를 가지기 전까지는 이벤트가 발생하지 않습니다.

1. [ImageButtonsCellRenderer](http://help.realgrid.com/api/types/ImageButtonsCellRenderer/)가 추가되었습니다.
  - 조건에 따라 서로다른 이미지 버튼을 보여줄수 있는 ImageButtonosCellRenderer가 추가되었습니다.
```js
var imageButtons1 = [{
    name:"zoomin",
    up:"./image/zoomin.png",
    width:16
}];
var imageButtons2 = [{
    name:"zoomout",
    up:"./image/zoomout.png",
    width:16
}];
gridView.addCellRenderers([{
        "id":"buttons1",
        "type":"imageButtons",
        "images": imageButtons1
    },{
        "id":"buttons2",
        "type":"imageButtons",
        "images": imageButtons2
}]);
gridView.setColumns([{
    name:"column1",
    fieldName:"field1",
    dynamicStyles:[{
         criteria:["value = 'A'", "value = 'B'"],
         styles:["renderer=buttons1", "renderer=buttons2"]
    }]
}]);
```
자세한 내용은 [셀 버튼]({{ '/CellComponent/CellButton/' | prepend: site.baseurl }})데모를 참조하세요.

1. [DataProvider.searchData](http://help.realgrid.com/api/LocalDataProvider/searchData/)
  - gridView.searchItem과 유사한 역활을 하는 dataProvider.searchDataRow함수가 추가되었습니다.  
  - gridView.searchCell과 유사한 역활을 하는 dataProvider.serachData함수가 추가되었습니다.  
  자세한 내용은 [트리뷰 노드 검색하기]({{ '/Tree/TreeSearchRow/' | prepend: site.baseurl }})데모를 참조하세요. 

1. [GroupingOptions](http://help.realgrid.com/api/types/GroupingOptions/)
  - rowGroup을 해제할수 있는 removeButton 속성이 추가되었습니다.
```js
gridView.setGroupingOptions({
    removeButton:{
      visible:true,
      color:"#FF00FFF0",
      hoveredColor:"#FFFF000F",
      size:12
    }
});
```
  - removeButton.visible이 true인 경우 groupPanel의 ColumnView의 오른쪽에 "X"표시가 생성되며 클릭시 해당 column은 rowGroup에서 제외됩니다.

1. [ColumnHeader](http://help.realgrid.com/api/types/ColumnHeader/)
  - column의 Header에 popupButton이 추가되었습니다.
  - popupMenu를 그리드에 추가한후 popupMenu명을 Column.Header.popup에 등록한후 사용할수 있습니다.
  - Column.Header.popup을 직접 정의하여 사용할수 있습니다.
```js
var menu = [{
    label: "menu1 입니다.",
    enabled: true,
    children: [{
         label: "submenu1 입니다.",
         callback:function(grid, index){console.log(index)}
    }, {
         label: "submenu2 입니다."
    }]
    }, {
         label: "menu2 입니다",
         enabled: false
}];
gridView.addPopupMenu("menu1", menu);
gridView.setColumns([{
    name:"column1", fieldName:"fieldName1",
    header:{
         popupMenu:"menu1"
    }
},{
    name:"column2", fieldName:"fieldName2",
    header:{
         popupMenu:[{label:"popupMenu", callback:function(grid, index){console.log("test")}}]
    }
}]);
```
  - [ColumnHeaderOptions](http://help.realgrid.com/api/types/ColumnHeaderOptions/)에 popupMenu관련 속성이 추가되었습니다.
  - popupMenuColor: popupMenuButton의 색상을 입력합니다.
  - hoveredPopupMenuColor: MouseOver시 popupMenuButton의 색상을 입력합니다.
  - popupMenuWidth: popupMenuButton의 넓이를 입력합니다.
```js
gridView.setColumnHeaderOptions({
    popupMenuWidth:12,
    popupMenuColor:"#ff696969",
    hoveredPopupMenuColor:"#FFFF0000"
});
```


#### 오류 수정
1. `searchCell`
  - gridView.searchCell을 이용해서 찾기 시 "undefined"를 찾으면 value가 undefined인 cell이 검색되는 현상을 수정하였습니다.

1. `checkBar`
  - checkBar의 check를 클릭하였을 때 그리드가 스크롤 되는 현상을 수정하였습니다.

1. `dataProvider.getUpdatedCells`
  - [dataProvider.getUpdatedCells](http://help.realgrid.com/api/DataProvider/getUpdatedCells/)를 이용해서 수정된 cell을 가져올 때 수정된 행을 모두 가져오지 못하는 오류를 수정하였습니다.

1. `gridExport.documentTitle`
  - 1.1.24버전에서 gridExport.documentTitle.spaceTop을 설정했을 때 발생하는 오류를 수정하였습니다.

1. `selectOptionis.style`
  - selectOptions.style이 "rows"일 때 아래쪽에서 위로 범위 설정 후 마우스 우클릭 시 범위 설정이 해제되는 오류를 수정하였습니다.

1. `displayOptions.rowHeight`
  - displayOptions.rowHeight의 값을 잘못된 값으로 설정 시 그리드가 깨지는 오류를 수정하였습니다.

1. `Mobile TreeGrid`
  - Mobile TreeGrid에서 화면 touch를 이용해서 스크롤 할 때 이동되지 않는 오류를 수정하였습니다.

1. `GridExport`
  - DataField의 DataType이 number이고 Column.styles.numberFormat이 `"#,##0;,;."`인 컬럼을 Excel로 Export하는 경우 음수인 Data가 Excel에서 정상적으로 보이지 않는 오류를 수정하였습니다.

1. `DataField.defaultValue`
  - DataField.defaultValue가 설정되어있어도 insert 또는 append시 적용되지 않는 오류가 수정되었습니다.

1. `paste`
  - 편집 불가 상태의 cell에 열 단위 붙여넣기를 했을 때 붙여넣기가 되지 않는 현상을 수정하였습니다.

1. `onCurrentChanged`
  - 그리드가 포커스를 가지고 있지 않은 상태에서 그리드의 (0,0) cell이 아닌 다른 cell을 클릭시 onCurrentChanged이벤트가 2번 발생하는 현상을 수정하였습니다.

1. `showSortOrder`
  - sortOrder가 간혹 사라지는 현상이 수정되었습니다.

1. `onHideEditor`
  - onHideEditor 이벤트가 발생하는 않는 오류를 수정하였습니다.

1. [ActualTargetBulletRenderer](http://help.realgrid.com/api/types/ActualTargetBulletRenderer/)
  - actualTargetBulletRenderer의 dynamicStyles가 적용되지 않는 오류가 수정되었습니다. 


## 1.1.24 (2017년 6월)

---

#### 기능 개선 
1. `MergedRowGroup의 Footer 상단표시`
  - `MergedRowGroup` 상태에서 Footer를 그룹의 상단에 표시할수 있도록 개선되었습니다.  
  - 자세한 내용은 [MergedRowGrouping]({{ '/RowGroup/MergedRowGrouping/' | prepend: site.baseurl }}) 데모를 참조하세요.  

1. [DataColumn](http://help.realgrid.com/api/types/DataColumn/)  
  - DataType이 Number인 컬럼의 값이 0 인경우 다른 문자로 표시할수 있도록 zeroText 속성이 추가되었습니다.  
  - 사용자가 컬럼의 넓이를 변경할때 최소넓이와 최대넓이를 지정할수 있도록 minWidth, maxWidth 속성이 추가되었습니다.   

1. [DisplayOptions](http://help.realgrid.com/api/types/DisplayOptions/)  
  - 데이터가 없는 셀에서도 Tooltip이 표시될 수 있도록 displayOptions.emptyShowTooltip 속성이 추가되었습니다.  
  - DisplayOptions.emptyShowTooltip을 true로 설정하면 데이터가 없는 셀에서도 [onShowToolip](http://help.realgrid.com/api/GridBase/onShowTooltip/) 이벤트가 발생되며 이벤트에서 리턴된 문자열을 tooltip으로 표시합니다.

1. [ExportOptions](http://help.realgrid.com/api/types/GridExportOptions/)
  - Export시 visible이 false인 컬럼도 표시될수 있도록 allColumns속성이 추가되었습니다.
```js
grid.exportGrid({
  type:"excel",
  target:"local",
  allColumns:true
});
```
1. [DateCellEditor](http://help.realgrid.com/api/types/DateCellEditor/)에서 선택가능한 범위지정.
  - DateCellEditor에서 minDate, maxDate를 지정하여 특정기간만 선택가능하도록 개선되었습니다.
```js
grid.setColumns([{ 
    fieldName:"date",
    name:"date",
    editor:{
      type:"date",
      minDate:new Date(2017, 05, 1), 
      maxDate:new Date(2017, 05, 30) //"2017-08-31"와 같이 문자열로도 지정가능.
    }
}])
```
  자세한 내용은 [Editors]({{ '/Editing/Editors/' | prepend: site.baseurl }})를 참조하세요.

1. `Editor TextAlignment`
  - editor의 textAlignment 를 변경할수 있도록 개선되었습니다.
```js
grid.setColumns([{ 
    fieldName:"text",
    name:"text",
    editor:{
      type:"text",
      textAlignment:"far"
    }
}])
```
  자세한 내용은 [Editors]({{ '/Editing/Editors/' | prepend: site.baseurl }})를 참조하세요.  

1. [BarCellRenderer](http://help.realgrid.com/api/types/BarCellRenderer/)
  - BarCellRenderer와 [SignalBarCellRenderer](http://help.realgrid.com/api/types/SignalBarCellRenderer/)에서 Value가 음수인경우 절대값으로 표시되도록 하는 absoluteValue 속성이 추가되었습니다.

1. [MultiCheckCellEditor](http://help.realgrid.com/api/types/MultiCheckCellEditor/)
  - MultiCheckCellEditor에서 전체 선택,해제 CheckBox를 표시하는 showAllCheck 속성이 추가되었습니다.
```js
grid.setColumns([{ 
  fieldName:"text",
  name:"text",
  editor:{
    type:"multiCheck",
    showAllCheck:true,
    allCheckText:"전체선택"
  }
}])
```
  자세한 내용은 [데모]({{ '/Editing/MultiCheckCellEditor/' | prepend: site.baseurl }})를 참조하세요.

1. `Column Move`
  - Column Header를 Drag하여 Column의 위치를 변경할때 그리드 영역을 벗어나면 가로스크롤이 되어 표시되지 않는 영역으로 이동할 수 있도록 개선되었습니다.

1. `Footer`
  - footer가 여러행인경우 각 행별로 스타일을 적용할수 있도록 개선되었습니다.
  - Footer.styles를 지정할때 array로 스타일을 지정하면 각 Footer별로 스타일이 지정됩니다.
  ```js
    grid.setFooter({styles:[{background:"#8800ee00"},{background:"#8800eeee"}]})
  ```
  자세한 내용은 [데모]({{ '/HeaderAndFooter/MultiFooter/' | prepend: site.baseurl }})를 참조하세요.

1. `DisplayOptions`
  - 사용자가 마우스를 움직일때 마우스 위치에 해당하는 DataRow를 보여줄수 있도록 [rowHoverMask](http://help.realgrid.com/api/types/RowHoverMask/)속성이 추가되었습니다.
```js 
grid.setDisplayOptions({
    rowHoverMask:{
        visible:true,
        styles:{
            background:"#2065686b"
        },
        hoverMask:"row"
    }
})
```
  자세한 내용은 [데모]({{ '/GridComponent/Selecting/' | prepend: site.baseurl }})를 참조하세요.

#### 오류 수정
1. `dataProvider.getFields`
  - dataProvider.getFields함수를 이용해서 field의 속성을 가져올때 orgFieldName속성이 누락되는 현상을 수정하였습니다.

1. `gridView.onEditRowChanged`
  - gridView.onEditRowChanged이벤트 사용시 키보드 도는 마우스로 행을 변경하면 이벤트가 2번 발생되는 현상이 수정되었습니다.

1. `gridView.setValues`
  - dataProvider.setRowCount등을 이용해서 빈행을 생성후 gridView.setValues를 이용해서 값을 입력할때 발생하는 오류를 수정하였습니다.

1. `gridView.getColumns`
  - gridView.getColumns를 이용해서 컬럼 정보를 가져올때 header, footer 속성이 포함되도록 수정되었습니다.

1. `gridView.getDisplayOptions`
  - 그리드 행높이가 기본일때 gridView.getDisplayOptions().rowHeight가 0으로 나오는 현상을 수정하였습니다.

1. `gridView.collapseParent`
  - RowGroup.expandedAdornments가 "summary"인 상태에서 gridView.collapseParent(itemIndex, true)를 호출하여 item을 접을때 하위 item이 접히지 않는 현상이 수정되었습니다.

1. `gridView.setColumnLayout`
  - gridView.saveColumnLayout()을 이용해서 현재 Column상태를 저장한후 gridView.setColumnLayout을 이용해서 Column상태를 되돌릴때 ColumnGroup의 하위 column의 넓이가 변경되는 현상이 수정되었습니다.

1. `columnHeader`
  - 그리드에 GroupPanel영역이 없을때 Column.Header의 Hovering색상이 유지되는 현상이 수정되었습니다.

1. `MultiCheckCellEditor`
  - MultiCheckCellEditor의 속성중 domainOnly를 true로 했을때 값을 선택할수 없는 현상이 수정되었습니다.

1. `ColumnGroup`
  - ColumnGroup.orientation이 Vertical이면서 visible이 false인 하위 컬럼이 있는 경우 정상적으로 표시되지 않는 현상을 수정하였습니다.

1. `FixedOptions.movable`
  - FixedOptions.movable이 true일때 고정되지 않은 컬럼을 고정영역으로 옮길수 없는 현상을 수정하였습니다.

## 1.1.23 (2017년 4월)

---

#### 기능 개선 
1. [TextWrap](http://help.realgrid.com/api/types/TextWrap/)
  - ellipse속성이 추가되었습니다.
  - column.styles.textWrap를 "ellipse"로 지정시 Data의 길이가 column의 넓이보다 긴 경우 보이지 않는 Data를 "..."으로 표시합니다.
1. [getColumnProperty](http://help.realgrid.com/api/GridBase/getColumnProperty/)
  - columnByName 또는 getColumnProperty에서 styles 속성과 dynamicStyles 속성을 가져오도록 개선되었습니다.
  - Column.styles에 정의된 속성만 가져오기를 원하는 grid.getColumnProperty(column, "styles", false)를 이용하면 Column.styles에 정의된 속성만 가져옵니다.
  - getColumnProperty를 이용해서 Column.editorOptions속성을 가져올수 있도록 개선되었습니다.
1. [PasteOptions](http://help.realgrid.com/api/types/PasteOptions/)
  - 하나의 셀을 복사후 여러개의 셀에 붙여넣기 할수 있도록 PasteOptions.selectBlockPaste이 추가되었습니다.
  - SelectOptions.sytle이 "block"인 경우만 적용됩니다.
  ```js
    grid.setPasteOptions({
      selectBlockPaste:true
    })
  ```
  - Column.Editor의 type이 "number"이면서 editFormat이 있거나 또는 styles.numberFormat이 있는 경우 소수점 자릿수를 제한할수 있도록 PasteOptions.applyNumberFormat이 추가되었습니다.
  ```js
    grid.setPasteOptions({
      applyNumberFormat:true
    }) 
  ```
1. [Field](http://help.realgrid.com/api/types/DataField/).calculateExpression에서 다른 계산필드를 참조할수 있도록 개선
  - 계산필드에서 다른 계산필드를 참조할수 있도록 개선되었습니다(선행필드만 참조가능합니다). 
1. Shift+Click 기능이 추가
  - Shift+Click을 이용하여 selection을 변경할수 있도록 개선되었습니다.
1. Column의 Header오른쪽을 더블클릭하여 Column의 넓이를 변경 개선
  - Column의 넓이를 계산할 때 Column.header의 text와 Column.footer의 text를 포함하여 계산하도록 개선되었습니다.
1. DataCell의 귀퉁이에 작은 삼각형의 표시할수 있도록 edgeMark 추가
  - styles.figureName에 "leftTop", "leftBottom", "rightTop", "rightBottom" 중에 하나를 지정하면 해당위치에 작은 삼각형이 표시됩니다. 
  - 자세한 내용은 [데모](http://demo.realgrid.com/CellComponent/EdgeMark/)와 [Help](http://help.realgrid.com/api/types/EdgeMark/)를 참조하세요.
1. [stateBar](http://help.realgrid.com/api/types/StateBar/)의 상태별 색상 변경
  - 행들의 상태를 표시하는 stateBar의 배경색을 상태에 따라 색상을 변경할수 있도록 updatedStyles, createdStyles, deletedStyles, createAndDeletedStyles 속성이 추가되었습니다.
  - 자세한 내용은 [데모](http://demo.realgrid.com/GridComponent/StateBar/)를 참조하세요.
1. [ExportOptions](http://help.realgrid.com/api/types/GridExportOptions/)
  - Export시 전체 data를 출력할수 있는 pagingAllItems 옵션이 추가되었습니다.
```js
  grid.export({
    type:"excel",
    target:"local",
    pagingAllItems:true
  });
```  
1. [CellButton.image](http://help.realgrid.com/api/types/CellButton/)
  - 하나의 셀에 여러개의 버튼이 표시될때 각 버튼의 넓이와 버튼간격을 지정할수 있도록 개선되었습니다.
  - imageGap속성으로 이미지의 간격을 지정하고 margin속성은 마지막 이미지와 Cell의 오른쪽 경계의 간격을 지정합니다.
```js
  var imageButtons = [ {
      name:"팝업",
      up:"./image/popup_normal.png",
      hover:"./image/popup_hover.png",
      down:"./image/popup_click.png",
      width:20  // 버튼별로 넓이를 지정.
    },{
      name:"조회",
      up:"./image/search_normal.png",
      hover:"./image/search_hover.png",
      down:"./image/search_click.png",
      width:30  // 버튼별로 넓이를 지정.
    }];  
  grid.setColumns([
    {fieldName:"fieldName", name:"columnName",button:"image", imageButtons:{images:imageButtons, margin:3, imageGap:2}}
  ])
```
  - [셀버튼]({{ '/CellComponent/CellButton/' | prepend: site.baseurl }})페이지에서 데모를 참조하세요.

#### 오류 수정
1. `getStyles`
  - gridView.getStyles("all")을 호출했을때 발생하는 오류를 수정하였습니다.
1. `rowGrouping상태일때 ColumnGroup의 rowGroup.footer`
  - rowGrouping상태일때 ColumnGroup의 rowGroup.footer의 높이가 달라지는 현상을 수정하였습니다.
1. `dynamicStyles가 적용된 그리드를 export`
  - dynamicStyles가 적용된 그리드를 export한 파일을 엑셀로 열었을때 일부파일이 열리지 않는 현상을 수정하였습니다.
1. `PasteOptions.selectionBase`
  - PasteOptions.selectionBase를 true인 상태에서 붙여넣기 할때 선택된 영역의 첫번째 컬럼이 ColumnGroup인 경우 발생하는 오류를 수정하였습니다.
1. `grid.setHeader`
   - Column.Header에 fixedHeight이 설정되었을때 grid.setHeader({heightFill:"default"})를 실행했을때 ColumnHeader의 높이가 달라는 현상을 수정하였습니다.
1. `TreeView export`
  - dynamicStyle이 적용된 tree에서 하위 노드를 펼쳤다가 접은 후 Excel Export하는 경우 발생하는 오류를 수정하였습니다.
1. `IE에서 dropdown Column에 붙여넣기`
  - IE에서 dropdown컬럼의 textReadOnly속성이 true일때 해당 컬럼에 붙여넣기가 되지 않는 현상이 수정되었습니다.

## 1.1.22 (2017년 2월)

---

#### 기능 개선
1. [SortingOptions](http://help.realgrid.com/api/types/SortingOptions/)
  - 컬럼정렬시 정렬순서를 표시하는 기능이 추가되었습니다.
  - SortingOptions.showSortOrder 를 true로 변경하면 Sort표시 오른쪽에 정렬순서가 표시됩니다.
  - SortingOptins.sortOrderStyles를 이용하여 폰트를 변경할수 있습니다.
```js
grid.setSortingOptions({
    showSortOrder:true, 
    sortOrderStyles:{font:"굴림체", 
    fontSize:10, 
    fontBold:true, 
    foreground:"#ffff8888", 
    textAlignment:"far"
});
```
1. [DisplayOptions](http://help.realgrid.com/api/types/DisplayOptions/)
  - 선택된 셀의 row를 표시할수 있는 rowFocus가 추가되었습니다.
  - DisplayOptions.rowFocusVisible 을 true로 변경하면 선택된 row의 배경색이 지정된 색상으로 표시됩니다.
```js
grid.setDisplayOptions({
    rowFocusVisible:true, 
    rowFocusBackground:"#340000ff"
})
```
  - DisplayOptions.rowFocusMask는 "data","row","fill"의 값을 가질수 있습니다.
1. [dataProvider.addField](http://help.realgrid.com/api/DataProvider/addField/)와 [grid.addColumn](http://help.realgrid.com/api/GridBase/addColumn/), [grid.removeColumn](http://help.realgrid.com/api/GridBase/removeColumn/)이 추가되었습니다.
  - 그리드를 생성하고 난후 필드를 추가하거나 또는 컬럼을 추가해야 하는 경우 사용할수 있도록 addField, addColumn, removeColumn이 추가되었습니다.
```js
dataprovider.addField({
    fieldName:"fieldName", 
    dataType:"text"
});
grid.addColumn({
    fieldName:"fieldName",
    name:"name", 
    ...
})
```
1. `날짜등의 특정포맷에 대한 Mask기능`
  - LineCellEditor와 DateCellEditor에서 사용할수 있는 mask속성이 추가되었습니다.
  - Cell 편집시에 적용되는 속성이며 표시되는 값을 변경하는 경우 datetimeFormat또는 displayRegExp등을 이용해서 변경해야 합니다.
```js
grid.setColumns([
{
    fieldName:"fieldName",
    name:"name",
    editor:{
        type:"date",
        mask:{
            editMask:"9999-99-99",
            includedFormat:true
        }
    },
    styles:{
        datetimeFormat:"yyyy-MM-dd"
    }
}
])
```
  - 자세한 내용은 [Mask](http://help.realgrid.com/api/types/Mask/)를 참조하세요.
1. 그리드 빈공간의 배경색을 변경할수 있도록 개선되었습니다.
  - 그리드의 body.empty.background의 색상을 지정하여 그리드 빈영역의 배경색을 지정할 수 있도록 개선되었습니다.
  - 그리드에 표시되는 데이터가 한건도 없는 경우 사용자에게 메세지를 표시할수 있도록 DisplayOptions.showEmptyMessage가 추가되었습니다.  
```js
grid.setDisplayOptions({
    showEmptyMessage:true, 
    emptyMessage:"자료가 없습니다"
});
grid.setStyles({
    body:{
        empty:{
            background:"#2100ff00", 
            textAlignment:"center", 
            lineAlignment:"center", 
            fontSize:15, 
            fontBold:true
        }
    }
});
```
1. [DisplayOptions](http://help.realgrid.com/api/types/DisplayOptions/)
  - 포커스된 셀의 background를 변경할 수 있도록 focusBackground 속성이 추가되었습니다.
1. [SearchCellEditor](http://help.realgrid.com/api/types/SearchCellEditor/)에서 버튼 클릭 이벤트 추가
- searchCellEditor의 editButton을 클릭했을때 발생하는 [onSearchCellButtonClick](http://help.realgrid.com/api/GridBase/onSearchCellButtonClick/) 이벤트가 추가되었습니다.
1. [onColumnPropertyChanged](http://help.realgrid.com/api/GridBase/onColumnPropertyChanged/)
  - 사용자가 컬럼의 width를 변경하거나 위치를 변경하는 경우 발생하는 onColumnPropertyChanged 이벤트가 추가되었습니다.
1. [dataProvider.getFields](http://help.realgrid.com/api/DataProvider/getFields/)
  - dataProvider.getFields()를 호출했을때 field 정보에 calculatedCallback과 calculatedExpression이 나오지 않는 현상이 개선되었습니다.
1. [SparkLineRenderer](http://help.realgrid.com/api/types/SparkLineRenderer/)
  - SparkLineRenderer의 pointer에 색상을 지정할수 있도록 개선되었습니다.
1. merge된 cell의 툴팁 표시를 행별로 표시
  - merge된 셀의 tooltip이 각셀 별로 표시되도록 개선되었습니다.

#### 오류 수정
1. `getDisplayValues`
  - datetime Column의 styles에 datetimeFormat이 없을때 grid.getDisplayValues() 를 호출하는 경우 발생하는 오류를 수정하였습니다.

1. `footer.text 에 \n 적용 안됨`
  - footer.text에 \n이 있어도 여러줄로 표시되지 않는 현상이 개선되었습니다.

1. `컬럼 그룹안의 컬럼은 onColumnHeaderDblClicked 이벤트가 발생 안함`
  - 컬럼 그룹안의 컬럼을 Double Click했을때 onColumnHeaderDblClicked 이벤트가 발생하지 않는 현상이 수정되었습니다.

1. `컬럼 그룹핑 상태에서 footer가 여러 줄일 때`
  - footer가 여러줄일때 그룹컬럼의 하위 컬럼의 footer가 동일한 값으로 나오는 현상이 개선되었습니다.

1. `shift + insert key로 행 추가시`
  - shift+insert key로 행을 추가시 grid.onRowInserting event의 itemIndex가 실제 추가되는 행의 itemIndex가 나오도록 수정되었습니다.

1. `모바일에서 포커스가 다른 위치에 표시되는 현상`
  - 모바일에서 확대를 했을때 touch된 셀이 아닌 다른 셀이 선택되는 현상을 수정하였습니다.

1. `데이터를 복원할때 groupFooter의 sum값이 변경되지 않는 현상`
  - [restoreMode](http://help.realgrid.com/api/types/RestoreMode/)가 "auto" 또는 "explicit"일때 데이터를 복원하여도 groupFooter의 값이 변경되지 않는 현상이 수정되었습니다.

1. `그리드의 외각선이 사라지는 현상`
  - 화면에 2개의 그리드가 수평으로 배치되었을때 두번째 그리드의 오른쪽 외각선이 사라지는 현상이 개선되었습니다.

1. `fillXmlData 자식노드 유형의 xml 데이터 입력오류`
  - [fillXmlData](http://help.realgrid.com/api/LocalDataProvider/fillXmlData/)를 이용하여 data를 입력할때 값이 xml attributes가 아닌 node에 있을때 값이 누락되는 현상이 수정되었습니다.

1. `fitStyle:"fill"일때 mergeRule 사용시 라인 틀어짐`
  - DisplayOptions.fitStyle이 "fill"인 경우 column의 mergeRule을 적용시 셀의 경계선이 틀어지는 현상이 개선되었습니다.

1. `gridView.getCellApplyStyles`
  - [grid.setCellStyle](http://help.realgrid.com/api/GridBase/setCellStyle/)로 스타일을 지정한 셀의 editable과 readOnly속성이 [grid.getCellApplyStyles](http://help.realgrid.com/api/GridBase/getCellApplyStyles/)에서 누락되는 현상을 수정하였습니다.

1. `Column.editable이 false일 때 셀에 style로 editable:true 지정시 붙여넣기 문제`
  - Column.editable이 false인 컬럼에 setCellStyle로 editable을 true로 지정시 붙여넣기가 되지 않는 현상이 수정되었습니다.

1. `columnGrouping상태에서 자식컬럼을 빼내면 footer영역의 높이가 달라지는 현상`
  - 컬럼그룹핑상태에서 하위컬럼의 부모를 변경하는 경우 footer의 높이가 달라지는 현상이 개선되었습니다.

1. `setCheckableExpression`
  - [grid.setStyles](http://help.realgrid.com/api/GridBase/setStyles/)등 스타일을 변경하고 [grid.setCheckableExpression](http://help.realgrid.com/api/GridBase/setCheckableExpression/)을 호출하는 경우 checkable이 적용되지 않는 현상이 수정되었습니다.


## 1.1.21 (2016년 12월)

---

#### 기능 개선

1. [DisplayOptions](http://help.realgrid.com/api/types/DisplayOptions/)
  - Tooltip이 나타나는 시간을 지연시킬수 있는 `DisplayOptions.hintDuration`속성이 추가되었습니다.
  - `DisplayOptions.hintDuration`을 0 이상으로 지정하면 Tooltip이 지정된 시간만큼 지연되어 표시됩니다.
  - 자세한 내용은 [툴팁]({{ '/CellComponent/Tooltip/' | prepend: site.baseurl }})페이지에서 데모를 참조하세요.

1. [FilterSelectorOptions](http://help.realgrid.com/api/types/FilterSelectorOptions/)
  - 그리드 ColumnFilter의 스타일을 사용자가 지정할수 있도록 `FilteringOptions.selector.useCssStyle`속성이 추가되었습니다.

1. [DisplayOptions](http://help.realgrid.com/api/types/DisplayOptions/)
  - 데이터의 행높이를 각 Row별로 변경할 수 있도록 DisplayOptions.eachRowResizable 속성이 추가되었습니다.

1. [getEditValue()](http://help.realgrid.com/api/GridBase/getEditValue/)
  - 그리드를 편집중인 경우 편집중인 값을 가져올 수 있도록 getEditValue api가 추가되었습니다.

1. [Footer](http://help.realgrid.com/api/types/Footer/)
  - 그리드 Column Footer를 여러 줄로 표시할 수 있도록 `Footer.count` 속성이 추가되었습니다.
  - Column Footer를 여러줄로 표시하는 경우 Column.footer.text와 Column.footer.expression을 배열로 지정할수 있습니다.

1. [MultiCheckCellEditor](http://help.realgrid.com/api/types/MultiCheckCellEditor/)
  - 여러 개의 항목을 선택할 수 있는 MultiCheckCellEditor가 추가되었습니다.

1. [ButtonVisibility](http://help.realgrid.com/api/types/ButtonVisibility/)
  - 행이 선택되었을때만 버튼이 보여지는 `ButtonVisibility.ROWFOCUSED` 속성이 추가되었습니다.
  - 자세한 내용은 [셀버튼]({{ '/CellComponent/CellButton/' | prepend: site.baseurl }})페이지에서 데모를 참조하세요.

1. [ShapeCellRenderer](http://help.realgrid.com/api/types/ShapeCellRenderer/)
  - ShapeCellRenderer에 원을 표시할 수 있도록 ellipse 속성이 추가되었습니다. 자세한 내용은 [도형 렌더러]({{ '/Renderer/ShapeCellRenderer/' | prepend: site.baseurl }})페이지에서 데모를 참조하세요.


#### 오류 수정

1. `RowGrouping 상태에서 ExcelExport`
  - FooterOptions.footerCellMerge:true일때 Excel에서는 merge가 되지않는 현상이 수정되었습니다.
  - RowGroup을 접은상태에서 Export하면 footer의 내용이 일부 나오지 않는 현상이 수정되었습니다.
  - RowGroup.expandedAdornments:"summary"인 경우 Excel Export시 Style이 적용되지 않는 현상이 수정되었습니다.

1. `Footer가 일부만 표시되는 현상`
  - ColumnGroup.orientation이 vertical인 컬럼이 중첩된 경우 footer가 일부만 표시되는 현상이 수정되었습니다.

1. `Excel Export 시 공백이 표시되지 않는 현상`
  - 공백이 있는 Data를 ExcelExport할때 공백이 사라지는 현상을 수정하였습니다.

1. `RowGroup의 childModel을 찾을수 없는 현상`
  - RowGrouping상태에서 그룹의 첫번재 행이 편집중이면 해당 그룹의 childModel을 찾을 수 없는 현상이 수정되었습니다.

1. `getGroupSummary() 함수가 정상적으로 실행되지 않는 현상`
  - MergedRowGrouping상태에서 expandedAdornments가 "footer"인경우 getGroupSummary api의 결과값이 정상적으로 나오도록 수정되었습니다.

1. `그리드의 button이 사라지는 현상`
  - 그리드를 편집중일때 스크롤을 하면 button들이 사라지는 현상이 수정되었습니다.

1. `FireFox에서 일부 문자가 사라지는 현상`
  - FireFox 브라우저에서 영문을 입력시 첫 글자가 일부 사라지는 현상을 수정하였습니다.

1. `RealGrid에서 Export한 파일을 Import할때 오류`
  - DateTime Field가 있는 그리드를 Export하고 Export된 파일을 POI Library를 이용하여 Import할때 발생하는 오류를 수정하였습니다.

1. `EditOptioins.Editalbe이 false일때 붙여넣기 수정`
  - PasteOptions.checkReadOnly:true, EditOptions.Editable:false인 경우에도 붙여넣기가 되는 현상이 수정되었습니다.

1. `Fixed Column이 남아있는 현상`
  - dataProvider.clearRows()와  grid.setFixedOptions()를 순차적으로 호출했을때 FixedColumn이 화면에 남아있는 현상이 수정되었습니다.

1. `Grid.getSelection() 오류 수정`
  - 그리드에서 select하는 방향이 따라서 getSelection() api의 결과값이 달라지는 현상이 수정되었습니다.


## 1.1.20 (2016년 10월)

---

#### 기능 개선

1. [GridBase.checkValidateCells()](http://help.realgrid.com/api/GridBase/checkValidateCells/)
  - 그리드의 전체 셀에 대해 validation이 가능합니다.
  - `checkValidateCells()`함수로 전체 데이터를 검사한 다음 [getInvalidCellList()](http://help.realgrid.com/api/GridBase/getInvalidCellList/)함수를 사용해 validation이 실패한 셀의 목록을 가져올 수 있습니다.

1. [GridBase.getCellApplyStyles()](http://help.realgrid.com/api/GridBase/getCellApplyStyles/)
  - 그리드의 셀에 적용된 스타일을 확인할수 있는 함수가 추가되었습니다.

1. [GridBase.getCellBounds()](http://help.realgrid.com/api/GridBase/getCellBounds/)
  - 그리드 셀의 위치를 반환하는 함수가 추가되었습니다.

1. [DataOutputOptions](http://help.realgrid.com/api/types/DataOutputOptions/)
  - `nullText`, `nanText`, `numberFormat`, `numberCallback`속성이 추가되었습니다.

1. [CellButton.image](http://help.realgrid.com/api/types/CellButton/)
  - `image`속성 추가: 하나의 셀에 여러개의 이미지를 올려 버튼처럼 사용 할 수 있습니다.
  - 이미지를 클릭하면 [onImageButtonClick()](http://help.realgrid.com/api/GridBase/onImageButtonClicked/)콜백 함수가 호출 됩니다.
  - [셀버튼]({{ '/CellComponent/CellButton/' | prepend: site.baseurl }})페이지에서 데모를 참조하세요.

1. [DisplayOptions](http://help.realgrid.com/api/types/DisplayOptions/)
  - `focusColor`속성 추가: 포커스 셀의 색상을 변경 할 수 있습니다.
  - `focusActiveColor`속성 추가: 포커스 셀의 에디터의 테두리 색상을 변경 할 수 있습니다.

1. [NumberCellEditor](http://help.realgrid.com/api/types/NumberCellEditor/)
  - `editFormat`속성 추가: 입력되는 숫자의 포멧을 지정합니다.
  - `textAlignment`속성 추가: 입력위치를 지정합니다. `far`를 지정하면 계산기처럼 오른쪽부터 입력할 수 있습니다.
  - [숫자 편집기]({{ '/Editing/NumberEditor/' | prepend: site.baseurl }})페이지에서 데모를 참조하세요.

1. [GridBase.onItemEditCancel()](http://help.realgrid.com/api/GridBase/onItemEditCancel/)
  - 사용자가 행 편집을 취소하는 시점 발생하는 이벤트 입니다.
  - `false`를 return하면 취소가 되지 않습니다.


#### 오류 수정

1. `commit()함수 호출시 메시지 팝업 오류`
  - [DataProviderOptions.commitBeforeDataEdit](http://help.realgrid.com/api/types/DataProviderOptions/)속성이 `true`일 때 [GridBase.onCellEdited](http://help.realgrid.com/api/GridBase/onCellEdited/) event에서 [commit()](http://help.realgrid.com/api/GridBase/commit/)함수 호출시 client Editing 관련 메시지가 팝업되는 현상을 수정했습니다.

1. `병합(merge)된 셀의 팝업메뉴 위치 오류`
  - 병합(merge)된 셀의 팝업 버튼(pupupButton)을 클릭했을 때 팝업메뉴(popupMenu)가 병합된 셀의 하단에 생성되는 현상을 수정했습니다.

1. `GridBase.setColumns()함수 두 번 호출시 헤더 이미지 위치 오류`
  - GridBase.setColumns()함수를 두 번 호출하는 경우 헤더의 이미지가 왼쪽 위로 이동하는 현상을 수정했습니다.

1. `복수행 붙여넣기시 validation 오류`
  - [PasteOptions.forceColumnValidation](http://help.realgrid.com/api/types/PasteOptions/)이 `true`이면서 컬럼에 validation이 설정되어 있을 때 복수행을 붙여넣기하는 경우 validation오류가 발생하는 현상을 수정했습니다.

1. `checkCellRenderer의 체크 오류`
  - checkCellRenderer 컬럼이 병합(merge)된 경우 병합(merge)된 cell중 첫 번째 행만 체크되는 현상을 수정했습니다.

1. `DataProvider.moveRow()시 삭제행이 보여지는 현상`
  - [DataProviderOptions.softDeleting](http://help.realgrid.com/api/types/DataProviderOptions/)이 `true`이고 [GridOptions.hideDeletedRows](http://help.realgrid.com/api/types/GridOptions/)가 `true`일때 [LocalDataProvider.moveRow()](http://help.realgrid.com/api/LocalDataProvider/moveRow/)를 이용하여 행을 이동하는 경우 삭제된 행이 보여지는 현상을 수정했습니다.

1. `MultiLineCellEditor의 복사/붙여넣기 오류`
  - [MultiLineCellEditor](http://help.realgrid.com/api/types/MultiLineCellEditor/)인 컬럼을 선택했을 때 복사 또는 붙여넣기가 안되는 현상을 수정했습니다.

1. `TreeView 엑셀 내보내기 오류`
  - TreeView에서 엑셀 내보내기 할때 [GridExportOptions.showProgress](http://help.realgrid.com/api/types/GridExportOptions/)를 `true`로 하면 비정상적으로 export되는 현상을 수정했습니다.

1. `ColumnGroupOrientation이 vertical인 경우 붙여넣기 오류`
  - [ColumnGroupOrientation](http://help.realgrid.com/api/types/ColumnGroupOrientation/)이 `vertical`인 그리드에서 여러 행을 복사 후 붙여넣기할 때 행이 추가되는 경우 발생하는 오류를 수정하였습니다.

1. `스크롤바 오류`
  - 전체 컬럼의 너이가 그리드의 너비 보다 큰 경우에도 가로 스크롤바가 즉시 생기지 않는 현상이 수정되었습니다.

1. `크롬브라우저에서 클릭시 스크롤 위치 오류`
  - 크롬브라우저에서 그리드의 `div`태그를 감싸고 있는 상위 `div`의 크기가 작아서 그리드가 들어 있는 레이어(layer)가 스크롤 되었을 때 그리드를 클릭하면 그리드의 스크롤 위치가 변경되는 현상이 일부 개선되었습니다.

1. `GridBase.onItemChecked() 이벤트 반복 오류`
  - [GridBase.onItemChecked()](http://help.realgrid.com/api/GridBase/onItemChecked/) 이벤트 내부에서 checkItem, checkRow를 사용하는 경우 이벤트가 반복적으로 발생하지 않도록 수정하였습니다. 자세한 내용은 [CheckBar 페이지]({{ "/GridComponent/CheckBar/" | prepend: site.baseurl }})를 참조하세요.


## 1.1.19 (2016년 9월)

---

1.1.19버전에서는 새로운 기능이 추가 되거나 개선되었습니다. 또, 지난 버전 이후 문제되었던 크고 작은 오류들도 해결되었습니다.<br/>
아래에서 내용을 확인하고 링크를 클릭하여 자세한 사용방법등을 알아보세요.

#### 기능 개선

1. [Renderer.showTooltip](http://help.realgrid.com/api/types/TextCellRenderer/)
  - TextCellRenderer에서만 가능했던 showTooltip속성을 모든 Cell Renderer에 적용되도록 개선했습니다.
1. [GridBase.onContextMenuPopup](http://help.realgrid.com/api/GridBase/onContextMenuPopup/)
  - `elementName` - 컨텍스트메뉴(Context Menu)가 활성화 될때 마우스 클릭 위치에 있는 영역의 명칭을 넘겨주기 위한 인자를 추가했습니다.
  - `return false` - 이벤트에서 false를 리턴하면 컨텍스트메뉴(Context Menu)가 활성화 되지 않도록 개선했습니다.
1. [GridBase.onTopItemIndexChanged](http://help.realgrid.com/api/GridBase/onTopItemIndexChanged/)
  - 그리드가 스크롤될때 발생하는 이벤트로 `onTopItemIndexChanged`가 추가되었습니다.
  - [Event Order](http://demo.realgrid.com/Demo/EventOrder) 페이지에서 확인하세요.
1. [RowGroup Footer 상단표시](http://help.realgrid.com/api/types/RowGroupAdornments/)
  - `RowGroup Footer`를 그룹의 상단에 표시할수 있도록 개선했습니다.
  - `expandedAdornments` - RowGroup Footer를 그룹상단에 표시하기 위해 `expandedAdornments`속성을 `'summary'`로 설정하면 됩니다.
  - [RowGrouping](RowGroup/RowGrouping)페이지에서 확인하세요.
1. [ExportOptions.done](http://help.realgrid.com/api/types/GridExportOptions/)
  - [GridBase.exportGrid()](http://help.realgrid.com/api/GridBase/exportGrid/)함수 호출시 Export가 완료된 시점에 호출되는 Callback function을 `done` 속성으로 추가했습니다.
  - 샘플 코드를 참조하세요.
```js
gridView.exportGrid({
  type:"excel",
  target:"local",
  done:function() {
    alert("엑셀 내보내기가 완료되었습니다.");
  }
});
```
1. [styles.textWrap](http://help.realgrid.com/api/features/Styling/)
  - `styles.textWrap`속성의 값이 `'normal'`또는 `'explicit'`인 경우 컬럼 넓이 자동조정이 개선되었습니다.
1. [DisplayOptions.toastZIndex](http://help.realgrid.com/api/types/DisplayOptions/)
  - ToastView의 zIndex값을 수정할수 있도록 `toastZIndex`속성이 추가되었습니다.
  - [ToastOptions.zIndex](http://help.realgrid.com/api/types/ToastOptions/)속성을 변경해도 동일한 결과를 얻을 수 있습니다.
  - 샘플코드를 참조하세요.
```js
gridView.setDisplayOptions({
  toastZIndex:100
});
```
또는
```js
gridView.showToast({
  message: '메세지를 입력하세요',
  zIndex: 100
});
```

1. [PasteOptions.checkDomainOnly](http://help.realgrid.com/api/types/PasteOptions/)
  - DropDown Editor의 `domainOnly`가 `'true'`인 경우, `values`에 없는 값은 붙여넣기 되지 않도록 할 수 있는 PasteOptions.checkDomainOnly 속성이 추가되었습니다.
  - [Copy And Paste](Editing/CopyAndPaste)페이지에서 확인하세요.
1. [RowGroupOptions.sorting](http://help.realgrid.com/api/types/RowGroupOptions/)
  - RowGroup시 자동 정렬 여부를 결정하기 위해 `RowGroup.sorting`속성이 추가되었습니다.
  - 기본값은 true입니다.
  - false로 설정하면 RowGroup시 자동으로 정렬되지 않고 그리드에 표시된 데이터의 순서대로 그룹핑 됩니다.
  - [GridView.groupBy()](http://help.realgrid.com/api/GridView/groupBy/)함수의 두번째 인자로 `sorting`여부를 넘겨줄 수도 있습니다.
  - 아래 샘플코드를 참조하세요.
```js
gridView.groupBy(['field1', 'field2'], true, 'ascending');
```
또는
```js
gridView.groupBy(['field1', 'field2'], false);
```
  - [RowGrouping](RowGroup/RowGrouping)페이지에서 확인하세요.
1. [EditOptions.insertable](http://help.realgrid.com/api/types/EditOptions/)
  - 행 삽입(insert)시 현재행의 아래에 새로운 행을 삽입할 수 있는 기능을 추가했습니다.
  - `'true'`인 경우 \[shift\]+\[insert\]키를 입력하면 새로운 행이 아래에 추가됩니다.
  - [GridView.beginInsertRow()](http://help.realgrid.com/api/GridView/beginInsertRow/)함수의 두 번째 인자로 `'true'`를 입력하면 동일한 동작을 구현할수 있습니다.
  - [Inserting](Editing/Inserting)페이지에서 확인하세요.
1. [PasteOptions.noEditEvent]()
  - `PasteOptions.noEditEvent`속성이 `'true'`인 경우 붙여넣기시 onCellEdited이벤트가 발생하지 않도록 수정되었습니다.


#### 오류 수정

1. `onRowInserted이벤트에서 dataProvider.setValue()함수 사용시 오류 발생 현상`
  - 새로운 행 추가시 발생하는 `onRowInserted`이벤트 내에서 `dataProvider.setValue()`함수를 사용할 때 오류가 발생하던 문제를 해결했습니다.
1. `MergeRule이 적용되지 않는 현상`
  - MergeRule이 적용된 컬럼이 RowGroup에 추가되어 있을때 그룹을 접고 RowGroup에서 해당 컬럼을 제외하면 MergeRule이 해제되던 오류를 수정했습니다.
1. `DisplayOptions.fitStyle 변경시 라인이 틀어지는 현상`
  - DisplayOptions.fitStyle이 `even` 또는 `evenFill` 일때 ColumnHeader와 DataCell의 라인이 틀어지는 문제를 해결했습니다.
1. `값이 없는 셀 복사시 오류`
  - 그리드에 Cell의 값이 없는 곳을 선택한 후 복사했을때 잘못된 문자열이 복사되는 오류를 수정했습니다.
1. `DataProvider.restoreUpdatedStates(0)함수 사용 오류`
  - DataProvider.restoreUpdatedStates(0)을 사용했을때 전체 row의 state까지 변경되는 오류를 수정했습니다.
1. `Export된 Excel의 부자연스러운 경계선`
  - RowGroup상태에서 Excel Export시 merge된 셀의 세로 경계선이 부자연스러운 현상을 수정하였습니다.
1. `Excel Export시 Fixed Column의 스타일 적용 오류`
  - 그리드를 excel export시 Fixed Column의 Style이 적용되지 않는 현상을 수정하였습니다.
1. `Date Editor의 날짜선택 오류`
  - Date Editor의 `textReadOnly`가 `true`인 경우 date Picker에서 선택을 하여도 날짜가 변경되지 않는 현상을 수정하였습니다.
1. `잘못된 날짜를 입력시 애매한 표현`
  - 잘못된 날짜를 입력하는경우 `NaN/NaN/NaN`으로 표시 되던것을 `빈문자`가 표시되도록 수정하였습니다.
1. `TreeView의 체크박스 오류`
  - TreeView의 `TreeOptions.showCheckBox`를 `true`로 변경했을때 체크된 행이 적용되지 않는 문제를 해결했습니다.
1. `TreeView에서 Indicator 선택 오류`
  - TreeView의 Indicator영역을 이용한 행 선택시 첫 번째 행부터 선택되는 오류를 수정하였습니다.
1. `Selection오류`
  - 컬럼그룹이 중첩되어있고 `Orientation`이 `vertical`인 경우 Selection이 정상적으로 되지 않는 오류를 수정했습니다.
1. `Multiline Editor의 붙여넣기 오류`
  - RowValidation이 설정된 그리드의 MultiLine Editor에 여러행 붙여넣기를 할때 Validation이 발생하는 경우 focus된 셀이 모두 붙여넣기가 되던 문제를 해결했습니다.
1. `Validation 아이콘 표시문제`
  - `onValidateColumn`사용시 첫 번째행과 마지막행에서는 Validation 아이콘이 표시되지 않는 문제를 수정하였습니다.

## 1.1.18 (2016년 8월)

- Column Filter의 조건에 개행문자가 있는 경우 필터생성은 되나 필터적용시 오류가 발생하는 현상을 수정하였습니다.
- Filter조건에 날짜관련 수식을 추가하였습니다. 자세한 내용은 ColumnFiltering 페이지를 참조바랍니다.
- Excel Export시 DynamicStyle을 Export할수 있도록 개선되었습니다. ExportOptions.applyDynamicStyles를 true로 설정하면 Grid에 적용된 Style이 Export됩니다. Export to Excel File 페이지를 참조바랍니다.
- Field의 DataType이 Date인 컬럼은 Column.mergeRule에 의해서 셀 병합되지 않는 문제를 수정하였습니다.
- ColumnGroup의 하위 Column도 Column.mergeRule이 적용되도록 수정하였습니다. ColumnGroup.orientation이 vertical인 경우에는 적용되지 않습니다.
- Grid.onItemEditCanceled이벤트가 추가되었습니다. 자세한 내용은 onItemEditCanceled를 참조바랍니다.
- Column의 visible을 변경할때 Column의 순서가 바뀌는 현상을 개선하였습니다.
- Column.mergeRule이 설정되어있을때 RowGrouping상태에서 dataProvider.clearRows()를 호출하였을때 발생하는 오류를 수정하였습니다.
- 중첩된 rowGrouping시 상위 컬럼을 그룹에서 제거하면 하위 컬럼도 같이 제거될수 있도록 RowGroupingOptions.removeIncludeLower속성을 추가하였습니다. true로 설정시 상위 컬럼을 그룹에서 제거하면 하위컬럼도 함께 제거됩니다. (기본값은 false)
