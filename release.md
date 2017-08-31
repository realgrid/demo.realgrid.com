---
layout: page
title: '최신버전 1.1.25'
published: true
permalink: /release/
---

{% comment %}
  - 함수 링크는 원본 객체명과 함께 작성해 주세요.
    - 예: GridBase.checkValidateCells()
  - 객체명, 함수명, 옵션명, 속성명의 대소문자 사용에 주의 하세요.
    - 예: PasteOptions.forceColumnValidation 속성
{% endcomment %}

## 1.1.25 (2017년 8월)

---

#### 기능 개선
1. [searchCell](http://help.realgrid.com/api/GridBase/searchCell/)  
  - gridView.searchCell을 이용해서 date형식의 자료를 찾을때 일부만 입력하여 검색가능하도록 개선되었습니다.
  - 구분자는 ".", "-", "/"를 사용할수 있으며 구분자없이 "201708"형태로도 검색가능합니다.
```js
  gridView.serachCell({fields:["dateField1", "dateField2"], value:"2017-08", partialMatch:true})
```

1. [NumberCellEditor](http://help.realgrid.com/api/types/NumberCellEditor/)
  - numberCellEditor에서 숫자 중간에 입력하는 경우 caret이 끝으로 이동하지 않도록 개선되었습니다.

1. [clearInvalidCellList](http://help.realgrid.com/api/GridBase/clearInvalidCellList/)
  - validation이 실패한 셀의 목록을 초기화 할수 있는 clearInvalidCellList함수가 추가되었습니다.

1. [ColumnHeader](http://help.realgrid.com/api/types/ColumnHeader/)
  - ColumnHeader의 image를 클릭시 발생하는 onColumnHeaderImageClicked 이벤트가 추가되었습니다.

1. [onBodyEmptyClicked](http://help.realgrid.com/api/GridBase/onBodyEmptyClicked/)
  - 그리드의 빈 영역을 클릭했을때 발생하는 onBodyEmptyClicked 이벤트와 onBodyEmptyDblClicked이벤트가 추가되었습니다.

1. [DynamicStyle](http://help.realgrid.com/api/types/DynamicStyle/)
  - 변경된 cell의 style을 변경할수 있도록 [Expression](http://help.realgrid.com/api/features/Expression/)에 "changedcell" 조건이 추가 되었습니다.
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
  - 그리드를 Excel로 Export할때 checkBar에 체크된 행만 Export할수 있도록 `GridExportOptions.onlyCheckedItems` 속성이 추가 되었습니다.
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
  - cell을 doubleTouch하면 편집상태로 변경이 됩니다.
  - dropdownEditor, dateEditor의 경우 cell을 선택후 editButton을 touch하면 편집상태로 변경됩니다.

1. [DisplayOptions](http://help.realgrid.com/api/types/DisplayOptions/)
  - DisplayOptions.rowFocusOption 속성이 추가 되었습니다.
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
  - progressView의 스타일을 사용자가 지정할수 있도록 DisplayOptions.useCssStyleProgress 속성이 추가 되었습니다.
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
  - gridView.searchItem과 유사한 역활을 하는 dataProvider.searchDataRow함수가 추가 되었습니다.  
  - gridView.searchCell과 유사한 역활을 하는 dataProvider.serachData함수가 추가 되었습니다.  
  자세한 내용은 [트리뷰 노드 검색하기]({{ '/Tree/TreeSearchRow/' | prepend: site.baseurl }})데모를 참조하세요. 

1. [GropingOptions](http://help.realgrid.com/api/types/GroupingOptions/)
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
  - [ColumnHeaderOptions](http://help.realgrid.com/api/types/ColumnHeaderOptions/)에 popupMenu관련 속성이 추가 되었습니다.
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
  - gridView.searchCell을 이용해서 찾기시 "undefined"를 찾으면 value가 undefined인 cell이 검색되는 현상을 수정하였습니다.

1. `checkBar`
  - checkBar의 check를 클릭하였을때 그리드가 스크롤되는 현상을 수정하였습니다.

1. `dataProvider.getUpdatedCells`
  - [dataProvider.getUpdatedCells](http://help.realgrid.com/api/DataProvider/getUpdatedCells/)를 이용해서 수정된 cell을 가져올때 수정된 행을 모두 가져오지 못하는 오류를 수정하였습니다.

1. `gridExport.documentTitle`
  - 1.1.24버전에서 gridExport.documentTitle.spaceTop을 설정했을때 발생하는 오류를 수정하였습니다.

1. `selectOptionis.style`
  - selectOptions.style이 "rows"일때 아래쪽에서 위로 범위 설정후 마우스 우클릭시 범위 설정이 해제되는 오류를 수정하였습니다.

1. `displayOptions.rowHeight`
  - displayOptions.rowHeight의 값을 잘못된 값으로 설정시 그리드가 깨지는 오류를 수정하였습니다.

1. `Mobile TreeGrid`
  - Mobile TreeGrid에서 화면 touch를 이용해서 스크롤할때 이동되지 않는 오류를 수정하였습니다.

1. `GridExport`
  - DataField의 DataType이 number이고 Column.styles.numberFormat이 `"#,##0;,;."`인 컬럼을 Excel로 Export하는 경우 음수인 Data가 Excel에서 정상적으로 보이지 않는 오류를 수정하였습니다.

1. `DataField.defaultValue`
  - DataField.defaultValue가 설정되어있어도 insert 또는 append시 적용되지 않는 오류가 수정되었습니다.

1. `paste`
  - 편집 불가 상태의 cell에 열단위 붙여넣기를 했을때 붙여넣기가 되지 않는 현상을 수정하였습니다.

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
  - 사용자가 마우스를 움직일때 마우스 위치에 해당하는 DataRow를 보여줄수 있도록 [rowHoverMask](http://help.realgrid.com/api/types/RowHoverMask/)속성이 추가 되었습니다.
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

### 오류 수정
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
  - Export시 전체 data를 출력할수 있는 pagingAllItems 옵션이 추가 되었습니다.
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
