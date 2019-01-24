#### 자동 필터링

필터 적용 버튼 클릭 시 `CustomerID` 컬럼에 `Filter`가 설정되며  
filter의 textBox에 `value` 값 입력하면 목록에서 검색이 됩니다.   
해당 filter값을 체크 후 `확인 버튼`을 클릭하면 선택된 값으로 필터링 합니다.     

자세한 사용 방법은 아래 링크를 참조하세요.
[http://help.realgrid.com/api/types/FilteringOptions/](http://help.realgrid.com/api/types/FilteringOptions/)

<a class="btn primary small round lowercase" id="btnSetFilters">필터 적용</a>
```js
//필터링 옵션 설정
gridView.setFilteringOptions({
  clearWhenSearchCheck:true, 
  selector: {
    showSearchInput: true,       
    showButtons:true,              
    acceptText: "확인",
    cancelText: "취소"
  }
});

//데이터로 필터 설정
var distinctValues = dataProvider.getDistinctValues("CustomerID");
var filters = [];
for(var i = 0; i < distinctValues.length; i++){
    filters.push({name:distinctValues[i],criteria:"value = " + "'" + distinctValues[i] + "'"});
}
gridView.setColumnFilters("CustomerID",filters);
```


<script>
var oldFilterColumn;
$("#btnSetFilters").click(function() { 
    gridView.setFilteringOptions({
      clearWhenSearchCheck:true, 
      selector: {
        showSearchInput: true,       
        showButtons:true,              
        acceptText: "확인",
        cancelText: "취소"
      }
    });

    var distinctValues = dataProvider.getDistinctValues("CustomerID");
    var filters = [];
    for(var i = 0; i < distinctValues.length; i++){
        filters.push({name:distinctValues[i],criteria:"value = " + "'" + distinctValues[i] + "'"});
    }
    gridView.setColumnFilters("CustomerID",filters);
});
</script>