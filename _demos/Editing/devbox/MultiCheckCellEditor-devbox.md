#### MultiCheckCellEditor 설정하기

[MultiCheckCellEditor](http://help.realgrid.com/api/types/MultiCheckCellEditor/)를 사용하기 위해서는 Editor의 type을 `"multiCheck"`로 지정하여 사용합니다. 

기본적인 기능은 dropDown과 같으며 추가된 속성으로는 `acceptText`, `canceltext`, `showButtons`가 있습니다. 
acceptText, cancelText에는 MultiCheckCellEditor에서 표시되는 DropDownList의 accept, cancel 버튼에 표시될 텍스트를 지정 합니다. 
showButtons는 accept, cancel 버튼의 표시 여부를 지정 합니다. 

values, labels는 array 타입의 문자열 데이터를 지정 합니다. 
각 value를 구분하기 위한 구분자 지정은 editor의 속성이 아닌 column.valueSeperator에서 지정하며 기본값은 ',' 입니다. 

```js
var columns = [{
    ...
    "valueSeparator": ",",
    "editor" : {
        "type": "multicheck",
        "dropDownCount": 4,
        "acceptText": "확인",
        "cancelText": "취소",
        "showButtons": true
    },
    "values": ['KR', 'US', ...],
    "labels": ['대한민국', '미국', ...], 
    ...
}]
```

#### CSS Styles

Multi Check Cell Editor에도 CSS Style을 적용할 수 있습니다.  
자세한 내용은 [CSS Styles](http://demo.realgrid.com/GridStyle/CSSStyles/) 페이지에서 확인하세요.