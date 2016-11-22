
#### XML Data 구조

> 트리 구성을 위한 `필드`와 `컬럼`은 트리 아래 ToolBox 버튼을 눌러 확인해 보세요.

```js
var data =
  "<rows>"+
  "  <row icon='0' do='경기도'>"+
  "    <row icon='0' do='경기도' si='성남시'>"+
  "      <row icon='0' do='경기도' si='성남시' gu='분당구' />"+
  "      <row icon='0' do='경기도' si='성남시' gu='수정구'/>"+
  "    </row>"+
  "    <row icon='0' do='경기도' si='수원시'>"+
  "      <row icon='0' do='경기도' si='수원시' gu='팔달구' />"+
  "      <row icon='0' do='경기도' si='수원시' gu='영통구' />"+
  "    </row>"+
  "    <row icon='0' do='경기도' si='안양시' />"+
  "    <row icon='0' do='경기도' si='의정부시' />"+
  "    <row icon='0' do='경기도' si='김포시' />"+
  "  </row>"+
  "</rows>";
```
위 코드는 트리뷰(TreeView)에 계층 구조를 구현하기 위한 XML형식의 데이터 구조를 보여줍니다.

이 데이터 구조에서 주목할 부분은 `row`라는 이름의 노드(node 또는 엘리먼트 element)입니다.
이 노드는 트리의 계층구조를 표현하기 위한 엘리먼트 입니다.

이 엘리먼트의 이름은 [TreeDataProvider.setXmlRows()](http://help.realgrid.com/api/TreeDataProvider/setXmlRows/)함수에는
두 번째 인자인 `rowsProp`의 값으로 넘겨 주어야 하며,
[TreeDataProvider.fillXmlData()](http://help.realgrid.com/api/TreeDataProvider/fillXmlData/)함수에는
두 번째 인자인 `options` 즉 [DataFillOptions](http://help.realgrid.com/api/types/DataFillOptions/)의
`rows`속성의 값으로 넘겨 주어야 합니다.

함수를 호출하는 샘플 코드를 작성해 보겠습니다.

<a class="btn primary small round lowercase clearRows">데이터 지우기</a>
<a class="btn primary small round lowercase" id="setXmlRows">setXmlRows()로 트리 구현</a>

```js
// 데이터 지우기
treeDataProvider.clearRows();

// XML 데이터 입력하기
treeDataProvider.setXmlRows(data, "row", "", "icon");
treeView.expandAll();
```

<a class="btn primary small round lowercase clearRows">데이터 지우기</a>
<a class="btn primary small round lowercase" id="fillXmlData">fillXmlData()로 트리 구현</a>

```js
// 데이터 지우기
treeDataProvider.clearRows();

// XML 데이터 입력하기
treeDataProvider.fillXmlData(data, {rows: "row", icon: "icon"});
treeView.expandAll();
```

#### XML에서 계층 구조

XML의 노드는 반드시 시작 태그(start-tag)와 끝 태그(end-tag)가 쌍을 이루어야 합니다.
`부모 노드(parent)`의 시작 태그와 끝 태그 사이에 들어 있는 또 다른 노드는 `자식 노드(child)`를 의미하게 됩니다.

```xml
<parent>
  <child field=value>      <!-- 부모 노드 -->
    <child field=value />  <!-- 자식 노드 -->
    ...
    <child field=value />
  </child>
</parent>
```

위 XML 샘플 코드에서는 `field`가 노드의 속성(attribute)

[TreeDataProvider.setXmlRows()](http://help.realgrid.com/api/TreeDataProvider/setXmlRows/)함수는
이런 XML의 계층 구조를 그대로 트리뷰(TreeView)에 적용해 주는 함수입니다.

```js
function setXmlRows(xml, rowElement, childrenField, iconField) {}
```

이 함수의 두 번째 인자인 `rowElement`는 XML 데이터에서 계층 구조를 담고 있는 노드의 이름입니다.
이 데모에서는 `row`노드가 여기에 해당 됩니다.

RealGrid 튜토리얼에 계층 구조 표현을 위한 데이터 구조에 대해 좀더 자세히 다루고 있는 문서들이 있습니다. 아래 링크를 참조하세요.

  - [B9-1 배열형 트리 데이터 구조이해](http://help.realgrid.com/tutorial/b9-1/)
  - [B9-2 JSON형 트리 데이터 구조이해](http://help.realgrid.com/tutorial/b9-2/)
  - [B9-3 TreeView의 ItemModel 이해하기](http://help.realgrid.com/tutorial/b9-3/)

#### 트리에 아이콘 표시하기

트리뷰에는 각 노드에 아이콘을 표시할 수 있습니다.
[TreeDataProvider.setJsonRows()](http://help.realgrid.com/api/TreeDtaProvider/setJsonRows/)함수의 마지막 인자인 `iconProp`에는
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
var data =
  "<rows>"+
  "  <row icon='0' do='경기도'>"+
  "    <row icon='0' do='경기도' si='성남시'>"+
  "      <row icon='0' do='경기도' si='성남시' gu='분당구' />"+
  "      <row icon='0' do='경기도' si='성남시' gu='수정구'/>"+
  "    </row>"+
  "    <row icon='0' do='경기도' si='수원시'>"+
  "      <row icon='0' do='경기도' si='수원시' gu='팔달구' />"+
  "      <row icon='0' do='경기도' si='수원시' gu='영통구' />"+
  "    </row>"+
  "    <row icon='0' do='경기도' si='안양시' />"+
  "    <row icon='0' do='경기도' si='의정부시' />"+
  "    <row icon='0' do='경기도' si='김포시' />"+
  "  </row>"+
  "</rows>";

$('#setXmlRows').click(function() {
  treeDataProvider.setXmlRows(data, "row", "", "icon");
  treeView.expandAll();
});

$('#fillXmlData').click(function() {
  treeDataProvider.fillXmlData(data, {rows: "row", icon: "icon"});
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
