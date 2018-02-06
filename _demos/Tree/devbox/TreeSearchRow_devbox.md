#### 특정 데이터 노드 검색

tree를 펼치는 것은 해당 아래와 같이 dataRowId를 찾은후 부모를 찾고 tree에서 펼쳐주는 방식으로 해야합니다.

버튼 클릭 시 ["col1","col2"] 필드에 해당하는 값중에서 "SPECD" 데이터를 검색합니다.

<a class="btn primary small round lowercase" id="btnSearchData">"SPECD" 검색</a>

```js
var ret = treeDataProvider.searchData({fields:["col1","col2"], value:"SPECD", wrap:true});
if (ret) {
    var rowId = ret.dataRow;
    var parents = treeDataProvider.getAncestors(rowId);
    if (parents) {
        for (var i = parents.length - 1; i >= 0 ; i--) {
            treeView.expand(treeView.getItemIndex(parents[i]));
        }
        treeView.setCurrent({itemIndex:treeView.getItemIndex(rowId), fieldIndex:ret.fieldIndex})
    }
}
```

<script>
  $('#btnSearchData').click(function() {
    var ret = treeDataProvider.searchData({fields:["col1","col2"], value:"SPECD", wrap:true});
	if (ret) {
	    var rowId = ret.dataRow;
	    var parents = treeDataProvider.getAncestors(rowId);
	    if (parents) {
	        for (var i = parents.length - 1; i >= 0 ; i--) {
	            treeView.expand(treeView.getItemIndex(parents[i]));
	        }
	        treeView.setCurrent({itemIndex:treeView.getItemIndex(rowId), fieldIndex:ret.fieldIndex})
	    }
	}
  });

</script>