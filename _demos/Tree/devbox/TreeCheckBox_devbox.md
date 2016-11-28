
#### 체크바(CheckBar)와 체크박스(CheckBox)

트리에서 [체크바(CheckBar)]({{ '/GridComponent/CheckBar/' | prepend: site.baseurl }})와 체크박스가 어떻게 다른지 확인해 보겠습니다.

이 기능을 위해

- [GridBase.setCheckBar()](http://help.realgrid.com/api/GridBase/setCheckBar/)
- [TreeView.setTreeOptions()](http://help.realgrid.com/api/TreeView/setTreeOptions/)

함수를 사용합니다.

<a class="btn primary small round lowercase" id="setCheckBar">체크바 보이기/감추기</a>
<a class="btn primary small round lowercase" id="setCheckBox">체크박스 보이기/감추기</a>

```js
// 체크바 보이기/감추기
var checkBar = treeView.getCheckBar();
checkBar.visible = !checkBar.visible;
treeView.setCheckBar(checkBar);

// 체크박스 보이기/감추기
var treeOptions = treeView.getTreeOptions();
treeView.setTreeOptions(
  {
    showCheckBox: !treeOptions.showCheckBox
  }
);
```

체크바와 체크박스는 표시되는 위치만 다를뿐 동일한 기능입니다. 체크바와 체크박스를 모두 보이게 한 다음
한 쪽을 체크/언체크 하면 동일하게 동작되는 것을 확인 할 수 있습니다.

또, 라디오버튼(Radio Button)처럼 단일 행 또는 노드를 선택하게 할 수도 있습니다.

<a class="btn primary small round lowercase" id="setRadioButton">라디오 버튼 보이기/감추기</a>

```js
// 라디오 버튼 보이기/감추기
var checkBar = treeView.getCheckBar();
checkBar.exclusive = !checkBar.exclusive;
treeView.setCheckBar(checkBar);
```

#### 체크된 행 가져오기

체크된 행의 [ItemIndex 또는 RowId](http://help.realgrid.com/tutorial/a11/)를 가져오기 위해

- [TreeView.getCheckedItems()](http://help.realgrid.com/api/TreeView/getCheckedItems/)
- [TreeView.getCheckedRows()](http://help.realgrid.com/api/TreeView/getCheckedRows/)

함수를 사용합니다.

<a class="btn primary small round lowercase" id="getCheckedItems">체크된 ItemIndex 배열</a>
<a class="btn primary small round lowercase" id="getCheckedRows">체크된 RowId 배열</a>

```js
// 체크된 ItemIndex 배열 가져오기
var checkedItems = treeView.getCheckedItems();
alert(checkedItems);

// 체크된 RowId 배열 가져오기
var checkedRows = treeView.getCheckedRows();
alert(checkedRows);
```

#### 체크 또는 언체크

그리드뷰(GridView) 트리뷰(TreeView)에는 체크, 언체크를 위한 함수들이 있습니다.

- [checkAll()](http://help.realgrid.com/api/GridBase/checkAll/)
- [checkItem()](http://help.realgrid.com/api/GridBase/checkItem/)
- [checkItems()](http://help.realgrid.com/api/GridBase/checkItems/)
- [checkRow()](http://help.realgrid.com/api/GridBase/checkRow/)
- [checkRows()](http://help.realgrid.com/api/GridBase/checkRows/)

또, 하위 노드들을 체크, 언체크하기 위한 트리뷰(TreeView)만의 함수도 있습니다.

- [TreeView.checkChildren()](http://help.realgrid.com/api/TreeView/checkChildren/)

위 함수들의 다양한 인자들을 조합하면 다음과 같은 조건의 체크가 가능합니다.

> 구분 컬럼이 `남자`인 노드의 모든 하위 노드를 체크 하라! 이때, 접혀서 보이지 않는 노드까지 모두 포함해서 체크하라.

<a class="btn primary small round lowercase" id="checkSample1">'남자'의 모든 하위노드 체크</a>

```js
// 최초 그리드뷰에서 '남자' 노드의 ItemIndex는 `0`입니다.
treeView.checkChildren(0, true, true, false);
```

#### 체크 여부

특정 행 또는 노드의 체크여부를 확인하기 위해

- [TreeView.isCheckedItem()](http://help.realgrid.com/api/TreeView/isCheckedItem/)
- [TreeView.isCheckedRow()](http://help.realgrid.com/api/TreeView/isCheckedRow/)

함수를 사용합니다.

<a class="btn primary small round lowercase" id="isCheckedItem">'아시아'노드가 체크되었는가?</a>

```js
// 최초 그리드뷰에서 구분이 '아시아' 노드의 ItemIndex는 `1`입니다.
var isCheckedItem = treeView.isCheckedItem(1);
alert(isCheckedItem);
```


<script>
  $('#setCheckBar').click(function() {
    var checkBar = treeView.getCheckBar();
    checkBar.visible = !checkBar.visible;
    treeView.setCheckBar(checkBar);
  });

  $('#setRadioButton').click(function() {
    var checkBar = treeView.getCheckBar();
    checkBar.exclusive = !checkBar.exclusive;
    treeView.setCheckBar(checkBar);
  });

  $('#setCheckBox').click(function() {
    var treeOptions = treeView.getTreeOptions();
    treeView.setTreeOptions({showCheckBox: !treeOptions.showCheckBox});
  });

  $('#getCheckedItems').click(function() {
    var checkedItems = treeView.getCheckedItems();
    alert(checkedItems);
  });

  $('#getCheckedRows').click(function() {
    var checkedRows = treeView.getCheckedRows();
    alert(checkedRows);
  });

  $('#checkSample1').click(function() {
    treeView.checkChildren(0, true, true, false);
  });

  $('#isCheckedItem').click(function() {
    var isCheckedItem = treeView.isCheckedItem(1);
    alert(isCheckedItem);
  });
</script>
