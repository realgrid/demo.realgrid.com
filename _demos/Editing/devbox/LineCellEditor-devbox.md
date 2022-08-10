#### 특정 문자만 입력가능

editor.inputCharacters 속성에 적용된 문자는 그리드 셀 편집 시 입력이 가능합니다.

```js
{
    "name": "OrderID",
    "fieldName": "OrderID",
    "width": "150",
    "styles": {
        "textAlignment": "center"
    },
    "header": {
        "text": "alphabet만 입력가능",
        "styles": {
            "background": "linear,#22ffd500,#ffffd500,90"
        }
    },
    "editor": {
        "type": "line",
        "inputCharacters": "A-Za-z" 
    }
}
```

#### 특정 문자 입력제한


editor.ignoreCharacters 속성에 적용된 문자는 그리드 셀 편집 시 입력이 불가능합니다

```js
{
    "name": "CustomerID",
    "fieldName": "CustomerID",
    "width": "150",
    "styles": {
        "textAlignment": "center"
    },
    "header": {
        "text": "alphabet은 입력불가",
        "styles": {
            "background": "linear,#22ffd500,#ffffd500,90"
        }
    },
    "editor": {
        "type": "line",
        "ignoreCharacters": "A-Za-z" 
    }
}
```

#### 한글만 입력가능

inputCharacters를 사용해서 한글만 입력할 수 있도록 설정할 수 있습니다.

```js
{
    "name": "EmployeeID",
    "fieldName": "EmployeeID",
    "width": "150",
    "styles": {
        "textAlignment": "center"
    },
    "header": {
        "text": "한글만 입력가능",
        "styles": {
            "background": "linear,#22ffd500,#ffffd500,90"
        }
    },
    "editor": {
        "type": "line",
        "inputCharacters": "ㄱ-힣"
    }
}
```