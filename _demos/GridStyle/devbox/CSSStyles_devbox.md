#### CSS Styles 적용

필터를 제외한 각 에디터에 CSS 스타일을 사용하기 위해서는 

* editorOptions.useCssStyleDropDownList
* editorOptions.useCssStyleDatePicker
* editorOptions.useCssStylePopupMenu
* editorOptions.useCssStyleMultiCheck 

속성값에 true를 설정해야 합니다.  
에디터 모두 CSS Style을 적용 한다면 useCssStyle 속성값만 true로 설정해도 됩니다.

필터의 CSS 스타일 적용여부는 FilteringOptions.selector.useCssStyle 에서 설정 합니다.  
필터의 경우 editorOptions.useCssStyle 의 영향을 받지 않습니다. 

`※ CSS 스타일은 각 객체가 생성된 이후에는 변경할 수 없습니다.(동적으로 변경할 수 없습니다.)`

```js
//각 Editor에 CSS 스타일 적용 여부 설정
gridView.setEditorOptions({
    //useCssStyle: true,  //모든 에디터에 CSS를 적용할 경우 사용  
    useCssStyleDropDownList: true, //dropDown
    useCssStyleDatePicker: true,   //달력
    useCssStylePopupMenu: true,    //popupMenu
    useCssStyleMultiCheck: true    //multiCheck
});
 
// 필터에 CSS 스타일 적용 여부 설정
gridView.setFilteringOptions({selector: {useCssStyle: true}});
```

#### CSS Styles

아래는 CSS Styles 데모에서 사용된 CSS 속성들입니다.  

