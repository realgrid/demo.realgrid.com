---
layout: page
title: 데이터 타입
order: 2
published: true
categories:
  - 데이터 관리
tags: ['data', 'datatype']
---

리얼그리드 DataProvider의 DataField는 네 가지 자료형 중 하나가 될 수 있습니다.  
Text, Number, Boolean, Datetime이 그것들인데, RealGrids.DataType 상수로 선언되어 있습니다.

```js
var DataType = {
    TEXT: "text",
    NUMBER: "number",       // or "numeric"
    BOOLEAN: "boolean",     // or "bool"
    DATETIME: "datetime"
};
```

Local DataProvider(RealGrid 메모리에 데이터를 저장합니다. 현재 리얼그리드 DataProvider는 Local DataProvider입니다.)에는 각 필드의 자료형에 맞게 변화되어 값들이 저장됩니다.  

---

#### 1). Text

문자열입니다. loadData()나 setRows() 등을 통해 리얼그리드 DataProvider에 전달되는 문자열은 utf-8로 인코딩되어야 합니다.  
Local DataProvider에는 <mark>문자열이 아닌 값은 문자열로 변환되어 DataProvider에 저장됩니다. undefined는 undefined로 저장됩니다.</mark>  

---

#### 2). Number

IEEE-754 double 정밀도 부동 소수점 값입니다. Javascript의 Number와 동일합니다. 정수형 data type은 별도로 존재하지 않습니다.  
Local DataProvider에는 <mark>Number가 아닌 값은 Number로 변환되어 DataProvider에 저장됩니다.. undefined는 undefined로 저장됩니다.</mark>

---

#### 3). Boolean

false, true 둘 중 하나의 값으로 저장됩니다. 즉, loadData()나 setRows() 등으로 외부 데이터가 Boolean 필드에 저장될 때, <mark>Boolean이 아닌 원본 값은 보존되지 않고 true/false로 변환됩니다. undefined는 undefined로 저장됩니다.</mark> 아래의 값들이 false로, 나머지 값들은 true로 변환됩니다.

```
0	Javascript 숫자 0
NaN	Javascript NaN
""	빈 문자열
null	Javascript null
```

DataProvider에는 false/true 두 값들 중 하나로 저장되지만, 그리드 사용 중 여러 지점에서 문자열과의 호환이 필요해집니다.  
Boolean 필드의 값과 문자열 값의 호환성이 고려되어야 하는 경우는 아래와 같습니다.

---

### Text -> DataProvider	

loadData()나 setRows() 등으로 DataProvider에 행들을 추가할 때, Boolean이 아닌 값을 Boolean 필드에 저장하고 싶다면, DataProvider나 DataField의 booleanFormat 속성을 이용합니다.

```
dataProvider.setOptions({
    booleanFormat: "false,f:true:0"
});
dataProvider.setFields([{
    booleanFormat: "false,f:true:0"
},
...}]);
```

booleanFormat 속성 값은 "false,f:true:0"과 같은 형식으로 지정합니다.  
콜론(:)으로 구분하며 첫번째 마디는 false로 해석될 하나 이상의 값들을 콤마로 분리하고, 두번째 마디에는 true로 해석할 하나 이상의 값들을 역시 콤마로 분리하여 지정합니다.  
세번째 마디에는 대소문자를 구분해야 하는 경우 1, 구분 없이 해석할 경우에는 0을 입력합니다. 지정하지 않거나 잘못된 값을 지정하면 대소문자를 구분합니다.   
DataProvider와 DataField에 모두 지정되었다면 DataField에 지정된 것들을 따릅니다.  
속성 값이 지정되면 Boolean 값이 아닌 경우 두 속성 값의 목록 중에 해당하는 값이 있으면 그 설정을 따르고, 속성 목록에 없는 값은 위에서 설명한 Boolean 변환 룰에 따라 저장됩니다. 원본 값은 저장되지 않습니다.  
즉, 어떤 상황이든 Text 원본값은 Bool 필드에는 true/false로만 저장됩니다. undefined값은 undefined로 저장됩니다.  

---

#### Cell Renderer	

셀 렌더러들은 Styles의 booleanFormat 속성 값을 기준으로 Boolean 필드의 값을 표시합니다. booleanFormat이 설정되지 않으면 각각 "false", "true"로 표시됩니다. undefined는 빈문자열로 표시됩니다.

