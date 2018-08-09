#### 피벗 컨텍스트 메뉴 설정

왼쪽 최상단에 위치한 버튼을 클릭할때 표시할 메뉴를 [setGlobalContextMenu()](http://help.realgrid.com/pivotApi/RealPivot/setContextMenu/) 함수로 지정합니다.  

<a class="btn primary small round lowercase" id="btnSetGlobalContextMenu">컨텍스트 메뉴 적용</a>

```js
pivot.setGlobalContextMenu([{
    text: "엑셀저장",
    callback: function(){
        pivot.exportGrid({
            type: "excel",
            target: "local",
            fileName: "RealPivotExport.xlsx"
        });
    }
}])
```

왼쪽 최상단에 위치한 버튼을 영역을 제외한 나머지 영역에 우클릭 시 표시할 메뉴를 [setContextMenu()](http://help.realgrid.com/pivotApi/RealPivot/setContextMenu/) 함수로 지정합니다.  

<a class="btn primary small round lowercase" id="btnSetContextMenu">컨텍스트 메뉴 적용</a>

```js
pivot.setContextMenu([{
    text: "엑셀저장",
    callback: function(){
        pivot.exportGrid({
            type: "excel",
            target: "local",
            fileName: "RealPivotExport.xlsx"
        });
    }
}])
```


<script>
$('#btnSetContextMenu').click(function() {
	pivot.setContextMenu([{
        text: "엑셀저장",
        callback: function(){
            pivot.exportGrid({
                type: "excel",
                target: "local",
                fileName: "RealPivotExport.xlsx"
            });
        }
    }]);
});

$('#btnSetGlobalContextMenu').click(function() {
    pivot.setGlobalContextMenu([{
        text: "엑셀저장",
        callback: function(){
            pivot.exportGrid({
                type: "excel",
                target: "local",
                fileName: "RealPivotExport.xlsx"
            });
        }
    }])
});

</script>