---
layout: page
title: 최신버전 (1.1.19)
permalink: /release/
---

<div class="nav-item show-desktop">
  <a class="btn orange small round lowercase"
      href="http://www.realgrid.com/license"
      target="_new">
      <span>평가판</span>
  </a>
</div>

## 2016년 9월 (1.1.19)

1.1.19버전에는 GridView의 여러가지 기능이 추가되거나 개선되었습니다.
또, 지난 버전 이후 문제되었던 크고 작은 오류들도 해결되었습니다.
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

## 2016년 8월 (1.1.18)

- Column Filter의 조건에 개행문자가 있는 경우 필터생성은 되나 필터적용시 오류가 발생하는 현상을 수정하였습니다.
- Filter조건에 날짜관련 수식을 추가하였습니다. 자세한 내용은 ColumnFiltering 페이지를 참조바랍니다.
- Excel Export시 DynamicStyle을 Export할수 있도록 개선되었습니다. ExportOptions.applyDynamicStyles를 true로 설정하면 Grid에 적용된 Style이 Export됩니다. Export to Excel File 페이지를 참조바랍니다.
- Field의 DataType이 Date인 컬럼은 Column.mergeRule에 의해서 셀 병합되지 않는 문제를 수정하였습니다.
- ColumnGroup의 하위 Column도 Column.mergeRule이 적용되도록 수정하였습니다. ColumnGroup.orientation이 vertical인 경우에는 적용되지 않습니다.
- Grid.onItemEditCanceled이벤트가 추가되었습니다. 자세한 내용은 onItemEditCanceled를 참조바랍니다.
- Column의 visible을 변경할때 Column의 순서가 바뀌는 현상을 개선하였습니다.
- Column.mergeRule이 설정되어있을때 RowGrouping상태에서 dataProvider.clearRows()를 호출하였을때 발생하는 오류를 수정하였습니다.
- 중첩된 rowGrouping시 상위 컬럼을 그룹에서 제거하면 하위 컬럼도 같이 제거될수 있도록 RowGroupingOptions.removeIncludeLower속성을 추가하였습니다. true로 설정시 상위 컬럼을 그룹에서 제거하면 하위컬럼도 함께 제거됩니다. (기본값은 false)