```
grid.setColumns([{
    styles: {
        booleanFormat: "Lie;Truth",
        ...
    }
}, {
...}]);
```

booleanFormat 스타일 속성은 "거짓말;참말;거짓말" 처럼 세미콜론(;)이나 콜론(:)으로 분리하여 false/true/undefined 값을 지정합니다.

---

#### Cell Editor	

텍스트를 입력하는 셀 에디터들은 booleanFormat 속성을 지정해서 Boolean 필드의 값을 텍스트로 표시하고, 입력된 텍스트 값을 Boolean 값으로 저장할 수 있습니다.

```
grid.setColumns([{
    editor: {
        booleanFormat: "false,f:true:0",
        emptyValue: false // 기본값은 undefined
        ...
    }
}, {
...}]);
```

셀 에디터의 booleanFormat 속성은 "false,f:true:0"과 같은 형식으로 지정합니다.  
콜론(:)으로 구분하며 첫번째 마디는 false로 해석될 값들을 콤마로 분리하고, 두번째 마디에는 true로 해석할 값들을 지정합니다.   
세번째 마디에는 대소문자를 구분해야 하는 경우 1, 구분 없이 해석할 경우에는 0을 입력합니다.  
지정하지 않거나 잘못된 값을 지정하면 대소문자를 구분합니다.  
또한, false, true 목록의 첫번째 값이 편집 시작 시 에디터에 표시되는 값이 됩니다.  
booleanFormat 지정하지 않으면 "false,f,0:true,t,1:0"이 기본 포맷으로 사용됩니다.  
emptyValue 속성에 빈문자열을 입력할 때 변환될 값을 지정합니다. 지정하지 않으면 undefined로 저장됩니다.  

---

#### 4). Datetime

Datetime 필드의 값들은 DataProvider에 Flash player가 생성하는 Date 객체로 저장됩니다.  
undefined는 undefined로 저장됩니다. 하지만, RealGrid 사용자는 주로 Text로 변환된 값이나, Javascript 함수를 통해 Javascript Date 객체로 변환되어 전달되는 값을 사용하게 됩니다.   
또, Datetime 편집기 등을 사용하여 입력하게 되므로 내부 구현 방식과 무관하게 Date 값을 다루게 됩니다.

---

#### 4.1). load

loadData()를 통해 Datetime 형의 값이 문자열로 전달되거나, setRows() 함수 등으로 javascript에서 문자열로 Date 필드의 값을 전달할 때, 그 문자열은 아래와 같이 리얼그리드가 Datetime 형의 값으로 인식할 수 있는 몇가지 형식으로 반드시 구성되어야 합니다. 이 형식의 종류는 DataProvider나 DataField의 datetimeFormat 속성 및 관련된 속성들에 지정할 수 있습니다. DataProvider와 DataField에 모두 설정된 경우 DataField에 지정한 것이 우선합니다.

```
dataProvider.setOptions({
    datetimeFormat: "yyyy/MM/dd",
    amText: "AM",
    pmText: "PM",
    baseYear: 2000
});
dataProvider.setFields([{
    datetimeFormat: "yyyy/MM/dd",
    amText: "am",
    pmText: "pm",
    baseYear: 2000
},
...}]
```

---

#### custom

DataProvider나 DataField의 datetimeFormat 속성은 "yyyy/MM/dd"과 같은 패턴으로 지정합니다.  
또한, DataProvider와 DataField에는 custom 형식을 해석하는 데 필요한 baseYear, amText, pmText 속성들이 있습니다.  
baseYear에는 년도 값이 100보다 작을 경우 기준 년도가 됩니다. 기본값은 2000입니다.  
amText, pmText에는 각각 AM/PM 구분자를 지정합니다. 이 값이 지정되어야 문자열에 포함된 AM/PM 구분자를 해석합니다.  
문자열에는 AM/PM 구분자가 중간 포함되어 있는 데 형식에 지정하지 않으면 시간 쪽 값을 읽지 못하게 됩니다. 기본값은 "AM", "PM"입니다.  
datetimeFormat 속성이 DataField에 지정하지 않으면, DataProvider에 지정된 datetimeFormat, amText, pmText, baseYear 속성 값들을 이용합니다.  
DataField에 datetimeFormat는 지정됐지만, amText, pmText, baseYear가 지정되지 않았다면 DataProvider에 지정된 값을 이용합니다.  
DataProvider에 지정된 기본 값은 각각 "yyyy/MM/dd HH:mm:ss", "AM", "PM", 20000 입니다. custom 형식으로 해석할 수 있는 문자열 패턴들은 아래와 같습니다.   
대소문자를 구분하므로 주의해야 합니다. 또한, 지정한 패턴과 다른 형식으로 표시된 문자열이거나 범위를 벗어나는 경우 의도와 다른 값으로 해석될 수 있습니다.  

