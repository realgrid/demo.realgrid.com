**트리노드 펼치기(expand) & 접기(collapse)**

- [expandAll()](http://help.realgrid.com/api/TreeView/expandAll/): 모든 노드 펼치기
- [collapseAll()](http://help.realgrid.com/api/TreeView/collapseAll/): 모든 노드 접기
- [expand()](http://help.realgrid.com/api/TreeView/expand/): 선택 노드 펼치기
- [collapse()](http://help.realgrid.com/api/TreeView/collapse/): 선택 노드 접기

<a class="btn primary small round lowercase" id="expandAll">모두 펼치기</a>
<a class="btn primary small round lowercase" id="collapseAll">모두 접기</a>

```js
  //모두 펼치기
  treeView.expandAll();
  //모두 접기
  treeView.collapseAll();
```

<a class="btn primary small round lowercase" id="expandNode">선택 노드 펼치기</a>
<a class="btn primary small round lowercase" id="collapseNode">선택 노드 접기</a>

```js
  var current = treeView.getCurrent();
  var itemIndex = current.itemIndex;
  //모두 펼치기
  treeView.expand();
  //모두 접기
  treeView.collapse();
```

**선택된 노드의 자식 노드 개수**

<a class="btn primary small round lowercase" id="getChildCount">자식 노드 수</a>
<a class="btn primary small round lowercase" id="getDescendantCount">모든 자손 노드 수</a>

```js
  var current = treeView.getCurrent();
  var itemIndex = current.itemIndex;
  //모두 펼치기
  treeView.expand();
  //모두 접기
  treeView.collapse();
```

<script>
function getCurrent() {
  var curr = treeView.getCurrent();
     if (!curr) {
         alert('트리의 특정 행을 선택하세요.');
         return;
     }
     return curr;
}

$('#collapseAll').click(function() {
  treeView.collapseAll();
});

$('#expandAll').click(function() {
  treeView.expandAll();
});

$('#collapseNode').click(function() {
  var current = getCurrent();
  treeView.collapse(current.itemIndex);
});

$('#expandNode').click(function() {
  var current = getCurrent();
  treeView.expand(current.itemIndex);
});

$('#getChildCount').click(function() {
  var current = getCurrent();
  treeDataProvider.getChildCount(current.dataRow);
});
</script>
