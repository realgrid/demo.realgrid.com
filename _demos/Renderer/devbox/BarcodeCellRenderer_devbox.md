#### 바코드 타입

현재 "Code128", "Code39" 심볼 타입의 기본 기능을 지원합니다.

* [Code128](http://help.realgrid.com/api/types/Code128CellRenderer/) Code128 Barcode를 표시하는 렌더러입니다.
* [Code39](http://help.realgrid.com/api/types/Code39CellRenderer/) Code39 Barcode를 표시하는 렌더러입니다.

#### 바코드 렌더러 적용

`Code128` 컬럼에 Code128 Barcode를 적용시킵니다.  

```js
gridView.setColumnProperty("OrderID2", "renderer", {type:"code128"});

gridView.setColumnProperty("Country2", "renderer", {type:"code128"});
gridView.setColumnProperty("Country2", "styles", {figureBackground: "#ff111111"});
```

`Code39` 컬럼에 Code39 Barcode 적용시킵니다.  

<a class="btn primary small round lowercase" id="btnCode39">바코드 적용</a>

```js
gridView.setColumnProperty("CustomerID2", "renderer", {type:"code39"});
gridView.setColumnProperty("CustomerID2", "styles", {figureBackground: "#ff000088"});
```


<script>
$('#btnCode39').click(function() {
	gridView.setColumnProperty("CustomerID2", "renderer", {type:"code39"});
	gridView.setColumnProperty("CustomerID2", "styles", {figureBackground: "#ff000088"});
});
</script>