---

|:--|:--|
|**년도 (y)**| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;소문자 yy, yyyy 둘 중 하나로 지정합니다. 년도는 14, 2104 처럼 두 자리나 네 자리여야 합니다. 0 ~ 9999 사이의 값이어야 합니다.|
|||
|**월 (M)**|	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;대문자 MM: 01, 12와 같이 두자리여야 하고 1 ~ 12 사이의 값이어야 합니다.|
||&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;대문자 M: 1, 12와 같이 앞자리 0을 생략할 수 있습니다. 이 경우에는 구분자가 반드시 포함되어야 합니다.|
||&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(현재 RealGrid+ 만 가능)|
|||
|**일 (d)**|	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;소문자 dd: 일자는 01, 22 처럼 두 자리여야 하고 1 ~ 31 사이의 값이어야 합니다. |
||&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;소문자 d: 1, 22와 같이 앞자리 0을 생략할 수 있습니다. 이 경우에는 구분자가 반드시 포함되어야 합니다.| 
||&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(현재 RealGrid+ 만 가능)  |
|||
|**AM/PM (a)**|	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;소문자 a로 지정합니다. AM/PM 구분자는 amText, pmText 속성에 지정한 값과 동일해야 합니다.  |
|||
|**시간 (H)**| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;대문자 HH: 00, 13 처럼 두 자리여야 하고 0 ~ 23 사이의 값이어야 합니다. 24는 다음날 0시로 해석합니다.|  
||&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;대문자 H: 0, 13과 같이 앞자리 0을 생략할 수 있습니다. 이 경우에는 구분자가 반드시 포함되어야 합니다. 24는 다음날 0시로 해석합니다.  |
||&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(현재 RealGrid+ 만 가능)  |
|||
|**시간 (h)**| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;소문자 hh: 00, 10 처럼 두 자리여야 합니다. |
||&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1 ~ 12 사이의 값이어야 합니다. a 값이 amText이면 12는 0시로 해석합니다. pmText인 경우 12시(정오)로 해석합니다.  |
||&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;소문자 h: 0, 10과 같이 앞자리 0을 생략할 수 있습니다. |
||&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;이 경우에는 구분자가 반드시 포함되어야 합니다.a 값이 amText이면 12는 0시로 해석합니다. pmText인 경우 12시(정오)로 해석합니다.  |
||&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(현재 RealGrid+ 만 가능)  |
|||
|**분 (m)**|	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;소문자 mm:00, 33 처럼 두 자리여야 합니다. 0 ~ 59 사이의 값이어야 합니다.  |
||&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;소문자 m: 0, 33과 같이 앞자리 0을 생략할 수 있습니다. 이 경우에는 구분자가 반드시 포함되어야 합니다. 0 ~ 59 사이의 값이어야 합니다.  |
||&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(현재 RealGrid+ 만 가능)  |
|||
|**초 (s)**|	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;소문자 ss: 00, 22 처럼 두 자리여야 합니다. 0 ~ 59 사이의 값이어야 합니다.  |
||&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;소문자 s: 0, 22과 같이 앞자리 0을 생략할 수 있습니다. 이 경우에는 구분자가 반드시 포함되어야 합니다. 0 ~ 59 사이의 값이어야 합니다.  |
||&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(현재 RealGrid+ 만 가능)  |
|||
|**밀리초 (S)**|	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;대문자 SSS로 지정합니다. 밀리초는 000, 122 처럼 세 자리여야 합니다. 0 ~ 999 사이의 값이어야 합니다.  
|||
|**구분자들**|	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;년 구분자 "/", ".", "-"들과 시간 구분자 ":"가 있습니다. |
||&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;빈 칸도 포함될 수 있습니다. 구분자는 위치 역할만을 담당하고 문자열의 것과 일치하지 않아도 해석 가능합니다. |
||&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;즉, 패턴에는 "/"로 지정했지만 문자열의 그 자리에는 "-"로 되어 있어도 해석이 됩니다.  |

