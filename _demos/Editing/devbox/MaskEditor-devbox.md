#### 마스크 편집기

텍스트와 날짜 필드의 편집기에 마스크를 적용할 수 있습니다.  
(숫자 필드는 [editFormat](http://demo.realgrid.com/Editing/Editors/) 사용)   

`dropDown`, `multiLine`, `multiCheck`, `number` 에디터 등에서는 동작하지 않습니다.

#### 마스크 편집기 기본형식

`"9"`의 경우 `공백이 허용`됩니다.  
입력되지 않은 경우 값에서 제외됩니다.  
공백이 허용되지 않는 형식이 있는 경우 반드시 입력해야 다른셀로 이동할 수 있습니다.

* `"9"`: new RegExp("[0-9 ]")
* `"0"`: new RegExp("[0-9]")
* `"a"`: new RegExp("[A-Za-z]")
* `"*"`: new RegExp("[A-Za-z0-9]")

#### TextCellEditor에 마스크 편집기 사용

TextCellEditor에 mask에 적용된 형식은 `편집기에만 표시`됩니다.  
mask: `"0000-0000"` 로 입력하는 경우 입력된 형식에 맞춰 편집기가 `"____-____"`로 표시됩니다. 
따라서 텍스트 필드의 경우 Cell에 display하기 위해서는 [정규식 표현](http://demo.realgrid.com/CellComponent/RegularExpression/)을 이용해서 적절히 가공해야 합니다. 


```js
{
    ...
    "editor": {
        "type":"text",
        "mask": "0000-0000-0000-0000"
    },
    //정규식 표현
    "displayRegExp": "([0-9]{4})([0-9]{4})([0-9]{4})([0-9]{4})",
    "displayReplace": "$1-$2-$3-$4"
    ...
}
```

#### DateCellEditor에 마스크 편집기 사용

날짜 필드의 경우 `editMask`, `editor.datetimeFormat`, `styles.datetimeFormat`의 형식을 일치시켜야 하며 `includedFormat:true`를 이용해서 구분자까지 그대로 셀로 전달이 되어야 날짜 데이터가 정상적으로 처리됩니다.

[Mask](http://help.realgrid.com/api/types/Mask/)속성 설정은 아래와 같이 사용할 수 있습니다.

```js
{
    ...
    "editor": {
        "type":"date", 
        "mask": {
            "editMask":"9999-99-99", //표시되는 형식
            "placeHolder":"yyyy-MM-dd", //편집기에 표시될 형식
            "includedFormat":true //편집기에 표시된 내용이 그대로 셀값으로 전달
        }, 
        "datetimeFormat":"yyyy-MM-dd" 
    }, 
    "styles": {
        "datetimeFormat":"yyyy-MM-dd"
    }
    ...
}
```