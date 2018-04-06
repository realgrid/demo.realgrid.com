#### exportToCsv 내보내기 `(Only JS Support)`


<a class="btn primary small round lowercase" id="exportToCsv">exportToCsv 실행</a>

```js
dataProvider.exportToCsv({
    target: "local",
    fileName: "ExportSample.csv",
    exportFields:['OrderID','CustomerID','EmployeeID','OrderDate'],
    includeFieldNames:true
});
```

#### exportToCsv 내보내기 옵션

[GridExportOptions](http://help.realgrid.com/api/DataProvider/exportToCsv/) 화면에 표시되는 그리드를 데이터프로바이더 수준에서 엑셀 등의 외부 문서로 내보기할 때 지정하는 설정 모델을 확인할 수 있습니다.


<script>
    $('#exportToCsv').click(function() {
        dataProvider.exportToCsv({
		    target: "local",
		    fileName: "ExportSample.csv",
		    exportFields:['OrderID','CustomerID','EmployeeID','OrderDate'],
		    includeFieldNames:true
		});
    });
</script>