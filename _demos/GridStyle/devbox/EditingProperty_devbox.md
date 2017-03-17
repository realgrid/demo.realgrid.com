
#### DataCellStyle 설정하기

 DataCellStyle은 id를 갖는 표시 스타일 속성들 및 편집 관련 속성들로 구성된 객체입니다.  
 이 스타일들을 GridBase.addCellStyle(id, style) 함수로 그리드에 미리 등록하고, GridBase.setCellStyles(dataRow, field, style) 함수로 특정한 데이터셀에 스타일을 지정합니다.  
 Editing 관련 속성으로는 editable과 readOnly 속성을 지원합니다.   

<a class="btn primary small round lowercase" id="btnAddCellStyles">셀 스타일 추가하기</a>

```js
gridView.addCellStyle("style01", {
    "foreground": "#ffffffff",
    "background": "#ff333333",
    "fontSize": 13,
    "fontBold": true,
    "editable": false
});
gridView.addCellStyle("style02", {
    "foreground": "#ff000000",
    "background": "#ffcccccc",
    "fontSize": 13,
    "readOnly": true
});
```


검정 바탕의 셀은 editable 속성이 false 이고 회색 바탕의 셀은 readOnly 속성이 true가 되도록 영역의 DataCellStyle들을 지정했습니다.

<a class="btn primary small round lowercase" id="btnSetCellStyles">셀 스타일 적용하기</a>

```js
gridView.setCellStyles([0, 1, 2, 3, 4, 5, 6], ["term", "1997", "1998"], "style01");
gridView.setCellStyles([0, 1, 2, 3, 4, 5, 6], ["2000", "2001", "2002"], "style02");
```


셀들에 지정했던 모든 설정을 제거합니다.

<a class="btn primary small round lowercase" id="btnClearAllClickHandler">스타일 설정 초기화</a>

```js
gridView.clearCellStyles();
```

<script>
$('#btnAddCellStyles').click(function() {
    gridView.addCellStyle("style01", {
        "foreground": "#ffffffff",
        "background": "#ff333333",
        "fontSize": 13,
        "fontBold": true,
        "editable": false
    });
    gridView.addCellStyle("style02", {
        "foreground": "#ff000000",
        "background": "#ffcccccc",
        "fontSize": 13,
        "readOnly": true
    });
});

$('#btnSetCellStyles').click(function() {
    gridView.setCellStyles([0, 1, 2, 3, 4, 5, 6], ["term", "1997", "1998"], "style01");
    gridView.setCellStyles([0, 1, 2, 3, 4, 5, 6], ["2000", "2001", "2002"], "style02");
});


$('#btnClearAllClickHandler').click(function() {
    gridView.clearCellStyles();
});

</script>