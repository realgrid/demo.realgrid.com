#### ActualTartget Renderer 종류


* [ActualTargetBulletRenderer](http://help.realgrid.com/api/types/ActualTargetBulletRenderer/)
* [ActualTargetTextRenderer](http://help.realgrid.com/api/types/ActualTargetTextRenderer/)

위와 같은 타입들이 있으며, 데이터의 내용에 맞게 적절한 타입을 선택해야 합니다.

`Target, Actual` 컬럼들의 값을 수정해서 각 renderer들이 변경되는 것을 확인해 보세요.

#### ActualTartget Renderer Type

**Bullet renderer**

목표값을 수직바로 실행값을 수평바로 표시합니다.

```js
{
    type: "series",
    fieldNames: "target,actual",
    renderer: {
        type: "actualTargetBullet",
        maximumBackground: "#18000000"
    },
    styles: {
        figureSize: "50%",
        figureBackground: "#88008800",
        figureBorder: "#88008800",
        figureInactiveBackground: "#ff008800"
    }
}
```

**ActualTarget text renderer**

"실행값 / 목표값" 형식으로 표시합니다.  
실행값의 `폰트`와 `색상` 스타일을 별도의 값으로 지정할 수 있습니다.  
렌더러의 동적 스타일을 이용해서 실행값이 목표값을 초과한 경우 `붉은색`으로 표시하고 있습니다.

```js
{
    type: "series",
    fieldNames: "target,actual",
    fillHeight: 100,
    renderer: {
        type: "actualTargetText",
        actualFont: "Arial,30,bold",
        actualForeground: "#ff888888",
        dynamicStyles: [{
            criteria: "value[1] / value[0] >= 1.0",
            styles: "actualForeground=#ffff00000"
        }]
    },
    header: { text: "Text" }
}
```