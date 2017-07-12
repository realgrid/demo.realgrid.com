#### TreeView Excel 내보내기

[exportGrid()](http://help.realgrid.com/api/GridBase/exportGrid/)함수로 지정한 설정에 따라 현재 그리드의 모양과 데이터를 외부 문서로 내보냅니다.

<a class="btn primary small round lowercase" id="btnExportGrid">Export실행</a>

**엑셀타입 설정**  
<input type="radio" name="excelType" value="2007"><label style="vertical-align: middle">MS Excel 2007 </label>&nbsp;&nbsp;&nbsp;&nbsp;
<input type="radio" name="excelType" value="2010" checked="checked"><label style="vertical-align: middle">MS Excel 2010 이상</label>

**감춰진 행 출력 여부**   
<input type="checkbox" id="chkAllItems"> <label style="vertical-align: middle">All Items</label>

#### 영역 표시 방법 설정

*indicator*  
<input type="radio" name="indicator" value="default" checked="checked"><label style="vertical-align: middle">default</label>&nbsp;&nbsp;&nbsp;&nbsp;
<input type="radio" name="indicator" value="visible"><label style="vertical-align: middle">visible</label>&nbsp;&nbsp;&nbsp;&nbsp;
<input type="radio" name="indicator" value="hidden"><label style="vertical-align: middle">hidden</label>

*header*   
<input type="radio" name="header" value="default" checked="checked"><label style="vertical-align: middle">default</label>&nbsp;&nbsp;&nbsp;&nbsp;
<input type="radio" name="header" value="visible"><label style="vertical-align: middle">visible</label>&nbsp;&nbsp;&nbsp;&nbsp;
<input type="radio" name="header" value="hidden"><label style="vertical-align: middle">hidden</label>

*footer*  
<input type="radio" name="footer" value="default" checked="checked"><label style="vertical-align: middle">default</label>&nbsp;&nbsp;&nbsp;&nbsp;
<input type="radio" name="footer" value="visible"><label style="vertical-align: middle">visible</label>&nbsp;&nbsp;&nbsp;&nbsp;
<input type="radio" name="footer" value="hidden"><label style="vertical-align: middle">hidden</label>


```js
var excelType = $(':radio[name="excelType"]:checked').val() == "2007";
var indicator = $(':radio[name="indicator"]:checked').val();
var header = $(':radio[name="header"]:checked').val();
var footer = $(':radio[name="footer"]:checked').val();
var allItems = $("#chkAllItems").is(":checked");

treeView.exportGrid({
    type: "excel",
    target: "local",
    fileName: "gridExportSample.xlsx",
    indicator: indicator,
    header: header,
    footer: footer,
    allItems: allItems,
    compatibility: excelType,
    done: function () {  //내보내기 완료 후 실행되는 함수
        alert("done excel export")
    }
});
```

#### export 내보내기 옵션

[GridExportOptions](http://help.realgrid.com/api/types/GridExportOptions/) API문서에서 화면에 표시되는 그리드를 엑셀 등의 외부 문서로 내보내기할 때 지정하는 설정 모델을 확인할 수 있습니다.



<script>
$('#btnExportGrid').click(function() {
	var excelType = $(':radio[name="excelType"]:checked').val() == "2007";
	var indicator = $(':radio[name="indicator"]:checked').val();
	var header = $(':radio[name="header"]:checked').val();
	var footer = $(':radio[name="footer"]:checked').val();
	var allItems = $("#chkAllItems").is(":checked");

	treeView.exportGrid({
	    type: "excel",
	    target: "local",
	    fileName: "gridExportSample.xlsx",
	    indicator: indicator,
	    header: header,
	    footer: footer,
	    allItems: allItems,
	    compatibility: excelType,
	    done: function () {  //내보내기 완료 후 실행되는 함수
	        alert("done excel export")
	    }
	});
});
</script>