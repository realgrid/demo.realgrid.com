#### 주차 선택 달력

yyyyWW -> yyyy-WW 컬럼은 필드가 text타입이며 [마스크 편집기](http://demo.realgrid.com/Editing/MaskEditor/) 기능과 [정규식 표현](http://demo.realgrid.com/CellComponent/RegularExpression/) 방법으로 주차 편집 컬럼을 생성할 수 있습니다.


* [DateCellEditor](http://help.realgrid.com/api/types/DateCellEditor/)링크를 참조하세요.  


```js
{
    "name": "dateTime3",
    "fieldName": "dateTime3",
    "width": "160",
    "header": {
        "text": "yyyyWW -> yyyy-WW",
        "styles": {
            "background": "linear,#22ffd500,#ffffd500,90"
        }
    },
    "displayRegExp": /^([0-9]{4})([0-9]{2})$/,
    "displayReplace": "$1-$2",
    "editor": {
        "type": "date",
        "textReadOnly": true,
        "commitOnSelect": true,
        "yearNavigation": true,
        "showWeeks": true,
        "weekSelectable": true,
        "startWeek": 4,
        "mask": {
            "editMask": "9999-99"
        }
    }
}
```