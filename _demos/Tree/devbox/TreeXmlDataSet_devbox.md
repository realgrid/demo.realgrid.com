
#### XML 데이터 구조

아래 코드는 트리를 구현하기 위한 JSON형식의 데이터 입니다.

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

#### XML 데이터로 트리 구현

`XML 데이터`로 트리를 구현하기 위해 아래 두 함수를 사용할 수 있습니다.

- [TreeDataProvider.setXmlRows()](http://help.realgrid.com/api/TreeDataProvider/setXmlRows/)
- [TreeDataProvider.fillXmlData()](http://help.realgrid.com/api/TreeDataProvider/fillXmlData/)

먼저 [setXmlRows()](http://help.realgrid.com/api/TreeDataProvider/setXmlRows/)
함수를 호출하여 트리를 구현해 보겠습니다.

<a class="btn primary small round lowercase clearRows">데이터 지우기</a>
<a class="btn primary small round lowercase" id="setXmlRows">setXmlRows()로 트리 구현</a>

```js
// XML 데이터 입력하기
treeDataProvider.setXmlRows(data, "row", "", "icon");
treeView.expandAll();
```

같은 데이터를 [fillXmlData()](http://help.realgrid.com/api/TreeDataProvider/fillXmlData/)
함수를 사용해 트리를 구현해 보겠습니다.

<a class="btn primary small round lowercase clearRows">데이터 지우기</a>
<a class="btn primary small round lowercase" id="fillXmlData">fillXmlData()로 트리 구현</a>

```js
// 데이터 지우기
treeDataProvider.clearRows();

// XML 데이터 입력하기
treeDataProvider.fillXmlData(data, {rows: "row", icon: "icon"});
treeView.expandAll();
```

두 함수의 실행 결과는 동일 합니다.

#### 트리 구현을 위한 XML데이터의 계층 구조

XML의 노드는 반드시 시작 태그(start-tag)와 끝 태그(end-tag)가 쌍을 이루어야 합니다.

```xml
<rows>
  <row field=value>      <!-- 부모 노드 -->
    <row field=value />  <!-- 자식 노드 -->
    ...
    <row field=value />
  </row>
</rows>
```

`부모 노드(위에서 rows tag)`의 시작 태그와 끝 태그 사이에 들어 있는 또 다른 노드는 `자식 노드(위에서 row tag)`를 의미하게 됩니다.

이 데모의 데이터에서 주목할 부분은 `row`라는 이름의 `노드(node 또는 엘리먼트 element)`입니다.
이 노드는 트리의 계층구조를 표현하기 위한 `엘리먼트(element)` 입니다.

아래는 [TreeDataProvider.setXmlRows()](http://help.realgrid.com/api/TreeDataProvider/setXmlRows/)함수의 정의 입니다.
위 속성명인 `'rows'`는 이 함수의 두 번째 인자인 `rowsElement`의 값으로 넘겨 주어야

```js
function setXmlRows(xml, rowElement, childrenField, iconField) {}
```

아래는 [TreeDataProvider.fillXmlData()](http://help.realgrid.com/api/TreeDataProvider/fillXmlData/)함수의 정의 입니다.
두 번째 인자인 `options` 즉 [DataFillOptions](http://help.realgrid.com/api/types/DataFillOptions/)의
`rows`속성의 값으로 위 속성명인 `'rows'`를 넘겨 주어야 합니다.

```js
function fillXmlData(data, options) {}
```

RealGrid 튜토리얼에 계층 구조 표현을 위한 데이터 구조에 대해 좀더 자세히 다루고 있는 문서들이 있습니다. 아래 링크를 참조하세요.

  - [B9-1 배열형 트리 데이터 구조이해](http://help.realgrid.com/tutorial/b9-1/)
  - [B9-2 JSON형 트리 데이터 구조이해](http://help.realgrid.com/tutorial/b9-2/)
  - [B9-3 TreeView의 ItemModel 이해하기](http://help.realgrid.com/tutorial/b9-3/)

{% include_relative devbox/TreeIcon.md %}

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
</script>
