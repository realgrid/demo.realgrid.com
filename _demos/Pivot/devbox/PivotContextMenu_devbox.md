#### 피벗 컨텍스트 메뉴 설정

왼쪽 최상단에 위치한 버튼을 클릭할때 표시할 메뉴를 지정합니다.  
[http://help.realgrid.com/pivotApi/RealPivot/setContextMenu/](http://help.realgrid.com/pivotApi/RealPivot/setContextMenu/)

<a class="btn primary small round lowercase" id="btnSetContextMenu">컨텍스트 메뉴 적용</a>

```js
pivot.setContextMenu([{
    text: "버전확인",
    callback: function(){
        alert(pivot.getVersion())
    }
}, {
    text: "엑셀저장",
    callback: function(){
        pivot.exportGrid({
            target: "local",
            fileName: "RealPivotExport.xlsx",
            expandAll: true
        });
    }
}]);
```


<script>
$('#btnSetContextMenu').click(function() {
	pivot.setContextMenu([{
        text: "버전확인",
        callback: function(){
            alert(pivot.getVersion())
        }
    }, {
        text: "엑셀저장",
        callback: function(){
            pivot.exportGrid({
                target: "local",
                fileName: "RealPivotExport.xlsx",
                expandAll: true
            });
        }
    }]);
});
</script>