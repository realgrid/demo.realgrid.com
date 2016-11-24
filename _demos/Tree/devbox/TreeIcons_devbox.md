
#### RealGrid의 Image List

그리드뷰(GridView) 또는 트리뷰(TreeView)에서 이미지를 사용하려면 먼저,
[ImageList](http://help.realgrid.com/api/types/ImageList/)객체를 이용해 이미지파일의
경로를 목록으로 만들어야 합니다.

```js
var imageList = new RealGridJS.ImageList("images", "/demo/resource/image/smallflag/");
    imageList.addUrls([
                "icon_male.png",
                "icon_female.png",
                "de.png",
                "gr.png",
                "hu.png",
                "is.png",
                ...
        ]
    );
 
treeView.registerImageList(imageList);
treeView.setTreeOptions({
    iconImages: imageList.getName(),
    iconWidth: 20
});
```
위 코드는 실제로 왼쪽 데모 화면에서 트리뷰(TreeView)에 아이콘을 적용하기 위해 이미지 목록을 만들고
트리에 등록하는 코드입니다.
이미지 목록을 트리에 등록하고 사용하려면

- [GridBase.registerImageList()](http://help.realgrid.com/api/GridView/registerImageList/)
- [TreeView.setTreeOptions()](http://help.realgrid.com/api/GridView/registerImageList/)

함수를 사용하면 됩니다.

#### 트리에 아이콘 표시하기

트리뷰(TreeView)에는 각 노드에 아이콘을 표시할 수 있습니다.

아래 트리 구현 함수들에서는 함수의 마지막 인자인 `iconField`에 트리컬럼에 표시할 아이콘의 index값이
들어 있는 필드명을 입력합니다. 이 필드에 들어있는 값이 트리노드의 기본 아이콘 인덱스(icon index)가 됩니다.

- [TreeDataProvider.setRows()](http://help.realgrid.com/api/TreeDataProvider/setRows/)
- [TreeDataProvider.setJsonRows()](http://help.realgrid.com/api/TreeDataProvider/setJsonRows/)
- [TreeDataProvider.setXmlRows()](http://help.realgrid.com/api/TreeDataProvider/setJsonRows/)

또 다른 트리 구현 함수인 아래 함수들에서는 두 번째 인자인 `options`
즉, [DataFillOptions](http://help.realgrid.com/api/types/DataFillOptions/)의
`rows`속성의 값으로 위 속성명인 `'rows'`를 넘겨 주어야 합니다.

- [TreeDataProvider.fillJsonData()](http://help.realgrid.com/api/TreeDataProvider/fillJsonData/)
- [TreeDataProvider.fillXmlData()](http://help.realgrid.com/api/TreeDataProvider/fillXmlData/)
- [TreeDataProvider.fillCsvData()](http://help.realgrid.com/api/TreeDataProvider/fillCsvData/)


<a class="btn primary small round lowercase" id="setIcons">트리 아이콘 표시</a>

트리뷰에서 사용할 아이콘의 목록을 [ImageList](http://help.realgrid.com/api/features/Image%20List/)로 작성하고 만들어진 ImageList를
[TreeView.registerImageList()](http://help.realgrid.com/api/GridView/registerImageList/)함수로
TreeView에 등록하면 아이콘 필드에 입력된 index값에 해당 하는 아이콘에 트리노드에 표시됩니다.

```js
// 이미지 리스트 만들기
var imageList = new RealGridJS.ImageList("images", "/demo/resource/image/smallflag/");
    imageList.addUrls([
                "icon_male.png",
                "icon_female.png",
                "icon_folder_col.png",
                "icon_folder-exp.png",
                "de.png",
                "gr.png",
                "hu.png",
                "is.png",
                ...
        ]
    );
 
// 트리뷰에 이미지 리스트 등록하기
treeView.registerImageList(imageList);
treeView.setTreeOptions({
    iconImages: imageList.getName(),
    iconWidth: 20
});
```

#### 트리 노드 아이콘 변경 하기

트리 노드의 `아이콘 인덱스(icon index)`를 가져오고 지정하기 위해

- [TreeDataProvider.getIconIndex()](http://help.realgrid.com/api/TreeDataProvider/getIconIndex/)
- [TreeDataProvider.setIconIndex()](http://help.realgrid.com/api/TreeDataProvider/setIconIndex/)

함수를 사용합니다.

<a class="btn primary small round lowercase" id="setIconIndex">현재 노드의 아이콘 변경하기</a>

```js
// 현재 노드의 아이콘을 2 또는 3으로 변경하기
var current = treeView.getCurrent();
if (current && current.dataRow) {
  var iidx = treeDataProvider.getIconIndex(current.dataRow);
  if (iidx == 2) {
    treeDataProvider.setIconIndex(current.dataRow, 3);
  } else {
    treeDataProvider.setIconIndex(current.dataRow, 2);
  }
}
```

#### 트리를 접거나 펼칠때 아이콘 바꾸기

트리를 접거나 펼칠때 아이콘을 변경하기 위해 아래 두 이벤트를 사용할 수 있습니다.

- [TreeView.onTreeItemExpanded()](http://help.realgrid.com/api/TreeView/onTreeItemExpanded/): 노드가 펼쳐진 다음 호출
- [TreeView.onTreeItemCollapsed()](http://help.realgrid.com/api/TreeView/onTreeItemCollapsed/): 노드가 접힌 다음 호출

위 콜백 함수를 이용해 트리 노드를 접거나 펼칠때 폴더 모양의 아이콘을 변경하는 코드를 실행해 보세요.

<a class="btn primary small round lowercase" id="setDynamicIconIndex">노드를 접고 펼칠 때 아이콘 변경</a>

```js
// 노드를 펼칠때 아이콘 인덱스를 3으로 변경
treeView.onTreeItemExpanded = function (tree, itemIndex, rowId) {
  var level = treeDataProvider.getLevel(rowId);
  if (level == 2) {
    treeDataProvider.setIconIndex(rowId, 3);
  }
}

// 노드를 접을때 아이콘 인덱스를 2로 변경
treeView.onTreeItemCollapsed = function (tree, itemIndex, rowId) {
  var level = treeDataProvider.getLevel(rowId);
  if (level == 2) {
    treeDataProvider.setIconIndex(rowId, 2);
  }
}
```

<script>
  $('#setIcons').click(function() {
    var imageList = new RealGridJS.ImageList("images", "{{"/resource/image/smallflag/" | prepend: site.baseurl}}");
    imageList.addUrls([
                "icon_male.png",
                "icon_female.png",
                "icon_folder_col.png",
                "icon_folder_exp.png",
                "de.png",
                "gr.png",
                "hu.png",
                "is.png",
                "eg.png",
                "au.png",
                "nz.png",
                "ph.png",
                "sg.png",
                "th.png",
                "tr.png",
                "ca.png",
                "mx.png",
                "us.png",
                "bo.png",
                "cr.png",
                "pe.png",
                "uy.png"
        ]
    );
 
    treeView.registerImageList(imageList);
    treeView.setTreeOptions({
        iconImages: imageList.getName(),
        iconWidth: 20
    });
  });

  $('#setIconIndex').click(function() {
    var current = treeView.getCurrent();
    if (current && current.dataRow) {
      var iidx = treeDataProvider.getIconIndex(current.dataRow);
      if (iidx == 3) {
        treeDataProvider.setIconIndex(current.dataRow, 2);
      } else {
        treeDataProvider.setIconIndex(current.dataRow, 3);
      }
    }
  });

  $('#setDynamicIconIndex').click(function() {
    treeView.onTreeItemCollapsed = function (tree, itemIndex, rowId) {
      var level = treeDataProvider.getLevel(rowId);
      if (level == 2) {
        treeDataProvider.setIconIndex(rowId, 2);
      }
    }

    treeView.onTreeItemExpanded = function (tree, itemIndex, rowId) {
      var level = treeDataProvider.getLevel(rowId);
      if (level == 2) {
        treeDataProvider.setIconIndex(rowId, 3);
      }
    }
  });

</script>
