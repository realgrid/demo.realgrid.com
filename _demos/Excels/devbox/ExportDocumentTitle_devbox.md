####  Excel문서에 제목 추가하기

[exportGrid()](http://help.realgrid.com/api/GridBase/exportGrid/) 함수를 사용해서 Excel 문서를 내려 받을 때
[GridExportOptions](http://help.realgrid.com/api/types/GridExportOptions/)의 *documentTitle*, *documentSubtitle*, *documentTail* 속성을 이용하여 Excel문서에 *제목*, *부제*, *꼬릿말*을 추가할 수 있습니다.

* documentTitle - 제목
* documentSubtitle - 부제
* documentTail - 꼬릿말

Title옵션의 세부 속성은 아래와 같습니다.

```js
GridExportOptions.documentTitle = {
    message: null,
    visible: true,
    styles: null,
    spaceTop: 0,    // 상단 여백
    spaceBottom: 0, // 하단 여백
    height: -1      // 엑셀의 행 높이
};
```

<a class="btn primary small round lowercase" id="btnExportGrid">Export실행</a>

**엑셀타입 설정**  
<input type="radio" name="excelType" value="2007"><label style="vertical-align: middle">MS Excel 2007 </label>&nbsp;&nbsp;&nbsp;&nbsp;
<input type="radio" name="excelType" value="2010" checked="checked"><label style="vertical-align: middle">MS Excel 2010 이상</label>

```js
var excelType = $(':radio[name="excelType"]:checked').val() == "2007";
gridView.exportGrid({
    type: "excel",
    target: "local",
    fileName: "gridExportSample.xlsx",
    compatibility: excelType,
    documentTitle: {  //제목
        message: "리얼그리드 제목1",
        visible: true,
        styles: {
            fontSize: 40,
            fontBold: true,
            textAlignment: "center",
            lineAlignment: "center",
            background: "#08f90000"
        },
        spaceTop: 1,
        spaceBottom: 0,
        height: 60
    },
    documentSubtitle: {  //부제
        message: "작성자 : 리얼그리드\n작성일 : " + today(),
        visible: true,
        styles: {
            textAlignment: "far",
            background: "#08f90000"
        },
        height: 60
    },
    documentTail: {  //꼬릿말
        message: "리얼그리드 꼬릿말",
        visible: true,
        styles: {
            fontSize: 12,
            fontBold: true,
            textAlignment: "center",
            background: "#080000f1"
        }
    }
});
```


<script>
$('#btnExportGrid').click(function() {
	var excelType = $(':radio[name="excelType"]:checked').val() == "2007";
    gridView.exportGrid({
        type: "excel",
        target: "local",
        fileName: "gridExportSample.xlsx",
        compatibility: excelType,
        documentTitle: {
            message: "리얼그리드 제목1",
            visible: true,
            styles: {
                fontSize: 40,
                fontBold: true,
                textAlignment: "center",
                lineAlignment: "center",
                background: "#08f90000"
            },
            spaceTop: 1,
            spaceBottom: 0,
            height: 60
        },
        documentSubtitle: {
            message: "작성자 : 리얼그리드\n작성일 : " + today(),
            visible: true,
            styles: {
                textAlignment: "far",
                background: "#08f90000"
            },
            height: 60
        },
        documentTail: {
            message: "리얼그리드 꼬릿말",
            visible: true,
            styles: {
                fontSize: 12,
                fontBold: true,
                textAlignment: "center",
                background: "#080000f1"
            }
        }
    });
});

function today() {
 
    var date = new Date();
 
    var year = date.getFullYear();
    var month = date.getMonth() + 1; // 0부터 시작하므로 1더함 더함
    var day = date.getDate();
 
    if (("" + month).length == 1) { month = "0" + month; }
    if (("" + day).length == 1) { day = "0" + day; }
 
    return (year + "-" + month + "-" + day);
 
}
</script>