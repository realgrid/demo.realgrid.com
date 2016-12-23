#### Renderer 종류

* [Line](http://help.realgrid.com/api/types/SparkLineRenderer/)
* [Column](http://help.realgrid.com/api/types/SparkColumnRenderer/)
* [WinLoss](http://help.realgrid.com/api/types/SparkWinLossRenderer/) 

위와 같은 타입들이 있으며, 데이터의 내용에 맞게 적절한 타입을 선택해야 합니다.   

데이터셀들의 값을 수정해서 각 renderer들이 변경되는 것을 확인해 보세요.

#### Renderer Type

기간 등 일정 범위 내의 데이터 흐름을 간략하고 직관적으로 표시하는 데 사용될 수 있습니다.  

**sparkLine 타입**

```js
{
    name: "colLine",
    type: "series",
    fieldNames: "2000..2010",
    width: 150,
    renderer: { 
        type: "sparkLine",
        highFill: "#ff008800",
        lowFill: "#ffff0000",
        lastFill: "#ff888888"
    },
    header: { text: "Spark Line" },
    styles: { 
        background: "#080000ff",
        figureBackground: "#ff888888", 
        paddingLeft:4, 
        paddingRight:4 ,
        paddingTop:4,
        paddingBottom:4
    }
}
```

**sparkColumn 타입**


```js
{
    name: "colColumn",
    type: "series",
    fieldNames: "2000..2010",
    width: 150,
    renderer: {
        type: "sparkColumn",
        highFill: "#ff008800",
        lowFill: "#ffff0000",
        lastFill: "#ff888888"
    },
    header: { text: "Spark Column" },
    styles: {
        figureBackground: "#ff888888",
        paddingLeft: 4,
        paddingRight: 4,
        paddingTop: 4,
        paddingBottom: 4
    }
}
```

**sparkWinLoss 타입**

```js
{
    name: "colWinLoss",
    type: "series",
    fieldNames: "2000..2010",
    width: 150,
    renderer: {
        belowHeight: 0.45,
        type: "sparkWinLoss",
        belowFill: "#ffff0000"
    },
    header: { text: "Spark WinLoss" },
    styles: {
        background: "#080000ff",
        figureBackground: "#ff008800",
        paddingLeft: 2,
        paddingRight: 2,
        paddingTop: 2,
        paddingBottom: 2
    }
}
```