형식에 지정한 패턴 개수보다 문자열 패턴의 개수가 모자라도 가능한 만큼 해석합니다. 아래와 같은 예제들이 가능합니다. 

|:--|:--|
|**yyyy/MM/dd a**|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"2014/01/12 AM 13:22:33"|
|**HH:mm:ss**|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"2014.11.22"|
|||
|**yyyy/MM/dd**|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"2014.11.22"|
||&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"2014/12"|


---

#### iso	

datetimeFormat 속성을 "iso"로 지정합니다.  
아래의 ISO 8601 표준 날짜/시간 형식으로 표현된 값을 해석합니다.

YYYY-MM-DDTHH:NN:SSTZD

시간 부분이 존재하는 경우 중간의 "T"는 반드시 존재해야 합니다.   
"TZD" 위치에는 시간대(Time zone)가 있어야 합니다.   
표준시를 사용하는 경우 "Z" 문자로, 표준시가 아니면 "+09:00", "-02:00"과 같이 지역 시간대 값이 지정되어야 합니다.  
ISO 표준 상으로는 시간대가 반드시 존재해야 하지만, 리얼그리드에서는 지정되어 있지 않으면 지역 시간대 값으로 해석합니다.   
또한, 시간 부분이 없거나 날짜 일부만 존재해도 해석합니다. 년도가 두자리일 경우 1900년이 추가되어 해석됩니다.  
"iso" 형식으로 해석할 수 있는 문자열들은 아래와 같습니다.

```
"2014/12/12T21:22:33Z"
"2014/12/12T21:22:33+09:00"
"2014/12/12T21:22"
"2014/12/12"
"2014/12"
```

---

#### flash	

datetimeFormat 속성을 "flash"로 지정합니다.  
Flash 플랫폼이 native로 지원하는 형식입니다. . 년도가 두자리일 경우 1900년이 추가되어 해석됩니다.  
해석 가능한 예제는 아래와 같습니다.

```
"2014/12/12T21:22:33Z"
"2014/12/12T21:22:33+09:00"
"2014/12/12T21:22"
"2014/12/12"
"2014/12"
```

가능하면 이 형식을 따라야 합니다. 특히 10만 건 이상의 대량 데이터를 로드하는 경우는 이 형식이 "iso"나 custom 형식보다 수 배 이상 빠르게 파싱합니다.

```
"Wed Jan 1 11:22:33 GMT+0900 2014"
"Wed Jan 1 2014 11:22:33 GMT+0900"
"Wed Jan 1 2014"
"01/01/2014"
"01/2014"
"2014/01/01 11:22:33 GMT+0900"
"2014/01/01 11:22:33"
"2014/01/01"
```

---

#### 4.2) rendering
Datetime 필드의 값을 표시하는 셀 렌더러는 datetimeFormat 스타일 값을 사용합니다.

```
grid.setColumns([{
    styles: {
        datetimeFormat: "yyyy.MM.dd a HH:mm:ss;오전,오후",
        ...
    }
}, {
...}]);
```

datetimeFormat 스타일은 아래와 같은 패턴들로 구성될 수 있습니다.   
스타일값이 지정되지 않으면 "yyyy/MM/dd" 포맷이 기본으로 사용됩니다.  
이전 버전의 dateFormat 스타일 속성이 지정되어 있는 경우 셀 렌더러는 그 형식을 사용하지만, dateFormat 스타일 속성은 폐기될 예정입니다.   
dateFormat 스타일 값을 없애고 datetimeFormat 스타일 값으로 재설정하십시오. 
이 형식의 패턴들은 대소문자를 구분하고, 자리수가 중요합니다.  

---

|:--||:--|
|**년도 (y)**| | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; yyyy = 2014, yy = 14|
|||
|**월 (M)**| | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; M = 1, MM = 11|
|||
|**일 (d)**| | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; d = 1, dd = 11, dd = 01|
|||
|**AM/PM (a)**| | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; AM, PM  |
|||
|**시 (H: 0 ~ 23)**| | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; H = 1, H = 11, HH = 01|
|||
|**시 (h: 1 ~ 12)**| | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; h = 1, h = 11, hh = 01|
|||
|**분 (m)**| | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; m = 1, mm = 11, mm = 01|
|||
|**초 (s)**| | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; s = 1, ss = 11, ss = 01|
|||
|**밀리초 (S)**| | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; S = 1, SS = 12 SSS = 123|
|||
|**구분자들 (:, /, ., -)**| | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; yyyy/MM/dd, yyyy.MM.dd, yyyy-MM-dd, HH:mm:ss.SSS|
|||
|**텍스트**| | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 대소문자 'a'에서 'z'로 시작하는 텍스트가 아니면 텍스트 그대로 표시됩니다.|

