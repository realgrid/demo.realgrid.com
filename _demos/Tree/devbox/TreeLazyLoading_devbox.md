#### 트리 펼칠때 자식 데이터 가져오기

트리뷰(TreeView)에서 Lazy Loading(지연된 로드, 레지 로딩)은 트리 노드가 펼쳐질때 비동기 방식으로 데이터를 가져와 자식 노드에 추가하는 방식으로 구현할 수 있습니다.

이 데모에서 자식 노드는 jQuery ajax()함수로 원격의 데이터를 비동기 방식으로 가져옵니다.

트리 노드가 펼쳐질때 호출해 주는 콜백 함수는

- [TreeView.onTreeItemExpanding()](http://help.realgrid.com/api/TreeView/onTreeItemExpanding/)

입니다.

이벤트가 호출되는 시점에 원격 데이터를 가지고와서 트리의 자식노드로 추가합니다. 콜백함수에서 `true`를
리턴하면 펼치는 동작을 완료하고 `false`를 리턴하면 펼치기를 취소합니다.

<a class="btn primary small round lowercase" id="setExpandingEvent">트리 펼쳐질때 자식 노드로 데이터 추가</a>

```js
// onTreeItemExpanding 이벤트에서 자식 노드 추가
treeView.onTreeItemExpanding = function (tree, itemIndex, rowId) {
  // expanding 중인 행이 자식이 하나도 없다면 hasChildren이 설정된 행이다.
  // 자식들을 가져와 그 행에 추가한다.
  if (treeDataProvider.getChildCount(rowId) <= 0) {
    $.ajax({
      type: "GET",
      url: "http://" + location.host + "{{'/resource/data/' | prepend: site.baseurl}}treedata5.txt?__time__=" + new Date().getTime(),
      dataType: "text",
      success: function (data) {
        treeDataProvider.fillCsvData(data,
          {
            append: true,
            parent: rowId,
            children: "childrenField",
            tree: "tree",
            icon: "icon",
            quoted: true,
            start: 0
          }
        );
        treeView.setFocus();
      },
      error: function (xhr, status, error) {
        alert(error);
      }
    });
  }
  return true;
};
```

참고로, 트리가 접힐때 호출되는 콜백 함수는

- [TreeView.onTreeItemCollapsing()](http://help.realgrid.com/api/TreeView/onTreeItemCollapsing/)

입니다.

<script>
  $('#setExpandingEvent').click(function() {
    // onTreeItemExpanding 이벤트에서 자식 노드 추가
    treeView.onTreeItemExpanding = function (tree, itemIndex, rowId) {
      // expanding 중인 행이 자식이 하나도 없다면 hasChildren이 설정된 행이다.
      // 자식들을 가져와 그 행에 추가한다.
      if (treeDataProvider.getChildCount(rowId) <= 0) {
        $.ajax({
          type: "GET",
          url: "http://" + location.host + "{{'/resource/data/' | prepend: site.baseurl}}treedata5.1.txt?__time__=" + new Date().getTime(),
          dataType: "text",
          success: function (data) {
            treeDataProvider.fillCsvData(data,
              {
                append: true,
                parent: rowId,
                children: "childrenField",
                tree: "tree",
                icon: "icon",
                quoted: true,
                start: 0
              }
            );
            treeView.setFocus();
          },
          error: function (xhr, status, error) {
            alert(error);
          }
        });
      }
      return true;
    };
  });
</script>
