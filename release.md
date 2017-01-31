---
layout: page
title: '최신버전 1.1.21'
published: true
permalink: /release/
---

{% comment %}
  - 함수 링크는 원본 객체명과 함께 작성해 주세요.
    - 예: GridBase.checkValidateCells()
  - 객체명, 함수명, 옵션명, 속성명의 대소문자 사용에 주의 하세요.
    - 예: PasteOptions.forceColumnValidation 속성
{% endcomment %}

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
