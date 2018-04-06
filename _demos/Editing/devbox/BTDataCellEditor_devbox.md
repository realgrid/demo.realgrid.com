#### 월 선택 달력 `(Only JS Support)`

컬럼의 editor.type 속성의 "btdate" 설정과 btOptions 속성 그리고 bootstrap을 사용한 월 선택 달력 기능을 설정한 Order Date컬럼 컬럼을 확인해 보세요.  

반드시 `bootstrap-datepicker` js파일을 아래와 같이 적용해야 정상적으로 월 선택 달력 기능을 사용할 수 있습니다.

자세한 사용 방법은 아래 링크를 참조하세요.  
[https://eternicode.github.io/bootstrap-datepicker/](https://eternicode.github.io/bootstrap-datepicker/)

```js
//include
<script type="text/javascript" src="/lib/bootstrap/bootstrap-datepicker.js"></script>
<script type="text/javascript" src="/lib/bootstrap/bootstrap-datepicker.ko.min.js"></script>
<link rel="stylesheet" type="text/css" href="/lib/css/bootstrap-datepicker.css">

//editor.btOptions
var btOptions1 = {
    startView: 1,
    minViewMode: 1,
    todayBtn: "linked",
    language: "kr",
    todayHighlight: true,
    language:"ko"
}

//컬럼 설정
{
    name: "OrderDate",
    fieldName: "OrderDate",
    type: "data",
    width: "130",
    styles: {
        textAlignment: "center",
        datetimeFormat: "yyyy-MM"
    },
    header: {
        text: "Order Date",
        styles: {
            background: "linear,#22ffd500,#ffffd500,90"
        }
    },
    editor: {
        type:"btdate", 
        btOptions:btOptions1, //옵션 변수 설정
        datetimeFormat:"yyyy-MM", 
        textReadOnly:true,
        //minDate:new Date("2017-01-01"), 
        //maxDate:new Date("2017-12-31")
    }
}
```

#### text 타입 월 선택 달력

field타입이 text인 컬럼에 문자 형태의 데이터로 월 선택 달력을 설정할 수 있습니다.  
"yyyyMM", "yyyyMM -> yyyy-MM" 컬럼을 참조하세요.

```js
{
    "name": "dateTime3",
    "fieldName": "dateTime3",
    "width": "160",
    "header": {
        "text": "yyyyMM -> yyyy-MM",
        "styles": {
            "background": "linear,#22ffd500,#ffffd500,90"
        }
    },
    "displayRegExp": "([0-9]{4})([0-9]{2})$",
    "displayReplace": "$1-$2",
    "editor": {
        "type": "btdate",
        "btOptions": {
            "startView": 1,
            "minViewMode": 1,
            "todayBtn": "linked",
            "language": "kr",
            "todayHighlight": true,
            "language": "ko"
        },
        "datetimeFormat": "yyyyMM",
        "textReadOnly": true,
        "mask": {
            "editMask": "9999-99"
        }
    }
}
```