#### 바 렌더러 스타일

컬럼 스타일의 figureBackground로 막대 상자 배경색을 표시합니다.

좌/우/상/하 padding 값들이 바의 너비나 기본 높이를 결정합니다.  
`paddingLeft`, `paddingRight`, `paddingTop`, `paddingBottom`    

`textAlignment` - 텍스트의 수평 정렬 상태를 지정합니다. "near", "center", "far" 중 하나를 지정합니다.  
`lineAlignment` - 텍스트의 수직 정렬 상태를 지정합니다. "near", "center", "far" 중 하나를 지정합니다.  
`figureSize` - padding을 제외한 그리기 영역 내에서 바가 차지할 너비나 높이를 %로 지정합니다.  
지정하지 않으면 기본 크기대로 그려집니다.

```js
{
    ...
    styles: {
        figureBackground: "linear,#ff000044,#ffeeeeee",
        textAlignment: "far",
        paddingRight: 5,
        figureSize: "50%"
    },
    ...
}
```

#### 바 렌더러 속성

[BarCellRenderer](http://help.realgrid.com/api/types/BarCellRenderer/)

Bar 셀렌더러의 숫자형 컬럼 셀의 값을 막대 상자로 표시하는 렌더러 속성입니다.  
막대 상자의 너비는 스타일이 아니라 Bar 렌더러의 속성으로 지정합니다.

```js
{
    ...
    renderer: {
        type: "bar",
        minimum: 0, //최소값
        maximum: 100, //최대값
        minWidth: 150, // 최소 너비
        showLabel: true //라벨표시 여부
    },
    ...
}
```