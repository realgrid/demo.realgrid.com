#### values와 labels 설정

`values`값을 `labels`로 표시될 목록을 지정하면 values값의 위치에 맞는 labels 항목이 표시됩니다.

```js
var columns = [{
	...
}, {
    name: "UserName",
    fieldName: "UserName",
    type: "data",
    width: "130",
    sortable: false,
    lookupDisplay: true,
    values: ["VINET", "HANAR", "SUPRD", "VICTE", "THREE", "SEVEN"],
    labels: ["<VINET>", "<HANAR>", "<SUPRD>", "<VICTE>", "<THREE>", "<SEVEN>"],
    styles: {
        textAlignment: "center"
    },
    header: {
        text: "Values/Labels",
        styles: {
            "background": "linear,#22ffd500,#ffffd500,90"
        }
    }
}, {
	...
}];

grid.setColumns(columns);
```

#### labelField 설정

해당 컬럼 셀에는 실제 값 대신 이 필드의 셀과 같은 행에 있는 `labelField`의 값을 표시합니다.

```js
var columns = [{
	...
}, {
    name: "Age",
    fieldName: "Age",
    type: "data",
    width: "130",
    lookupDisplay: true,
    labelField: "AgeLabel", //label로 사용할 field설정
    styles: {
        textAlignment: "center"
    },
    header: {
        text: "Label Field",
        styles: {
            background: "linear,#22ffd500,#ffffd500,90"
        }
    }
}, {
	...
}];

grid.setColumns(columns);
```

#### dropDown lookup 설정

values와 labels 목록은 `DropDown` 편집기의 lookup 목록으로 사용될 수도 있습니다.

```js
var columns = [{
	...
}, {
    name: "Gender",
    fieldName: "Gender",
    type: "data",
    width: "100",
    sortable: false,
    lookupDisplay: true,
    editor: {
        type: "dropDown",
        dropDownCount: 2,
        domainOnly: true,
        values: ["Male","Female"],
        labels: ["<Male>","<Female>"]
    },
    styles: {
        textAlignment: "center"
    },
    header: {
        text: "Gender",
        "styles": {
            "background": "linear,#22ffd500,#ffffd500,90"
        }
    }
}, {
	...
}];

grid.setColumns(columns);
```

#### value값 확인하기

현재 포커스 위치의 value값을 확인해보세요.

<a class="btn primary small round lowercase" id="getValue">데이터셀 값 확인</a>

```js
var focusIndex = gridView.getCurrent().itemIndex;
var focusField = gridView.getCurrent().fieldName;
alert(gridView.getValue(focusIndex, focusField))
```

<script>
$('#getValue').click(function() {
    var focusIndex = gridView.getCurrent().itemIndex;
	var focusField = gridView.getCurrent().fieldName;
	alert(gridView.getValue(focusIndex, focusField))
});
</script>