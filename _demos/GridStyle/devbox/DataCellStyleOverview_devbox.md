#### DataCellStyle 설명

DataCellStyle은 아이템과 컬럼이 아니라 데이터행과 데이터필드를 기준으로 지정합니다.  
Sorting이나 Filtering 후에도 같은 데이터셀에 지정된 스타일은 유지됩니다.   
다만 스타일 자체는 그리드에서 보관하고, 데이터셀에 대한 스타일 지정 정보는 Item Model에서 보관합니다.  
또, DataCellStyle로 지정한 스타일은 기존의 컬럼 스타일 및 동적 스타일들이 적용된 후 마지막으로 적용됩니다.  
즉, DataCellStyle이 우선적으로 데이터셀 표시에 반영됩니다.


#### DataCellStyle 설정하기

 DataCellStyle은 id를 갖는 표시 스타일 속성들 및 편집 관련 속성들로 구성된 객체입니다.  
 이 스타일들을 GridBase.addCellStyle(id, style) 함수로 그리드에 미리 등록하고, GridBase.setCellStyles(dataRow, field, style) 함수로 특정한 데이터셀에 스타일을 지정합니다.

<a class="btn primary small round lowercase" id="btnAddCellStyles">스타일 추가하기</a>

```js
gridView.addCellStyles([{
    "id": "style1",
    "foreground": "#ffffffff",
    "background": "#ff333333",
    "fontSize": 14,
    "fontBold": true,
    "editable": false
}, {
    "id": "style2",
    "foreground": "#ffffff00",
    "background": "#ff111111",
    "fontSize": 16,
    "fontBold": true,
    "readOnly": false
}, {
    "id": "style3",
    "background": "#110000ff",
    "foreground": "#ff000088",
    "fontSize": 13,
    "fontBold": true,
    "textAlignment": "center"
}, {
    "id": "styleNew",
    "background": "#33ffff00"
}]);
```


<a class="btn primary small round lowercase" id="btnSetRowClickHandler">선택 행 전체 스타일 적용</a>

```js
gridView.addCellStyle("style01", {
    "background": "#4400ff00",
    "fontSize": 14,
    "paddingTop": 5
});
// field가 -1이면 행 전체 셀들에 대해 지정한다.
gridView.setCellStyles([1, 3], -1, "style01");
gridView.setCellStyles([7, 8], -1, "style2");
// row가 -1이면 추가 중인 행에 대해 적용된다.
gridView.setCellStyle(-1, -1, "styleNew");
```

<a class="btn primary small round lowercase" id="btnSetFieldClickHandler">개별 스타일 적용</a>

```js
gridView.addCellStyle("style02", {
    "paddingLeft": 15,
    "background": "#000000",
    "foreground": "#ffffff"
}, true);
gridView.setCellStyle(4, 1, "style02");
gridView.setCellStyle(4, 3, "style02");
gridView.setCellStyle(3, 2, "style02");
```

<a class="btn primary small round lowercase" id="btnSetRangeClickHandler">여러 셀 동시 적용</a>

```js
gridView.addCellStyle("style03", {
    "background": "#cc880000",
    "foreground": "#ffffff",
    "fontSize": 14
}, true);
gridView.setCellStyles([6,7,8,9], [2,3,4,5,6], "style03");
```


셀들에 지정했던 모든 설정을 제거합니다.

<a class="btn primary small round lowercase" id="btnClearAllClickHandler">스타일 설정 초기화</a>

```js
gridView.clearCellStyles();
```

<script>
$('#btnAddCellStyles').click(function() {
	gridView.addCellStyles([{
	    "id": "style1",
	    "foreground": "#ffffffff",
	    "background": "#ff333333",
	    "fontSize": 14,
	    "fontBold": true,
	    "editable": false
	}, {
	    "id": "style11",
	    "foreground": "#ffffff00",
	    "background": "#ff111111",
	    "fontSize": 16,
	    "fontBold": true,
	    "readOnly": false
	}, {
	    "id": "style2",
	    "background": "#110000ff",
	    "foreground": "#ff000088",
	    "fontSize": 13,
	    "fontBold": true,
	    "textAlignment": "center"
	}, {
	    "id": "styleNew",
	    "background": "#33ffff00"
	}]);
});

$('#btnSetRowClickHandler').click(function() {
	 gridView.addCellStyle("style01", {
        "background": "#4400ff00",
        "fontSize": 14,
        "paddingTop": 5
    });
    // field가 -1이면 행 전체 셀들에 대해 지정한다.
    gridView.setCellStyles([1, 3], -1, "style01");
    gridView.setCellStyles([7, 8], -1, "style2");
    // row가 -1이면 추가 중인 행에 대해 적용된다.
    gridView.setCellStyle(-1, -1, "styleNew");
});

$('#btnSetFieldClickHandler').click(function() {
	gridView.addCellStyle("style02", {
        "paddingLeft": 15,
        "background": "#000000",
        "foreground": "#ffffff"
    }, true);
    gridView.setCellStyle(4, 1, "style02");
    gridView.setCellStyle(4, 3, "style02");
    gridView.setCellStyle(3, 2, "style02");
});

$('#btnSetRangeClickHandler').click(function() {
	gridView.addCellStyle("style03", {
        "background": "#cc880000",
        "foreground": "#ffffff",
        "fontSize": 14
    }, true);
    gridView.setCellStyles([6,7,8,9], [2,3,4,5,6], "style03");
});


$('#btnClearAllClickHandler').click(function() {
	gridView.clearCellStyles();
});

</script>