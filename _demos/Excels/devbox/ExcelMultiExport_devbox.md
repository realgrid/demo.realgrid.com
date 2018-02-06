#### 다중 그리드 Excel 내보내기

excel export시 2개 이상의 그리드를 파일 옵션은 공통으로 설정하며 exportGrids 속성으로 각 시트를 설정합니다.

<a class="btn primary small round lowercase" id="btnExportGrid">Export실행</a>

**엑셀타입 설정**  
<input type="radio" name="excelType" value="2007"><label style="vertical-align: middle">MS Excel 2007 </label>&nbsp;&nbsp;&nbsp;&nbsp;
<input type="radio" name="excelType" value="2010" checked="checked"><label style="vertical-align: middle">MS Excel 2010 이상</label>

```js
RealGridJS.exportGrid({
  type:"excel",
  target:"local",
  fileName:"multiExport.xlsx",
  compatibility: excelType,
  done:function() {
  	alert("done excel export")
  },
  exportGrids:[
    { 
        grid:gridView, //그리드 변수명
        sheetName:"sheetName" // 다른 그리드와 중복되어서는 안된다.
    }, {
        grid:gridView2,
        sheetName:"sheetName2"
    }
  ]
});
```

#### export 내보내기 옵션

[GridExportOptions](http://help.realgrid.com/api/types/GridExportOptions/) API문서에서 화면에 표시되는 그리드를 엑셀 등의 외부 문서로 내보내기할 때 지정하는 설정 모델을 확인할 수 있습니다.


<script>
$('#btnExportGrid').click(function() {
	var excelType = $(':radio[name="excelType"]:checked').val() == "2007";


	RealGridJS.exportGrid({
        type:"excel",
        target:"local",
        fileName:"multiExport.xlsx",
        compatibility: excelType,
        done:function() {
        	alert("done excel export")
        },
        exportGrids:[
        { grid:gridView,
          sheetName:"sheetName" // 다른 그리드와 중복되어서는 안된다.
        },
        {grid:gridView2,
         sheetName:"sheetName2"
        }
      ]
    });

});
</script>