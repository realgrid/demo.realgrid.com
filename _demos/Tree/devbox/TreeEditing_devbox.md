
#### 추가

트리는 그리드와 달리 새로운 행을 추가하는 것이 아닌 새로운 자식 노드를 추가하는 개념입니다. 자식 노드를
추가하는 함수는

- [TreeDataProvider.addChildRow()](http://help.realgrid.com/api/TreeDataProvider/addChildRow/)
- [TreeDataProvider.insertChildRow()](http://help.realgrid.com/api/TreeDataProvider/insertChildRow/)

입니다.

자식을 추가하는 개념이기 때문에 부모 노드의 RowId가 필요합니다. 그렇기 때문에, 두 함수의 첫 번째 인자는 모두 부모 노드의 RowId 입니다.

트리뷰(TreeView)에는 암묵적인 최상위(Root) 노드가 존재 합니다. 암묵적인 최상위 노드의 RowId는 -1 입니다. 즉, 최상위에 노드를 추가할 경우 함수의 첫 번째 인자에 -1을 입력하면 됩니다.

<a class="btn primary small round lowercase" id="addChildRow">최상위 노드 추가</a>

```js
// 최상위 노드에 행 추가
treeDataProvider.addChildRow(
  -1,     // parent rowId
  [3, "최상위 노드"],
  3,      // icon index
  false   // children(자식 보유 여부)
);
```

자식 노드가 여러개인 경우, 자식 노드들은 `순서(index)`를 가지고 있습니다. 따라서, 자식노드를 추가할 때 특정 순서의 위치에 추가하고 싶다면 [insertChildRow()](http://help.realgrid.com/api/TreeDataProvider/insertChildRow/) 함수를 호출 하면서 두 번째 인자에 자식 노드의 index를 입력합니다.

<a class="btn primary small round lowercase" id="insertChildRow">'아시아'의 세 번째 자식 노드 추가</a>

```js
// '아시아'의 세 번째 자식 노드 추가
treeDataProvider.insertChildRow(
  2,      // parent rowId
  2,      // child index
  [8, "세번째 자식 노드"],
  8,      // icon index
  false   // children(자식 보유 여부)
);
```


#### 수정

트리에서 수정 기능은 그리드와 동일 합니다. 아래 두 함수를 이용해 행의 데이터를 수정 할 수 있습니다.

- [DataProvider.updateRow()](http://help.realgrid.com/api/DataProvider/updateRow/)
- [DataProvider.updateStrictRow()](http://help.realgrid.com/api/DataProvider/updateStrictRow/)

<a class="btn primary small round lowercase" id="updateRow">'일본'을 'Japan'으로 수정</a>
<a class="btn primary small round lowercase" id="updateStrictRow">'마카오'를 '홍콩'으로 수정</a>

```js
// '일본'을 'Japan'으로 수정, '일본'의 rowId=3
reeDataProvider.updateRow(3, [0, "Japan"]);

// '마카오'를 '홍콩'으로 수정, '마카오'의 rowId=4
treeDataProvider.updateStrictRow(4, {Col0: "홍콩"});
```

#### 삭제

트리에서 삭제 기능은 그리드와 거의 동일 합니다. 단, 자식 노드가 있는 경우 부모 노드의 삭제와 동시에 자식 노드도 삭제 처리 됩니다.

삭제와 관련된 몇 가지 옵션이 있습니다.

- [DataProviderOptions.deletable](http://help.realgrid.com/api/types/DataProviderOptions/): 키보드를 통한 삭제 가능 여부
- [DataProviderOptions.softDeleting](http://help.realgrid.com/api/types/DataProviderOptions/): 삭제시 상태만 변경할 것인지 여부
- [EditOptions.deletable](http://help.realgrid.com/api/types/EditOptions/): 삭제 여부
- [EditOptions.deleteRowsConfirm](http://help.realgrid.com/api/types/EditOptions/): 삭제시 확인 메시지 여부

트리의 삭제 기능 구현을 위한 함수는 다음과 같습니다.

- [DataProvider.clearRows()](http://help.realgrid.com/api/DataProvider/clearRows/)
- [GridBase.deleteSelection()](http://help.realgrid.com/api/GridBase/deleteSelection/)
- [TreeDataProvider.removeRow()](http://help.realgrid.com/api/TreeDataProvider/removeRow/)
- [TreeDataProvider.removeRows()](http://help.realgrid.com/api/TreeDataProvider/removeRows/)

이중 `removeRow()` 함수를 사용해서 샘플코드를 작성해 보겠습니다.

<a class="btn primary small round lowercase" id="removeRow">removeRow()함수로 '아시아' 지우기</a>

부모가 삭제되면 자식도 모두 삭제됩니다.

```js
// rowId=2인 '아시아' 삭제
treeDataProvider.removeRow(2);
```

#### 단축 키보드(Short-Cut Key)

트리의 편집을 위한 단축키 기능이 있습니다. 일부는 그리드뷰(GridView)와 동일한 기능도 있고 트리뷰(TreeView)만을 위해 추가된 기능도 있습니다.

**추가**
- 키보드를 통한 삽입 기능은 [EditOptions.instable](http://help.realgrid.com/api/types/EditOptions/)이 `true`여야 합니다.
- `Insert`키는 현재 행 앞에 같은 레벨의 행을 추가합니다.
- `Shift + Insert`키는 현재 행 뒤에 같은 레벨의 행을 추가합니다.
- `Ctrl + Insert`키는 현재 행의 자식 행을 끝에 추가합니다. 현재 행이 leaf인 경우 [EditOptions.appendable](http://help.realgrid.com/api/types/EditOptions/)도 `true`여야 합니다.
- `아래 화살표`: 빈 트리나 표시되는 마지막 행에서 아래 화살표 키를 누르면 최상위 행을 추가합니다.

**수정**
- 편집 가능한 임의의 셀에서 키보드를 통해 입력을 시작하면 바로 편집상태가 됩니다.
- [EditOptions.updatable](http://help.realgrid.com/api/types/EditOptions/)이 `true`여야 합니다.

**삭제**
- `Ctrl+Delete` 키를 누르면 선택된 행들을 삭제합니다.
- [EditOptions.deletable](http://help.realgrid.com/api/types/EditOptions/)이 `true`여야 합니다.

<script>
  $('#addChildRow').click(function() {
    treeDataProvider.addChildRow(-1, [3, "최상위 노드"], 3, false);
  });

  $('#insertChildRow').click(function() {
    treeDataProvider.insertChildRow(2, 2, [8, "세번째 자식 노드"], 8, false);
  });

  $('#updateRow').click(function() {
    treeDataProvider.updateRow(3, [3, "Japan"]);
  });

  $('#updateStrictRow').click(function() {
    treeDataProvider.updateStrictRow(4, {Col0: "홍콩"});
  });

  $('#removeRow').click(function() {
    treeDataProvider.removeRow(2);
  });

</script>