---

#### 4.3) editing
Datetime 필드의 값을 입력하는 셀 에디터 또한 사용자의 입력을 Datetime 값으로 변환하고, Datetime 값을 에디터에 표시하기 위한 형식이 필요합니다.  
셀 에디터의 datetimeFormat 속성에 아래와 같은 형식으로 지정합니다.

```
grid.setColumns([{
    editor: {
        datetimeFormat: "yyyy.MM.dd a HH:mm:ss;2000;오전,오후",
        ...
    }
}, {
...}]);
```

세미콜론(;)으로 분리되며 첫 번째 마디는 날짜/시간의 패턴, 두 번째 마디는 년도를 두자리 이하로 입력할 때 자동 추가될 년도를 지정합니다.   
기본값은 2000 입니다. 세번째 마디에는 AM/PM 구분자를 콤마로 분리해서 순서대로 지정합니다.  
날짜/시간 패턴에는 아래와 같은 구성 요소들이 지정될 수 있습니다. 입력 시에는 범위 내의 값이라면 자리수가 중요하지 않습니다.   
즉, 패턴에 "yy"라고 설정하고 "2014"로 입력하면 년도가 2014가 됩니다.   
하지만, 편집 시작 시 에디터에 표시할 때는 자리수만큼 표시됩니다.

---

|:--|:--|
|년도 (y)|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;yyyy = 2014, yy = 14|
||&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;100보다 작은 값을 입력하면 datetimeFormat의 두번째 마디에 지정한 기준 년도를 추가해서 해석합니다.|
|||
|월 (M)|	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;M = 1, M = 11, MM = 01|
|||
|일 (d)|	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;d = 1, d = 11, dd = 01|
|||
|AM/PM 구분자(a)|	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;datetimeFormat의 세번째 마디에서 지정한 값을 사용합니다. |
||&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"am", "pm" 은 대소문자 구분하지 않고 각각 am, pm으로 해석합니다. |
||&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;am 이나 pm 이 설정되면 입력시 "H", "h"는 1 ~ 12 범위를 갖게됩니다. |
||&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;12시고 am이면 0시, 12시고 pm이면 12시로 해석합니다.|
|||
|H: 시(0 ~ 23)|	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;H = 1, H = 11, HH = 01|
||&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;입력시 24는 0으로 해석합니다. 24를 넘는 값은 에러입니다.|
|||
|h: 시(1 ~ 12)|	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;h = 1, h = 11, hh = 01|
||&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;입력 시에는 "H"와 동일하게 해석합니다.|
|||
|m: 분(0 ~ 59)|	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;m = 1, m = 11, mm = 01|
||&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;입력시 60은 0으로 해석합니다. 60을 넘는 값은 에러입니다.|
|||
|s: 초(0 ~ 59)|	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;s = 1, s = 11, ss = 01|
||&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;입력시 60은 0으로 해석합니다. 60을 넘는 값은 에러입니다.|
|||
|구분자|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;구분자는 5가지 문자 중 하나로 지정하면 됩니다. |
|(./-:whitespace)|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;연속된 빈칸(whitespace)는 포맷에서나 입력값에서 모두 하나의 구분자로 해석합니다.|
|||
|연속값|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"yyyyMMdd"와 같이 구분자 없이 연속적으로 포맷 문자열을 지정한 경우, 입력값 중 연속된 하나의 숫자열을 포맷과 비교하여 해석합니다. |
||&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;이 때 포맷 문자열에 포함된 각 토큰의 자리수에 맞춰 앞 쪽 토큰부터 입력 숫자열을 분리하여 해석합니다.|
||&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"yyyyMMdd": "2014032" => 2014.03.02, "yyyyMMdd": "2014" => 2014.01.01, "yyyyMM": "20140505" => 2014.05.01|
||&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"yyyyMMdd": "2014.02.03" => 2014.01.01, "yyyyMMdd.MM.dd": "201401.02.03" => 2014.02.03|


에러가 되는 값을 입력하면 입력이 무시됩니다.