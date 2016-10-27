---
layout: page
title: 최신버전 (1.1.19)
---

<div class="nav-item show-desktop">
  <a class="btn orange small round lowercase"
      href="http://www.realgrid.com/license"
      target="_new">
      <span>평가판</span>
  </a>
</div>

## September 2016 (1.1.19)

- Renderer.showTooltip속성이 TextCellRenderer뿐 아니라 Data를 표시하는 전체 Cell Renderer에서 적용되도록 개선되었습니다.
- 그리드에서 행을 추가할때 dataProvider.onRowInserted 이벤트에서 dataProvider.setValue api를 사용할때 발생하는 오류를 수정하였습니다.
- onContextMenuPopup 이벤트에 elementName이 추가되었습니다. 이베트에서 false를 return하면 contextMenu가 생성되지 않도록 개선되었습니다. ContextMenu 페이지에서 확인하세요.
- 그리드를 스크롤할때 발생되는 onTopItemIndexChanged event가 추가되었습니다. Event Order 페이지에서 확인하세요.
- RowGroup Footer를 그룹의 상단에 표시할수 있도록 개선되었습니다. RowGroup.expandedAdornments속성을 "summary"로 설정하면 rowGroup Footer가 그룹상단에 - 표시됩니다. 자세한 내용은RowGrouping페이지를 참조바랍니다.
- MergeRule이 적용을 컬럼을 rowGroup에 추가한 후 그룹이 접힌 상태에서 rowGroup에서 제외하는 경우 MergeRule이 해제되는 현상을 개선하였습니다.
- 그리드를 Export할때 Export가 끝난 시점을 알수 있도록 ExportOptions.done Callback을 추가하였습니다. gridView.exportGrid({type:"excel",target:"local",done:function() {alert("done excel export")}})형태로 사용할수 있습니다.
- 그리드에 Cell의 값이 없는 곳을 선택한후 복사했을때 잘못된 문자열이 복사되는 현상을 수정하였습니다.
- DataProvider.restoreUpdatedStates(0)을 사용했을때 전체 row의 state까지 변경되는 현상을 수정하였습니다.
- RowGroup상태에서 Excel Export시 merge된 셀의 세로 경계선이 부자연스러운 현상을 수정하였습니다.
- 그리드를 excel export시 Fixed Column의 Style이 적용되지 않는 현상을 수정하였습니다.
- date Editor의 textReadOnly가 true인경우 date Picker에서 선택을 하여도 날짜가 변경되지 않는 현상을 수정하였습니다.
- 잘못된 날짜를 입력하는경우 NaN/NaN/NaN으로 표시되던것을 공백으로 표시되도록 수정하였습니다.
- treeView의 treeOptions.showCheckBox를 true로 변경했을때 Check된 row가 적용되지 않는 현상을 개선하였습니다.
- treeView의 indicator영역을 이용한 RowSelect시 첫번째 행부터 선택되는 오류를 수정하였습니다.
- columnGroup이 중첩되어있고 Orientation이 Vertical인경우 Selection이 정상적으로 되지 않는 현상을 개선하였습니다.
- styles.textWrap이 "normal"또는 "explicit"인경우 컬럼 넓이 자동조정이 개선되었습니다.
- rowValidation이 설정된 그리드의 multiLine Editor에 여러행 붙여넣기를 할때 Validation이 발생하는 경우 focus된 셀이 모두 붙여넣기가 되는 현상이 수정되었습니다.
- toastView의 zIndex값을 수정할수 있도록 DisplayOptions.toastZIndex 속성이 추가되었습니다. gridView.setDisplayOptions({toastZIndex:100}) 또는 gridView.showToast({message:"메세지를 입력하세요", zIndex:100})와 같은 방식으로 사용할수 있습니다.
- DropDown Editor의 domainOnly가 true인경우 붙여넣기 할때 values에 없는 값은 붙여넣기 되지 않도록 PasteOptions.checkDomainOnly 속성이 추가되었습니다. Copy And Paste 페이지에서 확인하세요.
- DisplayOptions.fitStyle이 "even" 또는 "evenFill" 일때 ColumnHeader와 DataCell의 라인이 맞지않는 현상을 개선하였습니다.
- RowGroup.sorting 속성이 추가되었습니다. 기본값은 true입니다. false로 설정하면 rowGroup시 자동으로 정렬되지 않고 그리드에 표시된 데이터의 순서대로 RowGrouping됩니다. api를 이용한 rowGrouping시에는 gridView.groupBy([field1,field2],true || false)와 같이 사용할수 있습니다. 자세한 내용은RowGrouping페이지를 참조바랍니다.
- EditOptions.insertable이 true인경우 shift+insert키를 입력하는 경우 현재행 아래에 새로운 행이 추가되도록 변경되었습니다. api를 이용하는 경우 gridView.beginInsertRow(0,true)를 사용할수 있습니다. 자세한 내용은 Inserting 페이지를 참조바랍니다.
- onValidateColumn 사용시 첫번째행과 마지막행에서는 validation icon이 표시되지 않는 문제를 수정하였습니다.
- PasteOptions.noEditEvent가 true인경우 onCellEdited도 발생하지 않도록 수정되었습니다.

## August 2016 (1.1.18)

- Column Filter의 조건에 개행문자가 있는 경우 필터생성은 되나 필터적용시 오류가 발생하는 현상을 수정하였습니다.
- Filter조건에 날짜관련 수식을 추가하였습니다. 자세한 내용은 ColumnFiltering 페이지를 참조바랍니다.
- Excel Export시 DynamicStyle을 Export할수 있도록 개선되었습니다. ExportOptions.applyDynamicStyles를 true로 설정하면 Grid에 적용된 Style이 Export됩니다. Export to Excel File 페이지를 참조바랍니다.
- Field의 DataType이 Date인 컬럼은 Column.mergeRule에 의해서 셀 병합되지 않는 문제를 수정하였습니다.
- ColumnGroup의 하위 Column도 Column.mergeRule이 적용되도록 수정하였습니다. ColumnGroup.orientation이 vertical인경우에는 적용되지 않습니다.
- Grid.onItemEditCanceled이벤트가 추가되었습니다. 자세한 내용은 onItemEditCanceled를 참조바랍니다.
- Column의 visible을 변경할때 Column의 순서가 바뀌는 현상을 개선하였습니다.
- Column.mergeRule이 설정되어있을때 RowGrouping상태에서 dataProvider.clearRows()를 호출하였을때 발생하는 오류를 수정하였습니다.
- 중첩된 rowGrouping시 상위 컬럼을 그룹에서 제거하면 하위 컬럼도 같이 제거될수 있도록 RowGroupingOptions.removeIncludeLower속성을 추가하였습니다. true로 설정시 상위 컬럼을 그룹에서 제거하면 하위컬럼도 함께 제거됩니다. (기본값은 false)
