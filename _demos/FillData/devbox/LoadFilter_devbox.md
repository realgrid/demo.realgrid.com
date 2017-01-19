
#### 전체 데이터

그리드에 표시된 데이터는 자동차별 판매 현황 목록이며 전체는 5,000행의 데이터입니다.


#### DataProvider수준 필터링

그리드에 불러올 전체 데이터 중 `브랜드명`이 `르노삼성`인 데이터를 필터링 하는 코드를 실행해 보겠습니다.

<a class="btn primary small round lowercase" id="setFilters1">르노삼성 필터링</a>

```js
var filters = [
  "value['brandName']='르노삼성'"
];

dataProvider.setFilters(filters);

$.ajax({
  url: "{{ "/resource/data/carData2.json" | prepend : site.baseurl }}",
  success: function(data) {
    dataProvider.fillJsonData(data);
  }
});
```
DataProvider에 데이터를 로드 할 때 조건에 맞는 데이터만 걸러서 가져오기 위한 필터링 기능은 [LocalDataProvider.setFilters()](http://help.realgrid.com/api/LocalDataProvider/setFilters/)함수를 통해 구현할 수 있습니다.

이 함수의 인자는

- `filters` - 필터 조건 목록을 배열로 입력합니다.
- `filterMode` - 필터 조건의 처리방법으로 `and` 또는 `or` 중 하나를 입력 합니다. 기본값은 `and`입니다.

이번에는 `filterMode`인자를 이용해 `르노삼성` 브랜드 중 `가격`이 `3천만원 미만`인 데이터를 필터링 하는 코드를 실행해 보겠습니다.

<a class="btn primary small round lowercase" id="setFilters2">르노삼성 브랜드중 3천만원 미만 필터링</a>

```js
var filters = [
  "value['brandName'] = '르노삼성'",
  "value['price'] < 3000"
];

dataProvider.setFilters(filters, "and");

$.ajax({
  url: "{{ "/resource/data/carData2.json" | prepend : site.baseurl }}",
  success: function(data) {
    dataProvider.fillJsonData(data);
  }
});
```

코드를 보면 아시겠지만, 이 방법은 실행 시점에 원격의 데이터를 모두 로컬로 내려받은 후 데이터를 필터링 하는 동작이기 때문에 특별한 경우가 아니라면 추천할 만한 방법이 아닙니다. 과도한 네트웍 리소스의 사용과 로컬에서의 성능상 문제가 생길 수도 있기 때문입니다.

하지만, 서버모듈의 수정없이 로컬단계의 데이터 필터링을 위한 방법으로 활용할 수 있습니다.

<script>
$('#setFilters1').click(function() {
  var filters = [
    "value['brandName']='르노삼성'"
  ];

  dataProvider.setFilters(filters);

  $.ajax({
    url: "{{ "/resource/data/carData2.json" | prepend : site.baseurl }}",
    success: function(data) {
      dataProvider.fillJsonData(data);
    }
  });
});

$('#setFilters2').click(function() {
  var filters = [
    "value['brandName'] = '르노삼성'",
    "value['price'] < 3000"
  ];

  dataProvider.setFilters(filters, "and");

  $.ajax({
    url: "{{ "/resource/data/carData2.json" | prepend : site.baseurl }}",
    success: function(data) {
      dataProvider.fillJsonData(data);
    }
  });
});
</script>
