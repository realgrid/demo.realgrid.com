
#### JSON Data 구조

JSON 데이터를 이용해 트리뷰를 구현하기 위해서 아래 두 함수를 사용할 수 있습니다.

- [TreeDataProvider.setJsonRows()](http://help.realgrid.com/api/TreeDataProvider/setJsonRows/)
- [TreeDataProvider.fillJsonData()](http://help.realgrid.com/api/TreeDataProvider/fillJsonData/)

아래 코드는 트리뷰(TreeView)를 구현하기 위한 JSON형식의 데이터 구조를 보여줍니다.

```js
var data = {
  "rows":[
    { "icon":0, "do":"경기도",
      "rows":[
        { "icon":0, "do":"경기도", "si":"성남시",
          "rows":[
            { "icon":0, "do":"경기도", "si":"성남시", "gu":"분당구" },
            { "icon":0, "do":"경기도", "si":"성남시", "gu":"수정구" }
          ]
        },
        { "icon":0, "do":"경기도", "si":"수원시",
          "rows":[
            { "icon":0, "do":"경기도", "si":"수원시", "gu":"팔달구" },
            { "icon":0, "do":"경기도", "si":"수원시", "gu":"영통구" }
          ]
        },
        { "icon":0, "do":"경기도", "si":"안양시" },
        { "icon":0, "do":"경기도", "si":"의정부시" },
        { "icon":0, "do":"경기도", "si":"김포시" }
      ]
    }
  ]
}
```

> 트리 구성을 위한 `필드`와 `컬럼`은 트리 아래 ToolBox 버튼을 눌러 확인해 보세요.

이 데이터 구조에서 주목할 부분은 `rows`라는 이름의 배열 속성 입니다.
이 속성은 트리의 계층구조를 표현하기 위한 속성명 입니다.
보다 자세한 내용은 아래 `JSON에서 계층 구조` 부분을 참조하세요.

먼저 [setJsonRows()](http://help.realgrid.com/api/TreeDataProvider/setJsonRows/)
함수를 호출하여 트리를 구현해 보겠습니다.

<a class="btn primary small round lowercase clearRows">데이터 지우기</a>
<a class="btn primary small round lowercase" id="setJsonRows">setJsonRows()로 트리 구현</a>

```js
// 데이터 지우기
treeDataProvider.clearRows();

// JSON 데이터 입력하기
treeDataProvider.setJsonRows(data, "rows", "", "icon");
treeView.expandAll();
```

같은 데이터를 [fillJsonData()](http://help.realgrid.com/api/TreeDataProvider/fillJsonData/)
함수를 사용해 트리를 구현해 보겠습니다.

<a class="btn primary small round lowercase clearRows">데이터 지우기</a>
<a class="btn primary small round lowercase" id="fillJsonData">fillJsonData()로 트리 구현</a>

```js
// 데이터 지우기
treeDataProvider.clearRows();

// JSON 데이터 입력하기
treeDataProvider.fillJsonData(data, {rows: "rows", icon: "icon"});
treeView.expandAll();
```
각 함수의 API페이지로 이동해 구현 방법의 차이를 확인해 보세요.

#### JSON에서 계층 구조

트리를 구현하기 위한 JSON 데이터의 구조에 대해 조금 더 알아보겠습니다.

위 JSON 데이터에서 `rows` 속성은 자식 노드를 위한 속성입니다. 즉, JSON 에서 계층 구조는
계층을 표현하기 위한 속성(여기서는 `rows`)에 하위 노드의 데이터를 배열로 넣어주면 됩니다.

이 속성명은 JSON데이터로 트리를 구현하기 위한 각 함수의 인자로 넘겨주어야 합니다.

아래는 [TreeDataProvider.setJsonRows()](http://help.realgrid.com/api/TreeDataProvider/setJsonRows/)함수의 정의 입니다.

```js
function setJsonRows(json, rowsProp, childrenProp, iconProp) {}
```

위 속성명인 `'rows'`는 이 함수의 두 번째 인자인 `rowsProp`의 값으로 넘겨 주어야 합니다.


다음은 [TreeDataProvider.fillJsonData()](http://help.realgrid.com/api/TreeDataProvider/fillJsonData/)함수의 정의 입니다.

```js
function fillJsonData(data, options) {}
```

두 번째 인자인 `options` 즉 [DataFillOptions](http://help.realgrid.com/api/types/DataFillOptions/)의
`rows`속성의 값으로 위 속성명인 `'rows'`를 넘겨 주어야 합니다.

일반적으로 SQL을 통해 데이터를 쿼리하는 방식으로 계층 데이터를 만들어내는 것은 쉽지 않습니다. 하지만,
JSON 데이터가 가지는 계층 구조를 직접 트리뷰 구현에 사용할 수 있기 때문에 <mark>NoSQL,
Document방식의 데이터를 트리뷰에 표현하기 위해 이 보다 좋은 방법은 없습니다.</mark>

RealGrid 튜토리얼에 계층 구조 표현을 위한 데이터 구조에 대해 좀더 자세히 다루고 있는 문서들이 있습니다. 아래 링크를 참조하세요.

  - [B9-1 배열형 트리 데이터 구조이해](http://help.realgrid.com/tutorial/b9-1/)
  - [B9-2 JSON형 트리 데이터 구조이해](http://help.realgrid.com/tutorial/b9-2/)
  - [B9-3 TreeView의 ItemModel 이해하기](http://help.realgrid.com/tutorial/b9-3/)

#### 트리에 아이콘 표시하기

트리뷰에는 각 노드에 아이콘을 표시할 수 있습니다. 트리를 구성하기 위한 위 함수의 `iconProp`인자.
또는, [DataFillOptions](http://help.realgrid.com/api/types/DataFillOptions/)의 `icon`
속성의 값에 아이콘의 index값이 들어 있는 필드명을 입력합니다. 이 샘플 데이터에서는 아이콘 필드명은 `icon`입니다.

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
var data = {
  "rows":[
    { "icon":0, "do":"경기도",
      "rows":[
        { "icon":0, "do":"경기도", "si":"성남시",
          "rows":[
            { "icon":0, "do":"경기도", "si":"성남시", "gu":"분당구" },
            { "icon":0, "do":"경기도", "si":"성남시", "gu":"수정구" }
          ]
        },
        { "icon":0, "do":"경기도", "si":"수원시",
          "rows":[
            { "icon":0, "do":"경기도", "si":"수원시", "gu":"팔달구" },
            { "icon":0, "do":"경기도", "si":"수원시", "gu":"영통구" }
          ]
        },
        { "icon":0, "do":"경기도", "si":"안양시" },
        { "icon":0, "do":"경기도", "si":"의정부시" },
        { "icon":0, "do":"경기도", "si":"김포시" }
      ]
    }
  ]
}

$('#setJsonRows').click(function() {
  treeDataProvider.setJsonRows(data, "rows", "", "icon");
  treeView.expandAll();
});

$('#fillJsonData').click(function() {
  treeDataProvider.fillJsonData(data, {rows:"rows", icon:"icon"});
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
