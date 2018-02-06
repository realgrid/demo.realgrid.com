#### 피벗 컨텍스트 메뉴 설정

피벗 데이터 로드 시 진행 상태를 표시합니다.

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
        pivot.exportGrid();
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
            pivot.exportGrid();
        }
    }]);
});
</script>