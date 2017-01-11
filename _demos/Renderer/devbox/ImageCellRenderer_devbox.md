#### 이미지 렌더러 설정

[ImageCellRenderer](http://help.realgrid.com/api/types/ImageCellRenderer/)]는 데이터 셀의 값을 이미지 url로 해석해서 그 이미지를 내려받고 표시합니다.

컬럼 스타일 `contentFit` 값으로 이미지의 위치와 크기가 결정됩니다. 

ContentFit 상수 중 하나로 설정합니다.

* "center" - 이미지 크기는 변경하지 않고 셀 중앙에 위치 시킵니다.
* "both" - 이미지의 너비와 높이를 셀 크기에 맞춥니다. 이미지가 왜곡됩니다.
* "width" - 이미지의 높이는 그냥 두고 너비만 셀 크기에 맞춥니다. 이미지가 왜곡됩니다.
* "height" - 이미지의 너비는 그냥 두고 높이만 셀 크기에 맞춥니다. 이미지가 왜곡됩니다.
* "auto" - 이미지의 비율을 유지한 채로 셀 크기에 맞춥니다.
* "none" - 이미지 크기나 위치를 변경하지 않습니다. 크기대로 왼쪽 상단에서부터 표시됩니다.

```js
styles: {
    contentFit: "center"
}
```

렌더러의 `smoothing` 속성으로 이미지 크기 변경 후 처리 방법을 지정합니다.

* `smoothing` - 실제 이미지보다 크게 그릴 때 보정하여 그립니다.


```js
renderer: {
	type: "image",
	smoothing: true
}
```


#### 이미지 표시하기

컬럼 renderer의 type을 "image"로 설정하면 데이터 셀의 값을 이미지 url로 해석해서 그 이미지를 내려받고 표시합니다. 

추가로 styles 속성의 `contentFit` 설정으로 이미지의 위치가 크기를 설정합니다. 

<a class="btn primary small round lowercase" id="btnSetImageNormalFlag1">이미지 표시</a>

```js
//이미지 렌더러 설정
gridView.setColumnProperty("NormalFlag1", "renderer", {type: "image", sommthing: true});

//이미지의 위치와 크기가 결정
gridView.setColumnproperty("NormalFlag1", "styles", {contentFit: "none"});
```

<script>
$('#btnSetImageNormalFlag1').click(function() {
	gridView.setColumnProperty("NormalFlag1", "renderer", {type: "image", sommthing: true})
	gridView.setColumnProperty("NormalFlag2", "renderer", {type: "image", sommthing: true})
	gridView.setColumnProperty("NormalFlag3", "renderer", {type: "image", sommthing: true})
	gridView.setColumnProperty("NormalFlag4", "renderer", {type: "image", sommthing: true})
	gridView.setColumnProperty("NormalFlag5", "renderer", {type: "image", sommthing: true})
	gridView.setColumnProperty("NormalFlag6", "renderer", {type: "image", sommthing: true})
});
</script>