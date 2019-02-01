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
    type: "check", //check 설정
    checked: true, //check 상태
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

위에서 구성된 메뉴 정보를 그리드 [addPopupMenu](http://help.realgrid.com/api/GridBase/addPopupMenu/) 함수로 추가할 수 있습니다.  
추가된 `menu1` 을 컬럼에 설정하는 방법은 컬럼 설정 정보를 확인하세요.

```js
gridView.addPopupMenu("menu1", menu);
```

#### onMenuItemClicked 이벤트

메뉴 아이템이 클릭되면 [onMenuItemClicked](http://help.realgrid.com/api/GridBase/onMenuItemClicked/) 이벤트가 발생됩니다.

```js
gridView.onMenuItemClicked = function (grid, data, index) {
    alert(data.label);
};
```

#### 해더 PopupMenu 추가

위에서 구성된 메뉴 정보를 그리드 [addPopupMenu](http://help.realgrid.com/api/GridBase/addPopupMenu/) 함수로 추가할 수 있습니다.  
추가된 `menu2` 를 컬럼 해더에 설정하는 방법은 아래를 참조하세요.

```
var menu = [{
 label: "menu1 입니다.",
 enabled: true,
 children: [{
  label: "submenu1 입니다.",
  callback:function(grid, index){console.log(index)}
 }, {
  label: "submenu2 입니다."
 }]
 }, {
  label: "menu2 입니다",
  enabled: false
}];
gridView.addPopupMenu("menu2", menu);

gridView.setColumnProperty("OrderID","header",{popupMenu:"menu2"});
```