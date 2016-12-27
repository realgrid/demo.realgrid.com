#### 헤더 이미지

- `imageLocation`: 헤더 이미지의 위치를 지정합니다.
- `imageUrl`: 컬럼 헤더에 불러올 이미지의 경로를 지정합니다.

```js
var columns = [{
    "name": "Country Column",
    "fieldName": "Country",
    "width": 90,
    "header": {
        "text": "Country",
        "imageLocation": "right",
        "imageUrl": "/img/common/realgridsmall.png"
    }
  }]
```

<a class="btn primary small round lowercase" id="btnSetImageLocationRight">헤더 이미지 오른쪽으로</a>
<a class="btn primary small round lowercase" id="btnSetImageLocationLeft">헤더 이미지 왼쪽으로</a>

```js
  gridView.setColumnProperty(
    "Country Column",
    "header",
    { imageLocation: "right" }
  );
```

<script>

  $('#btnSetImageLocationRight').click(function() {
    gridView.setColumnProperty("Country Column", "header", {imageLocation: "right"});
  });

  $('#btnSetImageLocationLeft').click(function() {
    gridView.setColumnProperty("Country Column", "header", {imageLocation: "left"});
  });

</script>