```js
<style type="text/css">
    /*                  */
    /*      Filter      */
    /*                  */
    .rg-filterselector {
        background : rgb(233, 233, 233);
        border :1px solid rgb(200, 200, 200);
        box-shadow :rgba(0, 0, 0, 0.8) 1px 2px 5px;
        font-family :"나눔고딕코딩";
        font-style :normal;
        font-variant :normal;
        font-weight :normal;
        font-size :10pt;
        padding :4px;
    }
    .rg-filter-actions {
    }
    .rg-filter-action-item {
    } 
    .rg-filter-action-item:hover {
        text-decoration:underline;
    }
    .rg-filter-action-check {
    }
    .rg-filter-action-label {
    }
    .rg-filter-all {
        background-color : rgba(45, 164, 164, 1);
        color : #E0E0E0;
    }
    .rg-filter-all-check {
    }
    .rg-filter-all-label {
    }
    .rg-filter-all-hr {
    }
    .rg-filter-items {
    }
    .rg-filter-item {
        color: white;
        background-color: #151500;
    }
    .rg-filter-item:hover {
        text-decoration:underline;
    }
    .rg-filter-item-check {
    }
    .rg-filter-item-label {
    }

    /*                  */
    /*    MultiCheck    */
    /*                  */
    .rg-filterselector {
        background : rgb(233, 233, 233);
        border :1px solid rgb(200, 200, 200);
        box-shadow :rgba(0, 0, 0, 0.8) 1px 2px 5px;
        font-family :"나눔고딕코딩";
        font-style :normal;
        font-variant :normal;
        font-weight :normal;
        font-size :10pt;
        padding :4px;
    }
    .rg-filter-actions {
    }
    .rg-filter-action-item {
    } 
    .rg-filter-action-item:hover {
        text-decoration:underline;
    }
    .rg-filter-action-check {
    }
    .rg-filter-action-label {
    }
    .rg-filter-all {
        background-color : rgba(45, 164, 164, 1);
        color : #E0E0E0;
    }
    .rg-filter-all-check {
    }
    .rg-filter-all-label {
    }
    .rg-filter-all-hr {
    }
    .rg-filter-items {
    }
    .rg-filter-item {
        color: white;
        background-color: #151500;
    }
    .rg-filter-item:hover {
        text-decoration:underline;
    }
    .rg-filter-item-check {
    }
    .rg-filter-item-label {
    }

    /*                  */
    /*    MultiCheck    */
    /*                  */
    .rg-multicheck {
        background: #fff;
        border: 1px solid rgb(50, 50, 50);
        box-shadow: rgba(0, 0, 0, 0.8) 1px 2px 5px;
        font-family: 나눔고딕코딩;
        font-style: normal;
        font-variant: normal;
        font-weight: normal;
        font-size: 12pt;
        padding: 0px;
        margin: 0px;
    }
    .rg-multicheck-button {
        text-align: center;
    }
    .rg-multicheck-accept {
        border: 1px solid #0a3c59;
        border-radius: 3px;
        color: #06426c;
        border-width: 1px; 
    }
    .rg-multicheck-cancel {
        border: 1px solid #0a3c59;
        border-radius: 3px;
        color: #06426c;
        border-width: 1px; 
    }
    .rg-multicheck-accept:hover {
        background-color: #888
    }
    .rg-multicheck-cancel:hover {
        background-color: #888
    }
    .rg-multicheck-select {
        background:#40ff0b;
        color:#ffffff;
    }
    .rg-multicheck-list {
    }
    .rg-multicheck-item {
        background:none;
        color:none;
    }
    .rg-multicheck-item:hover {
        background:rgba(0, 0, 255, 0.2);
        color:none;
    }
    .rg-multicheck-selectitem {
        background:rgba(0, 0, 255, 0.2);
        color:#000;
    }.rg-multicheck {
        background: #fff;
        border: 1px solid rgb(50, 50, 50);
        box-shadow: rgba(0, 0, 0, 0.8) 1px 2px 5px;
        font-family: 나눔고딕코딩;
        font-style: normal;
        font-variant: normal;
        font-weight: normal;
        font-size: 12pt;
        padding: 0px;
        margin: 0px;
    }
    .rg-multicheck-button {
        text-align: center;
    }
    .rg-multicheck-accept {
        border: 1px solid #0a3c59;
        border-radius: 3px;
        color: #06426c;
        border-width: 1px; 
    }
    .rg-multicheck-cancel {
        border: 1px solid #0a3c59;
        border-radius: 3px;
        color: #06426c;
        border-width: 1px; 
    }
    .rg-multicheck-accept:hover {
        background-color: #888
    }
    .rg-multicheck-cancel:hover {
        background-color: #888
    }
    .rg-multicheck-select {
        background:#40ff0b;
        color:#ffffff;
    }
    .rg-multicheck-list {
    }
    .rg-multicheck-item {
        background:none;
        color:none;
    }
    .rg-multicheck-item:hover {
        background:rgba(0, 0, 255, 0.2);
        color:none;
    }
    .rg-multicheck-selectitem {
        background:rgba(0, 0, 255, 0.2);
        color:#000;
    }
 
    /*              */
    /*    Popup     */
    /*              */
    .rg-popup-menu {
        background: #ffeeb6;
        border: 1px solid rgb(200, 200, 200);
        box-shadow: rgba(0, 0, 0, 0.8) 1px 2px 5px;
        font-family: 나눔고딕코딩;
        font-style: normal;
        font-variant: normal;
        font-weight: normal;
        font-size: 10pt;
        padding: 4px;
        margin: 0px;
    }
 
    .rg-popup-item {
        padding-top: 2px;
        padding-bottom: 2px;
        height: 20px;
        cursor: pointer;
    }
 
    .rg-popup-item:hover {
        background-color: #ffd8d8;
    }
 
    .rg-popup-separator-hr {
        height: 1px;
        border: 0px;
        margin: 2px;
        color: #777;
        background-color: #777;
    }
 
    .rg-popup-expander {
        background-image: url("/resource/image/icon/menu_expander.png");
        background-repeat: no-repeat;
        background-position: center center;
    }
 
    .rg-popup-check {
        /*
        background-image:url("/resource/image/icon/menu_uncheck.png");
        background-repeat : no-repeat;
        background-position : center center;
        */
    }
 
    .rg-popup-check-checked {
        background-image: url("/resource/image/icon/menu_check.png");
        background-repeat: no-repeat;
        background-position: center center;
    }
 
    .rg-popup-radio {
        /*
        background-image:url("/resource/image/icon/menu_unradio.png");
        background-repeat : no-repeat;
        background-position : center center;
        */
    }
 
    .rg-popup-radio-checked {
        background-image: url("/resource/image/icon/menu_radio.png");
        background-repeat: no-repeat;
        background-position: center center;
    }
 
    .rg-popup-group1 {
        background: #ffd800;
    }
 
    /*              */
    /*    date      */
    /*              */
    .rg-calendar {
        font-family: "나눔고딕코딩";
        font-size: 12px;
        background: #fff;
        border: 1px solid rgba(50, 50, 50, 1);
        box-shadow: rgba(0, 0, 0, 0.8) 1px 2px 5px;
    }
 
    .rg-cal-header {
        height: 20px;
    }
 
    .rg-cal-year {
        cursor: default;
        top: 2px;
    }
 
    .rg-cal-month {
        cursor: pointer;
        top: 2px;
    }
 
    .rg-cal-prev-month {
        background-image: url("/resource/image/icon/cal_prev.png");
        width: 20px;
        height: 20px;
    }
 
    .rg-cal-prev-month:hover {
        background-image: url("/resource/image/icon/cal_prev_hover.png");
    }
 
    .rg-cal-prev-month:active {
        background-image: url("/resource/image/icon/cal_prev_active.png");
    }
 
    .rg-cal-next-month {
        background-image: url("/resource/image/icon/cal_next.png");
        width: 20px;
        height: 20px;
    }
 
    .rg-cal-next-month:hover {
        background-image: url("/resource/image/icon/cal_next_hover.png");
    }
 
    .rg-cal-next-month:active {
        background-image: url("/resource/image/icon/cal_next_active.png");
    }
 
    .rg-cal-today-button {
        font-size: 12px;
        font-family: "나눔고딕코딩";
        border: 1px solid transparent;
        border-radius: 3px;
        cursor: pointer;
    }
 
    .rg-cal-today-button:hover {
        border: 1px solid #aaa;
        background-color: #fff;
        text-decoration: underline;
    }
 
    .rg-cal-today-button:active {
    }
 
    .rg-cal-next-year {
        background-image: url("/resource/image/icon/cal_up.png");
    }
 
    .rg-cal-next-year:hover {
        background-image: url("/resource/image/icon/cal_up_hover.png");
    }
 
    .rg-cal-next-year:active {
        background-image: url("/resource/image/icon/cal_up_active.png");
    }
 
    .rg-cal-prev-year {
        background-image: url("/resource/image/icon/cal_down.png");
    }
 
    .rg-cal-prev-year:hover {
        background-image: url("/resource/image/icon/cal_down_hover.png");
    }
 
    .rg-cal-prev-year:active {
        background-image: url("/resource/image/icon/cal_down_active.png");
    }
 
    .rg-cal-weeks {
        color: black;
        font-size: 12px;
        font-family: "나눔고딕코딩";
        cursor: default;
    }
 
    .rg-cal-week-sun {
        color: red;
    }
 
    .rg-cal-week-sat {
        color: blue;
    }
 
    .rg-cal-days {
        font-family: "나눔고딕코딩";
        font-size: 12px;
        text-align: center;
    }
 
    .rg-cal-day {
        cursor: pointer;
        background: #f5f5f5;
        border: 1px solid #eee;
        width: 30px;
        height: 30px;
        border-radius: 7px;
        font-family: "나눔고딕코딩";
        font-size: 12px;
    }
 
    .rg-cal-day:hover {
        background: #55FFf5;
        color: red;
        border: 1px solid #eee;
    }
 
    .rg-cal-prev-day {
        color: #ccc;
        border: 1px solid #fff;
    }
 
    .rg-cal-next-day {
        color: #ccc;
        border: 1px solid #fff;
    }
 
    .rg-cal-today {
        background: #d5d5d5;
    }
 
    .rg-cal-focusday {
        background: rgba(255, 255, 0, 0.3);
        border: 1px solid #aaa;
        color: #333;
    }
 
    .rg-cal-month-picker {
        margin: 0px;
        cursor: pointer;
        background: #fff;
        border: 1px solid rgba(50, 50, 50, 0.5);
        box-shadow: rgba(0, 0, 0, 0.5) 1px 2px 5px;
        font-family: "나눔고딕코딩";
        font-size: 12px;
        font-style: normal;
        font-variant: normal;
        font-weight: normal;
    }
 
    .rg-cal-month-picker-month {
        padding: 1px 4px 1px 4px;
        width: 20px;
        height: 20px;
        border-radius: 7px;
        text-align: center;
    }
 
    .rg-cal-month-picker-month:hover {
        background: #e8e8e8;
    }
 
    /*              */
    /*   dropDown   */
    /*              */
    .rg-dropdownlist {
        background: #fff;
        font-family: 나눔고딕코딩;
        border: 1px solid rgb(50, 50, 50);
        box-shadow: rgba(0, 0, 0, 0.8) 1px 2px 5px;
        font-size: 10pt;
        padding: 0px;
        margin: 0px;
    }
 
    .rg-dropdown-select {
        background: #fffa00;
        margin: 2px;
    }
 
    .rg-dropdown-item {
        margin: 2px;
    }
 
    .rg-dropdown-item:hover {
        background: #88ff88;
    }
</style>
```