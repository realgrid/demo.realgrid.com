#### 트리노드 펼치기(expand) & 접기(collapse)

`TreeView`에는 트리 노드를 접고 펼치기 위한 함수들이 있습니다.

- [TreeView.expandAll()](http://help.realgrid.com/api/TreeView/expandAll/): 모든 노드 펼치기
- [TreeView.collapseAll()](http://help.realgrid.com/api/TreeView/collapseAll/): 모든 노드 접기

<a class="btn primary small round lowercase" id="expandAll">모두 펼치기</a>
<a class="btn primary small round lowercase" id="collapseAll">모두 접기</a>

```js
//모두 펼치기
treeView.expandAll();

//모두 접기
treeView.collapseAll();
```

선택된 노드에 대한 접기, 펼치기 기능을 실행해 보세요.

- [TreeView.expand()](http://help.realgrid.com/api/TreeView/expand/): 선택 노드 펼치기
  - 단축키: CTRL + LEFT (macOS: COMMAND + LEFT)
- [TreeView.collapse()](http://help.realgrid.com/api/TreeView/collapse/): 선택 노드 접기
  - 단축키: CTRL + RIGHT (macOS: COMMAND + RIGHT)

<a class="btn primary small round lowercase" id="expandNode">선택 노드 펼치기</a>
<a class="btn primary small round lowercase" id="collapseNode">선택 노드 접기</a>
<div class="checkbox">
  <label>
    <input type="checkbox" id="checkRecursive"> 모든 자식 노드에 적용(recursive)
  </label>
</div>
<div class="checkbox">
  <label>
    <input type="checkbox" id="checkForce"> 접혀있는 노드에 적용(force)
  </label>
</div>

```js
var current = treeView.getCurrent();
var recursive = document.getElementById("checkRecursive").checked;
var force = document.getElementById("checkForce").checked;

//선택 노드 펼치기
treeView.expand(current.itemIndex, recursive, force);

//선택 노드 접기
treeView.collapse(current.itemIndex, recursive);
```

#### 자식 노드 개수 가져오기

`TreeDataProvider`에는 특정 노드에서 자식노드의 개수를 확인할 수 있는 함수들 입니다.

- [TreeDataProvider.getChildCount()](http://help.realgrid.com/api/TreeDataProvider/getChildCount/): 모든 노드 펼치기
- [TreeDataProvider.getDescendantCount()](http://help.realgrid.com/api/TreeDataProvider/getDescendantCount/): 모든 노드 접기

<a class="btn primary small round lowercase" id="getChildCount">자식 노드 수</a>
<a class="btn primary small round lowercase" id="getDescendantCount">모든 자손 노드 수</a>

```js
var current = treeView.getCurrent();

//자식 노드 개수 가져오기
var childCount = treeDataProvider.getChildCount(current.dataRow);

//자식 및 모든 자손 노드의 개수 가져오기
var childCount = treeDataProvider.getDescendantCount(current.dataRow);
```

#### 자손 또는 조상 노드의 RowId 가져오기

선택한 노드의 자손 또는 조상 노드의 RowId를 배열로 가져올 수 있습니다.

- [TreeDataProvider.getDescendants()](http://help.realgrid.com/api/TreeDataProvider/getDescendants/): 자손 노드 RowId 가져오기
- [TreeDataProvider.getAncestors()](http://help.realgrid.com/api/TreeDataProvider/getAncestors/): 조상 노드 RowId 가져오기

<a class="btn primary small round lowercase" id="getDescendants">자손 노드 RowId 가져오기</a>
<a class="btn primary small round lowercase" id="getAncestors">조상 노드 RowId 가져오기</a>


```js
var current = treeView.getCurrent();

//자손 노드 RowId 가져오기
var descendants = treeDataProvider.getDescendants(current.dataRow);

//조상 노드 RowId 가져오기
var ancestors = treeDataProvider.getAncestors(current.dataRow);
```

#### 노드의 순서를 위/아래로 이동하기

동일한 형제들 사이에서 특정 노드를 위/아래로 움직일 수 있습니다.

- [TreeDataProvider.moveRowSibling()](http://help.realgrid.com/api/TreeDataProvider/moveRowSibling/): 노드를 위/아래로 이동하기

<a class="btn primary small round lowercase" id="moveRowSiblingUp">노드를 한 줄 위로 이동하기</a>
<a class="btn primary small round lowercase" id="moveRowSiblingDown">노드를 한 줄 아래로 이동하기</a>


```js
var current = treeView.getCurrent();

//노드를 한 줄 위로 이동하기
treeDataProvider.moveRowSibling(current.dataRow, -1);
treeView.setCurrent({dataRow: current.dataRow});

//노드를 한 줄 아래로 이동하기
treeDataProvider.moveRowSibling(current.dataRow, +1);
treeView.setCurrent({dataRow: current.dataRow});
```

#### 노드를 다른 노드의 자식으로 이동하기

왼쪽 그리드에서 `브라질의 상파울루`노드를 `아르헨티나`의 하위 노드로 이동할 수 있습니다.

- [TreeDataProvider.changeRowParent()](http://help.realgrid.com/api/TreeDataProvider/changeRowParent/): 노드를 위/아래로 이동하기

<a class="btn primary small round lowercase" id="prepareChangeRowParent">준비</a>

아래 코드는 변화를 잘 볼 수 있도록 모든 노드를 접고, 브라질과 아르헨티나 노드만 펼칩니다.

```js
//일단 모두 접기
treeView.collapseAll();
//브라질(ItemIndex = 1) 노드 펼치기
treeView.expand(1, true);
//아르헨티나 노드(ItemIndex = 0) 펼치기
treeView.expand(0);
```

[TreeDataProvider.changeRowParent()](http://help.realgrid.com/api/TreeDataProvider/changeRowParent/)함수를 사용하려면 이동할 노드와 목적 노드의 RowId를 알아야 합니다.
보통은 [GridBase.getCurrent()](http://help.realgrid.com/api/GridBase/getCurrent/)함수를 통해 [RowId](http://help.realgrid.com/tutorial/a9/)를 가져오지만 여기서는 실습을 위해 미리 정해진 RowId를 사용합니다.

- 브라질 하위 상파울루의 `RowId`는 `10`입니다.
- 아르헨티나의 `RowId`는 `1`입니다.

<a class="btn primary small round lowercase" id="changeRowParent">브라질의 상파울루를 아르헨티나 두 번째 하위로 이동</a>

```js
// 상파울루(RowId = 10)를 아르헨티나(RowId = 1) 하위 두 번째 노드(index = 1)로 이동하기
treeDataProvider.changeRowParent(10, 1, 1);
//상파울루노드(RowId = 10)에 포커스 이동하기
treeView.setCurrent({dataRow: 10});
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

//모두 접기
$('#collapseAll').click(function() {
  treeView.collapseAll();
});

//모두 펼치기
$('#expandAll').click(function() {
  treeView.expandAll();
});

//선택 노드 접기
$('#collapseNode').click(function() {
  var current = getCurrent();
  var recursive = document.getElementById("checkRecursive").checked;
  treeView.collapse(current.itemIndex, recursive);
});

//선택 노드 펼치기
$('#expandNode').click(function() {
  var current = getCurrent();
  var recursive = document.getElementById("checkRecursive").checked;
  var force = document.getElementById("checkForce").checked;
  treeView.expand(current.itemIndex, recursive, force);
});

//자식 노드 개수 가져오기
$('#getChildCount').click(function() {
  var current = getCurrent();
  var childCount = treeDataProvider.getChildCount(current.dataRow);
  alert(childCount);
});

//자식 및 모든 자손 노드의 개수 가져오기
$('#getDescendantCount').click(function() {
  var current = getCurrent();
  var childCount = treeDataProvider.getDescendantCount(current.dataRow);
  alert(childCount);
});

//자손 노드 RowId 가져오기
$('#getDescendants').click(function() {
  var current = getCurrent();
  var descendants = treeDataProvider.getDescendants(current.dataRow);
  alert(descendants);
});

//조상 노드 RowId 가져오기
$('#getAncestors').click(function() {
  var current = getCurrent();
  var ancestors = treeDataProvider.getAncestors(current.dataRow);
  alert(ancestors);
});

//노드를 한 줄 위로 이동하기
$('#moveRowSiblingUp').click(function() {
  var current = getCurrent();
  treeDataProvider.moveRowSibling(current.dataRow, -1);
  treeView.setCurrent({dataRow: current.dataRow});
});

//노드를 한 줄 아래로 이동하기
$('#moveRowSiblingDown').click(function() {
  var current = getCurrent();
  treeDataProvider.moveRowSibling(current.dataRow, 1);
  treeView.setCurrent({dataRow: current.dataRow});
});

$('#prepareChangeRowParent').click(function() {
  //일단 모두 접기
  treeView.collapseAll();
  //브라질(ItemIndex = 1) 노드 펼치기
  treeView.expand(1, true);
  //아르헨티나(ItemIndex = 0) 노드 펼치기
  treeView.expand(0);
});

//브라질의 상파울루를 아르헨티나 노드 하위로 이동하기
$('#changeRowParent').click(function() {
  //일단 모두 접기
  treeView.collapseAll();
  //브라질(ItemIndex = 1) 노드 펼치기
  treeView.expand(1, true);
  //아르헨티나(ItemIndex = 0) 노드 펼치기
  treeView.expand(0);

  //상파울루를 아르헨티나 하위 두 번째 노드로 이동하기
  treeDataProvider.changeRowParent(10, 1, 1);
  //상파울루노드(RowId = 10)에 포커스 이동하기
  treeView.setCurrent({dataRow: 10});
});

</script>
