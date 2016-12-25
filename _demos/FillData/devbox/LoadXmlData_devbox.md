
#### XML 데이터    

RealGrid의 DataProvider에 XML 포멧의 데이터를 입력 할 수 있습니다. XML데이터의 유형은 아래와 같이 `attribute`를 활용하거나 `childNode`를 활용하는 방법, 모두 가능하며 두 방법을 조합하여 사용할 수도 있습니다.

아래, 각 유형에 대한 데이터 샘플을 참고하세요.

XML 포멧의 데이터는 [LocalDataProvider.fillXmlData()](http://help.realgrid.com/api/LocalDataProvider/fillXmlData/)라는 함수를 이용해 데이터를 읽어 올 수 있습니다.

**attribute를 필드와 매핑하는 XML 데이터**

```xml
<rows>
  <row produce="수입차" country= "유럽" brandNo= "14" brandName= "재규어" modelNo= "5" modelName= "XE 20d" colorNo= "5" color= "소닉 실버" salesDay= "2016-01-01" salesQty= "10" price= "4990" vehicleType= "준중형" fuel= "휘발유"/>
  <row produce="수입차" country= "유럽" brandNo= "14" brandName= "재규어" modelNo= "3" modelName= "All New XF 20t" colorNo= "3" color= "소닉 실버" salesDay= "2016-01-01" salesQty= "3" price= "9090" vehicleType= "중형" fuel= "휘발유"/>
</rows>
```

<a class="btn primary small round lowercase" id="fillXmlData1">XML 데이터 로드</a>

```js
var data = '<rows> \
  <row produce="수입차" country= "유럽" brandNo= "14" brandName= "재규어" modelNo= "5" modelName= "XE 20d" colorNo= "5" color= "소닉 실버" salesDay= "2016-01-01" salesQty= "10" price= "4990" vehicleType= "준중형" fuel= "휘발유"/> \
  <row produce="수입차" country= "유럽" brandNo= "14" brandName= "재규어" modelNo= "3" modelName= "All New XF 20t" colorNo= "3" color= "소닉 실버" salesDay= "2016-01-01" salesQty= "3" price= "9090" vehicleType= "중형" fuel= "휘발유"/> \
  </rows>';

dataProvider.fillXmlData(data);
```

**child node를 필드와 매핑하는 XML 데이터**

```xml
<rows>
  <row>
    <produce>수입차</produce>
    <country>유럽</country>
    <brandNo>14</brandNo>
    <brandName>재규어</brandName>
    <modelNo>5</modelNo>
    <modelName>XE 20d</modelName>
    <colorNo>5</colorNo>
    <color>소닉 실버</color>
    <salesDay>2016-01-01</salesDay>
    <salesQty>10</salesQty>
    <price>4990</price>
    <vehicleType>준중형</vehicleType>
    <fuel>휘발유</fuel>
  </row>
  <row>
    <produce>수입차</produce>
    <country>유럽</country>
    <brandNo>14</brandNo>
    <brandName>재규어</brandName>
    <modelNo>3</modelNo>
    <modelName>All New XF 20t</modelName>
    <colorNo>3</colorNo>
    <color>소닉 실버</color>
    <salesDay>2016-01-01</salesDay>
    <salesQty>3</salesQty>
    <price>9090</price>
    <vehicleType>중형</vehicleType>
    <fuel>휘발유</fuel>
  </row>
</rows>
```
<a class="btn primary small round lowercase" id="fillXmlData2">XML 데이터 로드</a>

```js
var data = ' \
  <rows> \
    <row> \
      <produce>수입차</produce> \
      <country>유럽</country> \
      <brandNo>14</brandNo> \
      <brandName>재규어</brandName> \
      <modelNo>5</modelNo> \
      <modelName>XE 20d</modelName> \
      <colorNo>5</colorNo> \
      <color>소닉 실버</color> \
      <salesDay>2016-01-01</salesDay> \
      <salesQty>10</salesQty> \
      <price>4990</price> \
      <vehicleType>준중형</vehicleType> \
      <fuel>휘발유</fuel> \
    </row> \
    <row> \
      <produce>수입차</produce> \
      <country>유럽</country> \
      <brandNo>14</brandNo> \
      <brandName>재규어</brandName> \
      <modelNo>3</modelNo> \
      <modelName>All New XF 20t</modelName> \
      <colorNo>3</colorNo> \
      <color>소닉 실버</color> \
      <salesDay>2016-01-01</salesDay> \
      <salesQty>3</salesQty> \
      <price>9090</price> \
      <vehicleType>중형</vehicleType> \
      <fuel>휘발유</fuel> \
    </row> \
  </rows> \
';

dataProvider.fillXmlData(data);
```

**두 가지 방법을 조합한 XML 데이터**

```xml
<rows>
  <row brandNo= "14" modelNo= "5" colorNo= "5">
    <produce>수입차</produce>
    <country>유럽</country>
    <brandName>재규어</brandName>
    <modelName>XE 20d</modelName>
    <color>소닉 실버</color>
    <salesDay>2016-01-01</salesDay>
    <salesQty>10</salesQty>
    <price>4990</price>
    <vehicleType>준중형</vehicleType>
    <fuel>휘발유</fuel>
  </row>
  <row brandNo= "14" modelNo= "3" colorNo= "3">
    <produce>수입차</produce>
    <country>유럽</country>
    <brandName>재규어</brandName>
    <modelName>All New XF 20t</modelName>
    <color>소닉 실버</color>
    <salesDay>2016-01-01</salesDay>
    <salesQty>3</salesQty>
    <price>9090</price>
    <vehicleType>중형</vehicleType>
    <fuel>휘발유</fuel>
  </row>
</rows>
```
<a class="btn primary small round lowercase" id="fillXmlData3">XML 데이터 로드</a>

```js
var data = ' \
  <rows> \
    <row brandNo= "14" modelNo= "5" colorNo= "5"> \
      <produce>수입차</produce> \
      <country>유럽</country> \
      <brandName>재규어</brandName> \
      <modelName>XE 20d</modelName> \
      <color>소닉 실버</color> \
      <salesDay>2016-01-01</salesDay> \
      <salesQty>10</salesQty> \
      <price>4990</price> \
      <vehicleType>준중형</vehicleType> \
      <fuel>휘발유</fuel> \
    </row> \
    <row brandNo= "14" modelNo= "3" colorNo= "3"> \
      <produce>수입차</produce> \
      <country>유럽</country> \
      <brandName>재규어</brandName> \
      <modelName>All New XF 20t</modelName> \
      <color>소닉 실버</color> \
      <salesDay>2016-01-01</salesDay> \
      <salesQty>3</salesQty> \
      <price>9090</price> \
      <vehicleType>중형</vehicleType> \
      <fuel>휘발유</fuel> \
    </row> \
  </rows> \
  ';  

dataProvider.fillXmlData(data, {fillMode: "set"});
```

[LocalDataProvider.fillJsonData()](http://help.realgrid.com/api/LocalDataProvider/fillJsonData/)함수의 인자는 `data`와 [DataFillOptions](http://help.realgrid.com/api/types/DataFillOptions/)객체인 `options`가 있습니다.

`options`에 대해서는 아래 `DataFillOptions` 데모를 확인하세요.

{% include_relative devbox/FillDataOptions.md %}


<script>
$('#fillXmlData1').click(function() {
  var data = '<rows> \
    <row produce="수입차" country= "유럽" brandNo= "14" brandName= "재규어" modelNo= "5" modelName= "XE 20d" colorNo= "5" color= "소닉 실버" salesDay= "2016-01-01" salesQty= "10" price= "4990" vehicleType= "준중형" fuel= "휘발유"/> \
    <row produce="수입차" country= "유럽" brandNo= "14" brandName= "재규어" modelNo= "3" modelName= "All New XF 20t" colorNo= "3" color= "소닉 실버" salesDay= "2016-01-01" salesQty= "3" price= "9090" vehicleType= "중형" fuel= "휘발유"/> \
    </rows>';

  dataProvider.fillXmlData(data, {fillMode: "set"});
});

$('#fillXmlData2').click(function() {
  var data = ' \
    <rows> \
      <row> \
        <produce>수입차</produce> \
        <country>유럽</country> \
        <brandNo>14</brandNo> \
        <brandName>재규어</brandName> \
        <modelNo>5</modelNo> \
        <modelName>XE 20d</modelName> \
        <colorNo>5</colorNo> \
        <color>소닉 실버</color> \
        <salesDay>2016-01-01</salesDay> \
        <salesQty>10</salesQty> \
        <price>4990</price> \
        <vehicleType>준중형</vehicleType> \
        <fuel>휘발유</fuel> \
      </row> \
      <row> \
        <produce>수입차</produce> \
        <country>유럽</country> \
        <brandNo>14</brandNo> \
        <brandName>재규어</brandName> \
        <modelNo>3</modelNo> \
        <modelName>All New XF 20t</modelName> \
        <colorNo>3</colorNo> \
        <color>소닉 실버</color> \
        <salesDay>2016-01-01</salesDay> \
        <salesQty>3</salesQty> \
        <price>9090</price> \
        <vehicleType>중형</vehicleType> \
        <fuel>휘발유</fuel> \
      </row> \
    </rows> \
  ';

  dataProvider.fillXmlData(data);
});


$('#fillXmlData3').click(function() {
  var data = ' \
    <rows> \
      <row brandNo= "14" modelNo= "5" colorNo= "5"> \
        <produce>수입차</produce> \
        <country>유럽</country> \
        <brandName>재규어</brandName> \
        <modelName>XE 20d</modelName> \
        <color>소닉 실버</color> \
        <salesDay>2016-01-01</salesDay> \
        <salesQty>10</salesQty> \
        <price>4990</price> \
        <vehicleType>준중형</vehicleType> \
        <fuel>휘발유</fuel> \
      </row> \
      <row brandNo= "14" modelNo= "3" colorNo= "3"> \
        <produce>수입차</produce> \
        <country>유럽</country> \
        <brandName>재규어</brandName> \
        <modelName>All New XF 20t</modelName> \
        <color>소닉 실버</color> \
        <salesDay>2016-01-01</salesDay> \
        <salesQty>3</salesQty> \
        <price>9090</price> \
        <vehicleType>중형</vehicleType> \
        <fuel>휘발유</fuel> \
      </row> \
    </rows> \
    ';  

  dataProvider.fillXmlData(data, {fillMode: "set"});
});

</script>