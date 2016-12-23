#### 시리즈 컬럼

시리즈 컬럼은 컬럼에 설정된 렌더러를 통해 셀을 그리게 됩니다.   
예제는 *통계청 포탈에서 제공하는 세계 경제 지표* 데이터입니다.  
"Series" 컬럼은 필드들의 값을 텍스트로 나열하는 *기본 시리즈 렌더러*가 설정되었고, "Spark" 컬럼은 *Spark line chart 렌더러*로 설정됐습니다.  

```js
"renderer": { 
    "type": "sparkLine",
    "highFill": "#ff008800",
    "lowFill": "#ffff0000",
    "lastFill": "#ff888888"
}
```

데이터셀들의 값을 수정해서 Spark line이 변경되는 것을 확인해 보세요.

#### 시리즈 컬럼 설정

컬럼의 type은 `"series"`로 지정하고, 표시할 컬럼은 fieldNames 속성으로 지정합니다. fieldNames에 콤마로 나누어진 필드 목록을 지정하는 데, 데이터 프로바이더에 추가한 컬럼 순서대로 이어진 필드들을 지정할 때는 `field1..fieldn` 처럼 할 수도 있습니다. 


```js
{
    "name": "colSeries",
    "type": "series", //타입 설정
    "fieldNames": "2000,2002,2004,2006,2008,2010", //컬럼에 표시할 필드들
    "width": 120,
    "header": { "text": "Series" },
    "styles": { 
        "background": "#0800ff00",
        "textAlignment": "near"
    }
}, {
    "name": "colSpark",
    "type": "series",
    "fieldNames": "2000..2010", //2000부터 2010필드까지 한컬럼에 표시
    "width": 150,
    "renderer": { 
        "type": "sparkLine",
        "highFill": "#ff008800",
        "lowFill": "#ffff0000",
        "lastFill": "#ff888888"
    },
    "header": { "text": "Spark" },
    "styles": { 
        "background": "#08000000",
        "figureBackground": "#ff888888", 
        "paddingLeft":4, 
        "paddingRight":4 ,
        "paddingTop":4,
        "paddingBottom":4
    }
}
```