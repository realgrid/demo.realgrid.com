#### Array 트리 데이터

아래 코드는 트리뷰(TreeView)를 구현하기 위한 Array 데이터 구조 입니다.

```js
var data = [
  [0, "1", "경기도"],
  [0, "1.1", "경기도", "성남시"],
  [0, "1.1.1", "경기도", "성남시", "분당구"],
  [0, "1.2", "경기도", "수원시"],
  [0, "1.2.2", "경기도", "수원시", "팔달구"],
  [0, "1.2.1", "경기도", "수원시", "영통구"],
  [0, "1.1.2", "경기도", "성남시", "수정구"],
  [0, "1.3", "경기도", "안양시"],
  [0, "1.4", "경기도", "의정부시"],
  [0, "1.5", "경기도", "김포시"]
]
```

<a class="btn primary small round lowercase" id="setRows">Array 트리 데이터</a>

```js
// setRows()함수로 트리 구현
treeDataProvider.setRows(data, "tree", false, "", "icon");
```

#### Array 데이터로 트리 구현

`Array 데이터`로 트리를 구현하기 위해서 아래 함수를 사용할 수 있습니다.

- [TreeDataProvider.setRows()](http://help.realgrid.com/api/TreeDataProvider/setRows/)

함수를 호출하는 샘플 코드를 작성해 보겠습니다.

데이터 입력시 정렬을 위해 함수의 `needSorting`인자를 `true`로 설정합니다.
정렬에 대한 자세한 설명은 아래 내용을 참고 하세요.

<a class="btn primary small round lowercase clearRows">데이터 지우기</a>
<a class="btn primary small round lowercase" id="setRowsNeedSorting">정렬하고 입력하기</a>

```js
// 데이터 지우기
treeDataProvider.clearRows();

// 배열형 데이터 정렬하여 입력하기
treeDataProvider.setRows(data, "tree", true, "", "icon");
treeView.expandAll();
```

데이터 입력시 정렬을 하지 않고 입력 하려면 `needSorting`인자를 `false`로 설정합니다.
정렬에 대한 자세한 설명은 아래 내용을 참고 하세요.

<a class="btn primary small round lowercase clearRows">데이터 지우기</a>
<a class="btn primary small round lowercase" id="setRowsNoSorting">정렬하지 않고 입력하기</a>

```js
// 데이터 지우기
treeDataProvider.clearRows();

// 배열형 데이터 정렬하지 않고 입력하기
treeDataProvider.setRows(data, "tree", false, "", "icon");
treeView.expandAll();
```

#### 트리 구현을 위한 Array 데이터 계층 구조

Array 데이터 계층 구조에서 주목할 부분은 `treeField` 입니다. `treeField`는 이 데모의 데이터에서
두 번째 항목에 해당하는 필드 입니다. 즉,

```js
'1'
'1.1'
'1.1.1'
...
```

`treeField`는 트리를 구성하기 위한 문자열이며 설명의 편의상 필드의 값을 `트리코드(tree code)`라 명명 하겠습니다.

`트리코드(tree code)`는 바로 전에 입력된 트리코드와 비교하여 `문자열의 포함 여부` 또는 `문자열의 갯수`를
기준으로 노드의 깊이(Level)를 판단 합니다. 트리코드에 대한 자세한 설명은
\[[B9-3 TreeView의 ItemModel 이해하기](http://help.realgrid.com/tutorial/b9-3/)\]를
참조하세요.

배열의 각 항목은 DataProvider에 구성된 필드(Field)들에 순서대로 매핑됩니다.

[TreeDataProvider.setRows()](http://help.realgrid.com/api/TreeDataProvider/setRows/)함수의 정의는 아래와 같습니다.

```javascript
function setRows(rows, treeField, needSorting, childrenField, iconField) {}
```

이 함수의 마지막 인자인 `iconField`에 데이터에서 `아이콘 인덱스(icon index)`에 해당하는 필드 이름을 넘겨줍니다.
이 함수의 두 번째 인자인 `treeField`에 데이터에서 트리코드에 해당하는 필드 이름을 넘겨줍니다.

> 하지만, 트리의 계층 구조가 바뀌어도 자동으로 이 필드의 값이 바뀌지는 않는다는 사실은 주의해야 합니다.

RealGrid 튜토리얼에 계층 구조 표현을 위한 데이터 구조에 대해 좀더 자세히 다루고 있는 문서들이 있습니다. 아래 링크를 참조하세요.

  - [B9-1 배열형 트리 데이터 구조이해](http://help.realgrid.com/tutorial/b9-1/)
  - [B9-2 JSON형 트리 데이터 구조이해](http://help.realgrid.com/tutorial/b9-2/)
  - [B9-3 TreeView의 ItemModel 이해하기](http://help.realgrid.com/tutorial/b9-3/)

#### treeField값의 정렬

배열형 데이터를 입력할 때 주의할 점은 <mark>정렬되지 않은</mark> `treeField`값을 입력할 경우 정확한 계층 구조를 만들지 못할 수도 있다는 사실입니다.

위의 배열형 데이터를 다시 자세히 보면 8행에 있는 `성남시 수정구`의 경우 treeField 값이 순방향 정렬 순서에 맞지 않는 곳에 위치해 있습니다.

이처럼 정렬되지 않은 배열 데이터를 입력할 경우 setRows() 함수의 로직으로 인해 원하는 계층 구조가 만들어 지지 않을 수 있습니다.
그러므로, 서버에서 데이터를 가져올때 미리 정렬을 하거나, `needSorting`인자를 `true`로 입력하여 트리를 구성하기 전에
반드시 `treeField`의 값을 정렬하도록 해야 합니다.

{% include_relative devbox/TreeIcon.md %}

{% comment %} ----------------- DEVBOX SCRIPT --------------- {% endcomment %}
<script>
  var data = [
      [0, "1", "경기도"],
      [0, "1.1", "경기도", "성남시"],
      [0, "1.1.1", "경기도", "성남시", "분당구"],
      [0, "1.2", "경기도", "수원시"],
      [0, "1.2.2", "경기도", "수원시", "팔달구"],
      [0, "1.2.1", "경기도", "수원시", "영통구"],
      [0, "1.1.2", "경기도", "성남시", "수정구"],
      [0, "1.3", "경기도", "안양시"],
      [0, "1.4", "경기도", "의정부시"],
      [0, "1.5", "경기도", "김포시"]
  ]

  $('#setRows').click(function() {
    treeDataProvider.setRows(data, "tree", true, "", "icon");
  });

  $('#setRowsNeedSorting').click(function() {
    treeDataProvider.setRows(data, "tree", true, "", "icon");
    treeView.expandAll();
  });

  $('#setRowsNoSorting').click(function() {
    treeDataProvider.setRows(data, "tree", false, "", "icon");
    treeView.expandAll();
  });

  $('.clearRows').click(function() {
    treeDataProvider.clearRows();
  });
</script>
