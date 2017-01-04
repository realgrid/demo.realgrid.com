
#### 그리드에서 페이징 처리가 필요한가?

그리드를 사용하는 목적중 하나는 많은 양의 데이터를 스크롤하면서 조회하기 위한 것입니다. 그런데 왜? 그리드에서 페이지네이션을 구현해야 하는 걸까요?

> 고객의 요구에 의해 그리드에서도 페이지네이션을 구현할 필요가 있다면 RelaGrid가 가지고 있는 자체 페이지네이션 기능을 이용할 수 있습니다.

#### 현재 5000행, 10행씩 500페이지로 쪼개기

페이징 처리를 위해 [GridView.setPaging()](http://help.realgrid.com/api/GridView/setPaging/)함수를 이용합니다. 함수를 호출하면 DataProvider에 들어 있는 데이터를 페이지단위로 나누고 `첫 페이지 데이터`를 그리드에 표시 합니다.

<a class="btn primary small round lowercase" id="setPaging">페이징 처리</a>

```js
var page = -1;
var totalPage = -1;

gridView.setPaging(true, 10);

page = gridView.getPage();
totalPage = gridView.getPageCount();

$(".current-page-view").text(page);
$(".total-page-view").text(pageCount);
```

#### 현재 페이지는 <span class="current-page-view">????</span> / <span class="total-page-view">????</span>

페이지 정보를 가져오는 함수가 있습니다.

- [GridView.getPage()]() - 현재 페이지 번호 가져오기
- [GridView.getPageCount()]() - 전체 페이지 수 가져오기

<a class="btn primary small round lowercase" id="setPreviousPage">이전페이지</a>
 <span class="current-page-view">????</span> / <span class="total-page-view">????</span> <a class="btn primary small round lowercase" id="setNextPage">다음페이지</a>


```js
gridView.onPageChanged = function(grid, page) {
  $(".current-page-view").text(page);
}

gridView.onPageCountChanged = function(grid, pageCount) {
  $(".total-page-view").text(pageCount);
}
```

페이지가 변경될때 발행하는 이벤트도 있습니다.

- [GridView.onPageChanging()](http://help.realgrid.com/api/GridView/onPageChanging/) - 페이지가 바뀌기 전 호출
- [GridView.onPageChanged()](http://help.realgrid.com/api/GridView/onPageChanged/) - 페이지가 바뀐 다음 호출
- [GridView.onPageCountChanged()](http://help.realgrid.com/api/GridView/onPageCountChanged/) - 페이지 갯수가 바뀐 다음 호출

하지만, 이 이벤트들은 [GridView.setPaging()](http://help.realgrid.com/api/GridView/setPaging/)함수 호출시에는 발생하지 않습니다. 주의하세요.

```js
gridView.onPageChanged = function(grid, page) {
  $(".current-page-view").text(page);
}

gridView.onPageCountChanged = function(grid, pageCount) {
  $(".total-page-view").text(pageCount);
}
```

#### 페이지 이동 <span class="current-page-view">????</span> / <span class="total-page-view">????</span>

페이지를 이동하기 위한 함수는 [GridView.setPage()]() 입니다.

<a class="btn primary small round lowercase" id="setPage10">10</a>
<a class="btn primary small round lowercase" id="setPage100">100</a>
<a class="btn primary small round lowercase" id="setPage600">600</a>

RealGrid에서 페이징 처리시 page 번호는 모두 0부터 시작되는 숫자 입니다. 따라서 화면에 페이지 번호를 표시하기 위해서는 이점을 고려하여 1 을 더해 줄 필요가 있습니다.

```js
$('#setPage10').click(function() {
  gridView.setPage(9);
});

$('#setPage100').click(function() {
  gridView.setPage(99);
});

$('#setPage600').click(function() {
  gridView.setPage(599);
});
```


<script>
$('#setPaging').click(function() {
  var page = -1;
  var pageCount = -1;

  gridView.setPaging(true, 10);

  page = gridView.getPage();
  pageCount = gridView.getPageCount();

  $(".current-page-view").text(page);
  $(".total-page-view").text(pageCount);

  gridView.onPageChanged = function(grid, page) {
    $(".current-page-view").text(page);
  }
});

$('#setNextPage').click(function() {
  var currentPage = gridView.getPage();
  gridView.setPage(currentPage + 1);
});

$('#setPreviousPage').click(function() {
  var currentPage = gridView.getPage();
  gridView.setPage(currentPage - 1);
});

$('#setPage10').click(function() {
  gridView.setPage(9);
});

$('#setPage100').click(function() {
  gridView.setPage(99);
});

$('#setPage600').click(function() {
  gridView.setPage(599);
});

</script>
