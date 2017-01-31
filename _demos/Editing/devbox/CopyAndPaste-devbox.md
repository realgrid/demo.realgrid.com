#### [Copy Options](http://help.realgrid.com/api/types/CopyOptions/){:target="_blank"}
[Copy Options](http://help.realgrid.com/api/types/CopyOptions/){:target="_blank"}을 설정하여 그리드에서 복사를 허용할 것인지, 날짜나 불린 타입의 경우 복사되는 값의 포맷을 지정할 수 있습니다. 

<input type="checkbox" id="chkSingleMode">singleMode: 포커스를 갖는 셀 하나의 값만 클립보드로 복사  
<input type="checkbox" id="chkEnabled">enabled: Copy가능여부 설정  

<a class="btn primary small round lowercase" id="btnSetCopyOptions">setCopyOptions()
</a>

```js
gridView.setCopyOptions({
  singleMode: $("#chkSingleMode").is(":checked"),
  datetimeFormat: "yyyy/MM/dd",
  booleanFormat:"N;Y"
});
```


#### [Paste Options](http://help.realgrid.com/api/types/PasteOptions/){:target="_blank"}
[Paste Options](http://help.realgrid.com/api/types/PasteOptions/){:target="_blank"}을 설정하여 붙여넣기시에 요구되는 다양한 옵션들을 설정할 수 있습니다.    

<input type="checkbox" id="chkPasteSingleMode">singleMode: 포커스를 갖는 셀 하나에만 붙여넣기    
<input type="checkbox" id="chkPasteEnabled">enabled: Paste가능여부 설정    
<input type="checkbox" id="chkStartEdit">startEdit: 붙여넣게 될 값이 복수 행이 아니고, 붙여넣을 행이 아직 편집 중이 아니면 편집을 시작    
<input type="checkbox" id="chkCommitEdit">commitEdit: 복수 행 붙여넣기일 때 기존 편집 상태를 commit    
<input type="checkbox" id="chkEnableAppend">enableAppend: 붙여넣을 복수 행이 기존 행의 범위를 넘어설 때 행을 추가  
<input type="checkbox" id="chkFillFieldDefaults">fillFieldDefaults: 행 추가시 포함되지 않은 필드의 값을 data field의 기본값으로 채움  
<input type="checkbox" id="chkFillColumnDefaults">fillColumnDefaults: 행 추가시 포함되지 않은 필드의 값을 컬럼의 기본값으로 채움  
<input type="checkbox" id="chkForceRowValidation">forceRowValidation: 복수행 붙여 넣기 중 행별로 행 validation을 실행  
<input type="checkbox" id="chkForceColumnValidation">forceColumnValidation: 복수행 붙여 넣기 중 행별로 컬럼 validation을 실행  
<input type="checkbox" id="chkSelectionBase">selectionBase: true면 focus 셀이 포함된 선택 영역의 처음 셀부터 붙여넣기 시작  
<input type="checkbox" id="chkStopOnError">stopOnError: Validation이 실패하거나 형변환이 실패하면 나머지 붙여넣기를 중지하고 예외를 발생  
<input type="checkbox" id="chkNoEditEvent">noEditEvent: 단일행을 붙여넣기 할때 Cell마다 발생하는 onEditRowChanged가 발생하지 않는다.  
<input type="checkbox" id="chkEventEachRow">eventEachRow: 복수행을 붙여넣기 할때 각 행마다 onEditRowPasted이벤트가 발생    
<input type="checkbox" id="chkCheckReadOnly">checkReadOnly: readOnly이거나 editable이 false인 Column은 paste대상에서 제외  
<input type="checkbox" id="chkCheckDomainOnly">checkDomainOnly: DropDown Editor의 domainOnly가 true인 컬럼에 붙여넣기 할때 values에 없는 값은 붙여넣기 되지 않음    

<a class="btn primary small round lowercase" id="btnSetPasteOptions">setPasteOptions()
</a>

```js
gridView.setPasteOptions({
  singleMode: $("#chkPasteSingleMode").is(":checked"),
  enabled: $("#chkPasteEnabled").is(":checked"),
  startEdit: $("#chkStartEdit").is(":checked"),
  commitEdit: $("#chkCommitEdit").is(":checked"),
  enableAppend: $("#chkEnableAppend").is(":checked"),
  fillFieldDefaults: $("#chkFillFieldDefaults").is(":checked"),
  fillColumnDefaults: $("#chkFillColumnDefaults").is(":checked"),
  forceRowValidation: $("#chkForceRowValidation").is(":checked"),
  forceColumnValidation: $("#chkForceColumnValidation").is(":checked"),
  selectionBase: $("#chkSelectionBase").is(":checked"),
  stopOnError: $("#chkStopOnError").is(":checked"),
  noEditEvent: $("#chkNoEditEvent").is(":checked"),
  eventEachRow: $("#chkEventEachRow").is(":checked"),
  checkReadOnly: $("#chkCheckReadOnly").is(":checked"),
  checkDomainOnly: $("#chkCheckDomainOnly").is(":checked")
});
```
<script>

  $('#btnSetCopyOptions').click(function() {
    gridView.setCopyOptions({
      singleMode: $("#chkSingleMode").is(":checked"),
      datetimeFormat: "yyyy/MM/dd",
      booleanFormat:"N;Y"
    });
  });

  $('#btnSetPasteOptions').click(function() {
    gridView.setPasteOptions({
      singleMode: $("#chkPasteSingleMode").is(":checked"),
      enabled: $("#chkPasteEnabled").is(":checked"),
      startEdit: $("#chkStartEdit").is(":checked"),
      commitEdit: $("#chkCommitEdit").is(":checked"),
      enableAppend: $("#chkEnableAppend").is(":checked"),
      fillFieldDefaults: $("#chkFillFieldDefaults").is(":checked"),
      fillColumnDefaults: $("#chkFillColumnDefaults").is(":checked"),
      forceRowValidation: $("#chkForceRowValidation").is(":checked"),
      forceColumnValidation: $("#chkForceColumnValidation").is(":checked"),
      selectionBase: $("#chkSelectionBase").is(":checked"),
      stopOnError: $("#chkStopOnError").is(":checked"),
      noEditEvent: $("#chkNoEditEvent").is(":checked"),
      eventEachRow: $("#chkEventEachRow").is(":checked"),
      checkReadOnly: $("#chkCheckReadOnly").is(":checked"),
      checkDomainOnly: $("#chkCheckDomainOnly").is(":checked")
    });
  });  


</script>
