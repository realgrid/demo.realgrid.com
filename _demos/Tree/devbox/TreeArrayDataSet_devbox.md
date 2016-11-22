
#### Array Data 구조

[TreeDataProvider.setRows()](http://help.realgrid.com/api/TreeDataProvider/setRows/)함수에 넘겨줄 배열 데이터의 간단한 샘플을 작성해 보면 아래와 같습니다.
> 트리 구성을 위한 `필드`와 `컬럼`은 트리 아래 ToolBox 버튼을 눌러 확인해 보세요.

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

배열의 첫 번째 항목은 트리 노드에 표시될 `아이콘 인덱스(icon index)` 입니다.
두 번째 항목은 트리를 구성할 계층 구조을 담고 있는 `트리 코드(tree code)` 입니다.

우선, 위 데이터를 입력하기 위해 [TreeDataProvider.setRows()](http://help.realgrid.com/api/TreeDataProvider/setRows/)함수를 호출하는 샘플 코드를 작성해 보겠습니다.

<a class="btn primary small round lowercase clearRows">데이터 지우기</a>
<a class="btn primary small round lowercase" id="setRowsNeedSorting">배열형 데이터 정렬하여 입력하기</a>

```js
// 데이터 지우기
treeDataProvider.clearRows();

// 배열형 데이터 정렬하여 입력하기
treeDataProvider.setRows(data, "tree", true, "", "icon");
treeView.expandAll();
```

#### 계층구조 표현을 위한 treeField

[TreeDataProvider.setRows()](http://help.realgrid.com/api/TreeDataProvider/setRows/)함수의 정의는 아래와 같습니다.

```javascript
function setRows(rows, treeField, needSorting, childrenField, iconField) {}
```
이 함수의 두 번째 인자인 `treeField`는 데이터에서 트리 구조를 담고 있는 필드의 이름을 입력하는 인자입니다.
TreeView는 이 필드의 값으로 트리를 구성합니다.

> 하지만, 트리의 계층 구조가 바뀌어도 자동으로 이 필드의 값이 바뀌지는 않는다는 사실을 기억하세요.

RealGrid 튜토리얼에 계층 구조 표현을 위한 데이터 구조에 대해 좀더 자세히 다루고 있는 문서들이 있습니다. 아래 링크를 참조하세요.

  - [B9-1 배열형 트리 데이터 구조이해](http://help.realgrid.com/tutorial/b9-1/)
  - [B9-2 JSON형 트리 데이터 구조이해](http://help.realgrid.com/tutorial/b9-2/)
  - [B9-3 TreeView의 ItemModel 이해하기](http://help.realgrid.com/tutorial/b9-3/)

#### treeField값의 정렬

배열형 데이터를 입력할 때 주의할 점은 <mark>정렬되지 않은</mark> `treeField`값을 입력할 경우 정확한 계층 구조를 만들지 못할 수도 있다는 사실입니다.

위의 배열형 데이터를 다시 자세히 보면 일곱 번째 행에 있는 `성남시 수정구`의 경우 treeField 값이 순방향 정렬 순서에 맞지 않는 곳에 위치해 있습니다.

<a class="btn primary small round lowercase clearRows">데이터 지우기</a>
<a class="btn primary small round lowercase" id="setRowsNoSorting">배열형 데이터 정렬하지 않고 입력하기</a>

```js
// 데이터 지우기
treeDataProvider.clearRows();

// 배열형 데이터 정렬하지 않고 입력하기
treeDataProvider.setRows(data, "tree", false, "", "icon");
treeView.expandAll();
```

> 정렬되지 않은 배열 데이터를 입력할 경우 setRows() 함수의 로직으로 인해 원하는 계층 구조가 만들어 지지 않을 수 있습니다.
> 그러므로, 서버에서 데이터를 가져올때 미리 정렬을 하거나, `needSorting`인자를 `true`로 입력하여 트리를 구성하기 전에
> 반드시 `treeField`의 값을 정렬하도록 해야 합니다.


#### 트리에 아이콘 표시하기

TreeView에는 각 노드에 아이콘을 표시할 수 있습니다.
[TreeDataProvider.setRows()](http://help.realgrid.com/api/TreeDataProvider/setRows/)함수의 마지막 인자인 `iconField`에는
트리컬럼에 표시할 아이콘의 index값이 들어 있는 필드명을 입력합니다.

<a class="btn primary small round lowercase" id="setIcons">트리 아이콘 표시</a>

트리뷰에서 사용할 아이콘의 목록을 [ImageList](http://help.realgrid.com/api/features/Image%20List/)로 작성하고 만들어진 ImageList를
[TreeView.registerImageList()](http://help.realgrid.com/api/GridView/registerImageList/)함수로 TreeView에 등록하면 아이콘 필드에 입력된 index값에 해당 하는 아이콘에 트리노드에 표시됩니다.

```js
// 이미지 리스트 만들기
var imgFiles = [
              "kr.png",
              "br.png",
              "fr.png",
              "mx.png",
              "pt.png",
              "es.png",
              "gb.png",
              "us.png",
              "ve.png"
  ];
var imageList = new RealGridJS.ImageList("images", "{{"/resource/image/smallflag/" | prepend: site.baseurl}}");
imageList.addUrls(imgFiles);

// 트리뷰에 이미지 리스트 등록하기
treeView.registerImageList(imageList);
treeView.setTreeOptions({
    iconImages: imageList.getName(),
    iconWidth: 20
});
```


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

$('#setIcons').click(function() {
  var imgFiles = [
                "kr.png",
                "br.png",
                "fr.png",
                "mx.png",
                "pt.png",
                "es.png",
                "gb.png",
                "us.png",
                "ve.png"
    ];
  var imageList = new RealGridJS.ImageList("images", "{{"/resource/image/smallflag/" | prepend: site.baseurl}}");
  imageList.addUrls(imgFiles);

  treeView.registerImageList(imageList);

  treeView.setTreeOptions({
      iconImages: imageList.getName(),
      iconWidth: 20
  });
})



</script>
