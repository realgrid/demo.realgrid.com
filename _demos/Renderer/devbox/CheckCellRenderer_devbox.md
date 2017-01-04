#### 체크 렌더러

[CheckCellRenderer](http://help.realgrid.com/api/types/CheckCellRenderer/)

컬럼에 연결된 필드의 자료형이 Boolean이 아니라면, 렌더러의 `trueValues`에 지정된 값들을 true로, `falseValues`로 지정된 값들을 false로 판단합니다.  
이 값들에 해당하지 않는 값은 Boolean으로 자동 변환되어 판단됩니다.  
상태를 표시하는 체크 마크는 배경색, 크기 등을 컬럼 스타일 값들로 지정할 수 있습니다.

#### 편집기로 사용하기

`editable` - true로 지정하면 편집기로 사용됩니다.  
셀이 선택된 상태에서 마우스를 클릭하면 값이 toggle됩니다.  
이 때, falseValues에 지정된 첫번째 값을 false 값으로, trueValues에 지정된 첫번째 값을 true 값으로 사용합니다. 
 지정된 값이 없다면 각각 true/false 값이 사용됩니다.

`spaceKey` - 편집기로 사용될 때 사용자가 space 키를 누르면 값을 변경할 것인 지를 지정합니다.  
즉, 마우스 클릭과 같은 기능을 갖게 할 것인 지를 지정합니다. 기본값은 true입니다.

`주의` - Column.editable이 true(기본값)이면 다른 편집기와 마찬가지로 직접 값을 입력할 수도 있습니다.  
마우스 클릭이나 space 키 입력만으로 충분하다면 Column.editable을 false로 지정하는 것이 좋습니다.

#### 렌더러 스타일

`figureSize` - 체크 마크의 기본 크기는 12 pixel 너비입니다.  
이 스타일에 백분율 값을 지정하여 마크의 크기를 변경할 수 있습니다.

`figureBackground` - true에 해당하는 값의 체크 색상

`figureInactiveBackground` - false 해당하는 값의 체크 색상

```js
{
    ...
    styles: {
        textAlignment: "center",
        figureBackground: "#ffff0000",
        figureInactiveBackground: "#33ff0000",
        figureSize: "130%"
    },
    ...
}
```

#### 렌더러 속성

`falseValues` - false로 판단되는 값들을 콤마로 분리하여 지정합니다.  
이 속성이나 trueValues에 지정되지 않은 값일 경우 false로 생각될 수 있으면 false로 판단합니다.

`trueValues` - true로 판단되는 값들을 콤마로 분리하여 지정합니다.  
이 속성이나 trueValues에 지정되지 않은 값일 경우 true 생각될 수 있으면 true로 판단합니다.

`labelPosition` - Check마크와 텍스트를 같이 표시할 경우 텍스트의 위치를 지정합니다.  
"left", "right", "top", "bottom" 중 하나로 지정할 수 있습니다. 기본값은 텍스트를 표시하지 않는 "hidden" 입니다.

`labelGap` - 텍스트 레이블이 표시되는 경우 체크 마크와 텍스트 사이의 간격을 지정합니다. 기본값은 4 pixel 입니다.


```js
{
    ...
    renderer: {
        type: "check",
        editable: true,
        startEditOnClick: true,
        trueValues: "True",
        falseValues: "False",
        labelPosition: "right"
    },
    ...
}
```