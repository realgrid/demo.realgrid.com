
#### 마지막행까지 스크롤 되면 다음 데이터 불러오기

그리드의 맨 마지막 행까지 스크롤될 때 호출되는 [GridBase.onScrollToBottom()](http://help.realgrid.com/api/GridBase/onScrollToBottom/) 콜백 함수를 이용해 Lazy Loading을 구현 할 수 있습니다.

<a class="btn primary small round lowercase" id="onScrollToBottom">마지막행까지 스크롤될 때 다음 데이터 읽어오기</a>

```js
function loadNext() {
  var newStart = dataProvider.getRowCount();
  $.ajax({
    url: "{{ "/resource/data/carData2.json" | prepend : site.baseurl }}",
    success: function(data) {
      dataProvider.fillJsonData(data,
        {fillMode: "append", start: newStart, count: 100});
    }
  });
}

gridView.onScrollToBottom = function() {
  loadNext();
}
```

#### 50개 행이 스크롤될때 마다 데이터 불러오기

그리드에는 스크롤을 감지 할 수 있는 또 다른 이벤트가 있습니다.  [GridBase.onTopItemIndexChanged()](http://help.realgrid.com/api/GridBase/onTopItemIndexChanged/)함수는 그리드가 세로방향으로 스크롤될대 호출되는 콜백함수이며 그리드의 최 상단 ItemIndex를 인자로 들려줍니다.

이 함수를 이용해 50개 행이 스크롤될때 마다 다음 데이터를 미리 읽어 오도록 구현해 보겠습니다.

<a class="btn primary small round lowercase" id="onTopItemIndexChanged">스크롤시 50행 지날때 마다 데이터 읽어오기</a>

```js
function loadNext() {
  var newStart = dataProvider.getRowCount();
  $.ajax({
    url: "{{ "/resource/data/carData2.json" | prepend : site.baseurl }}",
    success: function(data) {
      dataProvider.fillJsonData(data,
        {fillMode: "append", start: newStart, count: 100});
    }
  });
}

var scrollItem = 0;

gridView.onTopItemIndexChanged = function(grid, item) {
  if (item > scrollItem) {
    scrollItem += 50;
    loadNext();
  }
}
```

<script>
function loadNext() {
  var newStart = dataProvider.getRowCount();
  $.ajax({
    url: "{{ "/resource/data/carData2.json" | prepend : site.baseurl }}",
    success: function(data) {
      dataProvider.fillJsonData(data, {fillMode: "append", start: newStart, count: 100});
    }
  });
}

$('#onScrollToBottom').click(function() {
  gridView.onScrollToBottom = function(grid) {
    loadNext();
  }
});

var scrollItem = 0;

$('#onTopItemIndexChanged').click(function() {
  gridView.onTopItemIndexChanged = function(grid, item) {
    if (item > scrollItem) {
      scrollItem += 50;
      console.log(scrollItem);
      loadNext();
    }
  }
});
</script>
