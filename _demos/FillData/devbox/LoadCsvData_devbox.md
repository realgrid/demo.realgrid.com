#### CSV 데이터    

콤마(comma)로 구분된 CSV 데이터를 RealGrid의 DataProvider에 입력하기 위해서는 [LocalDataProvider.fillCsvData()](http://help.realgrid.com/api/LocalDataProvider/fillCsvData/)함수는 이용할 수 있습니다. CSV 데이터의 행과 행을 구분하기 위헤 CR, LF, CRLF 중 하나가 포함되어 있어야 합니다.

<a class="btn primary small round lowercase" id="fillCsvData1">CSV 데이터 로드</a>

```js
var data = '\
국산,국산,2,기아,15,더 뉴 K9,9,미드나이트 블랙,2016/01/01,16,8620,대형,휘발유,images/215.png, images/215.png\n\
국산,국산,5,르노삼성,2,QM6,3,이온 실버,2016/01/01,71,3470,중형SUV,휘발유,images/502.png, images/502.png\
';

dataProvider.fillCsvData(data);
```

#### 쌍따옴표로 값이 싸여진 CSV 데이터

만일, 값이 쌍따옴표(double-quotation mark, ex: `"xxx"`)에 둘러싸여 있다면 [DataFillOptions](http://help.realgrid.com/api/types/DataFillOptions/)옵션의 `quoted`속성의 값을 `true`로 설정 해야 합니다.

<a class="btn primary small round lowercase" id="fillCsvData2">쌍따옴표로 둘러싸인 데이터 로드</a>

```js
var data = '\
"국산","국산","2","기아","15","더 뉴 K9","9","미드나이트 블랙","2016/01/01", 16, 8620,"대형","휘발유","images/215.png","images/215.png"\n\
"국산","국산","5","르노삼성","2","QM6","3","이온 실버","2016/01/01", 71, 3470,"중형SUV","휘발유","images/502.png","images/502.png"\
';

dataProvider.fillCsvData(data, {fillMode:"append", quoted: true});
});
```

#### 헤더(Header)가 있는 CSV 데이터

데이터 구조상 헤더가 붙어 있는 CSV 데이터인 경우 헤더 영역을 데이터에서 제외 시켜야할 필요가 있습니다. 이런 경우 [DataFillOptions](http://help.realgrid.com/api/types/DataFillOptions/)옵션의 `start` 속성을 사용할 수 있습니다.

<a class="btn primary small round lowercase" id="fillCsvData3">헤더가 있는 CSV 데이터 로드</a>

```js
var data = '\
"head1","head2","head3","head4","head5","head6","head7","head8"\
"국산","국산","2","기아","15","더 뉴 K9","9","미드나이트 블랙","2016/01/01","16","8620","대형","휘발유","images/215.png","images/215.png"\
';

dataProvider.fillCsvData(data, {fillMode:"append", quoted: true, start: 1});
```

#### 구분자가 콤마(comma)가 아닌 데이터

구분자가 콤마가 아닌 경우 구분자를 지정할 수 있습니다. 이런 경우 [DataFillOptions](http://help.realgrid.com/api/types/DataFillOptions/)옵션의 `delimiter` 속성을 사용할 수 있습니다.

<a class="btn primary small round lowercase" id="fillCsvData4">탭으로 구분된 데이터 로드</a>

```js
var data = '\
"국산"\t"국산"\t"5"\t"르노삼성"\t"2"\t"QM6"\t"3"\t"이온 실버"\t"2016/01/01"\t"71"\t"3470"\t"중형SUV"\t"휘발유"\t"images/502.png"\t"images/502.png"\
';

dataProvider.fillCsvData(data, {fillMode:"append", quoted: true, delimiter:"\t"});
```

[LocalDataProvider.fillJsonData()](http://help.realgrid.com/api/LocalDataProvider/fillJsonData/)함수의 인자는 `data`와 [DataFillOptions](http://help.realgrid.com/api/types/DataFillOptions/)객체인 `options`가 있습니다.

`options`에 대해서는 아래 `DataFillOptions` 데모를 확인하세요.

{% include_relative devbox/FillDataOptions.md %}

<script>

$('#fillCsvData1').click(function() {
var data = '\
국산,국산,2,기아,15,더 뉴 K9,9,미드나이트 블랙,2016/01/01,16,8620,대형,휘발유,images/215.png, images/215.png\n\
국산,국산,5,르노삼성,2,QM6,3,이온 실버,2016/01/01,71,3470,중형SUV,휘발유,images/502.png, images/502.png\
';

dataProvider.fillCsvData(data);
});

$('#fillCsvData2').click(function() {
var data = '\
"국산","국산","2","기아","15","더 뉴 K9","9","미드나이트 블랙","2016/01/01", 16, 8620,"대형","휘발유","images/215.png","images/215.png"\n\
"국산","국산","5","르노삼성","2","QM6","3","이온 실버","2016/01/01", 71, 3470,"중형SUV","휘발유","images/502.png","images/502.png"';
  dataProvider.fillCsvData(data, {fillMode:"append", quoted: true});
});

$('#fillCsvData3').click(function() {
var data = '\
"head1","head2","head3","head4","head5","head6","head7","head8"\n\
"국산","국산","2","기아","15","더 뉴 K9","9","미드나이트 블랙","2016/01/01", 16, 8620,"대형","휘발유","images/215.png","images/215.png"';

  dataProvider.fillCsvData(data, {fillMode:"append", quoted: true, start: 1});
});

$('#fillCsvData4').click(function() {
  var data = '"국산"\t"국산"\t"5"\t"르노삼성"\t"2"\t"QM6"\t"3"\t"이온 실버"\t"2016/01/01"\t 71\t 3470\t"중형SUV"\t"휘발유"\t"images/502.png"\t"images/502.png"';

  dataProvider.fillCsvData(data, {fillMode:"append", quoted: true, delimiter:"\t"});
});
</script>