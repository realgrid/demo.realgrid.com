#### 메뉴 정보 구성

팝업 메뉴의 각 메뉴 아이템은 `check` 상태를 가질 수 있고, `group` 속성을 통해 `radio group`으로 구성할 수도 있습니다.

```js
var menu = [{
    label: "menu1 입니다.",
    enabled: true,
    children: [{
        label: "submenu1 입니다."
    }, {
        label: "submenu2 입니다."
    }]
}, {
    label: "menu2 입니다",
    enabled: false
}, {
    label: "-"
}, {
    label: "menu3 입니다",
    type: "check", //check 상태
    checked: true,
    tag: "check_menu"
}, {
    label: "group menu", //group 및 radio
    children: [{ 
        label: "group1 - 첫번째", 
        type: "radio",
        group: "group1",
        checked: true
    }, {
        label: "group1 - 두번째",
        type: "radio",
        group: "group1"
    }, {
        label: "group1 - 세번째",
        type: "radio",
        group: "group1"
    }]
}];
```

#### PopupMenu 추가

구성된 메뉴 정보를 그리드 `addPopupMenu` 함수로 추가할 수 있습니다.

```js
gridView.addPopupMenu("menu1", menu);
```

#### onMenuItemClicked 이벤트

메뉴 아이템이 클릭되면 `onMenuItemClicked` 이벤트가 발생됩니다.

```js
gridView.onMenuItemClicked = function (grid, data, index) {
    alert(data.label);
};
```