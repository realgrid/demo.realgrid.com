#### 엑셀 내보내기

[exportGtrid()](http://help.realgrid.com/pivotApi/RealPivot/exportGrid/)함수로 지정한 설정에 따라 현재 pivot의 모양과 데이터를 외부 문서로 내보냅니다.

<a class="btn primary small round lowercase" id="btnExportGrid">export실행</a>

```
pivot.exportGrid({
    target: "local",
    fileName: "PivotExport.xlsx"
});
``` 


<script>
$('#btnExportGrid').click(function() {
    pivot.exportGrid({
        target: "local",
        fileName: "PivotExport.xlsx"
    });
});

</script>