#### 트리노드 펼치기(expand) & 접기(collapse)

`TreeView`에는 트리 노드를 접고 펼치기 위한 함수들이 있습니다.

- [TreeView.expandAll()](http://help.realgrid.com/api/TreeView/expandAll/): 모든 노드 펼치기
- [TreeView.collapseAll()](http://help.realgrid.com/api/TreeView/collapseAll/): 모든 노드 접기
- [TreeView.expand()](http://help.realgrid.com/api/TreeView/expand/): 선택 노드 펼치기
- [TreeView.collapse()](http://help.realgrid.com/api/TreeView/collapse/): 선택 노드 접기

버튼을 눌러 해당 기능을 실습해 보세요.

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
<div class="checkbox">
  <label>
    <input type="checkbox" id="chkRecursive"> 모든 자식 노드에 적용(recursive)
  </label>
</div>
<div class="checkbox">
  <label>
    <input type="checkbox" id="chkRecursive"> 접혀있는 노드에 적용(force)
  </label>
</div>

```js
var current = treeView.getCurrent();
//선택 노드 펼치기
treeView.expand(current.itemIndex);
//선택 노드 접기
treeView.collapse(current.itemIndex);
```

#### 선택된 노드의 자식 노드 개수

`TreeDataProvider`에는 특정 노드에서 자식노드의 개수를 확인할 수 있는 함수들 입니다.

- [TreeDataProvider.getChildCount()](http://help.realgrid.com/api/TreeDataProvider/getChildCount/): 모든 노드 펼치기
- [TreeDataProvider.getDescendantCount()](http://help.realgrid.com/api/TreeDataProvider/getDescendantCount/): 모든 노드 접기

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

{% comment %} ---------------
  여기서 부터 실제 실행 코드
------------- {% endcomment %}
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
  var recursive = document.getElementById("chkRecursive").checked;
  treeView.collapse(current.itemIndex, recursive);
});

$('#expandNode').click(function() {
  var current = getCurrent();
  var recursive = document.getElementById("chkRecursive").checked;
  treeView.expand(current.itemIndex, recursive, true);
});

$('#getChildCount').click(function() {
  var current = getCurrent();
  var childCount = treeDataProvider.getChildCount(current.dataRow);
  alert(childCount);
});

$('#getDescendantCount').click(function() {
  var current = getCurrent();
  var childCount = treeDataProvider.getDescendantCount(current.dataRow);
  alert(childCount);
});

</script>
