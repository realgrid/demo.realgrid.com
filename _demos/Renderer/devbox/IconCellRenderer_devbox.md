#### RealGrid의 Image List

그리드뷰(GridView) 또는 트리뷰(TreeView)에서 이미지를 사용하려면 먼저, [ImageList](http://help.realgrid.com/api/types/ImageList/)객체를 이용해 이미지파일의 경로를 목록으로 만들어야 합니다.

```js
var imgs = new RealGridJS.ImageList("images1", "/demo/resource/image/icon/");
    imgs.addUrls([
        "be.png",
        "br.png",
        "fr.png",
        "de.png",
        "us.png"
    ]);

gridView.registerImageList(imgs);
```

위 코드는 실제로 왼쪽 데모 화면에서 그리드뷰(GridView)에 아이콘을 적용하기 위해 이미지 목록을 만들고 트리에 등록하는 코드입니다.  
이미지 목록을 트리에 등록하고 사용하려면

* [GridBase.registerImageList()](http://help.realgrid.com/api/GridView/registerImageList/)

함수를 사용하면 됩니다.

#### 아이콘 스타일

아이콘을 표시할 때 사용되는 스타일 속성들입니다.

[IconLocation](http://help.realgrid.com/api/types/IconLocation/)을 사용해서 아이콘의 위치를 변경 할 수 있습니다.  
(기본 값은 "left"입니다.)  

* `iconIndex` - ImageList에서 표시될 아이콘의 인덱스.
* `iconLocation` - 아이콘을 표시할 위치. ("left", "right", "top", "bottom" )
* `iconAlignment` - 아이콘 정렬 상태. ("near", "far", "center")
* `iconOffset` - 위치별 시작점과 아이콘 사이의 간격.
* `iconPadding` - 아이콘과 텍스트 사이의 간격.


#### 아이콘 표시하기

그리드뷰(GridView)에는 각 컬럼에 아이콘을 표시할 수 있습니다.

`LEFT` 컬럼에 이미지 리스트의 iconIndex가 0인 아이콘을 동일하게 표시합니다.

<a class="btn primary small round lowercase" id="btnSetIcon">아이콘 표시</a>

```js
//아이콘 리스트 및 이름 생성
var imgs = new RealGridJS.ImageList("images1", "/demo/resource/image/icon/");
    imgs.addUrls([
        "be.png",
        "br.png",
        "fr.png",
        "de.png",
        "us.png"
    ]);

gridView.registerImageList(imgs);

//이미지 리스트에서 사용할 이름 설정
gridView.setColumnProperty("left","imageList", "images1");

//아이콘 타입의 렌더러 설정
gridView.setColumnProperty("left","renderer",{type:"icon"}); 

//아이콘 적용 설정
gridView.setColumnProperty("left","styles", {
    textAlignment: "near",
    iconIndex: 0,
    iconLocation: "left",
    iconAlignment: "center",
    iconOffset: 4,
    iconPadding: 4
});

```

#### 동적 아이콘 표시하기

[dynamicStyles](http://help.realgrid.com/api/types/DynamicStyle/)를 사용해서 동적으로 값에 따른 아이콘 표시를 할 수 있습니다.

아이콘 표시하는 방법 까지는 설정이 동일하며 추가로 [dynamicStyles](http://help.realgrid.com/api/types/DynamicStyle/)가 적용됩니다.  

`RIGHT`컬럼에 동적으로 값에 따라 아이콘이 변경되는 동적 아이콘을 표시합니다.   
(iconIndex값이 -1 이면 아이콘을 표시하지 않습니다.)

<a class="btn primary small round lowercase" id="btnSetDynamicIconRight">RIGHT 아이콘 표시</a> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<a class="btn primary small round lowercase" id="btnSetDynamicIconTop">TOP 아이콘 표시</a>  

<a class="btn primary small round lowercase" id="btnSetDynamicIconBottom">BOTTOM 아이콘 표시</a>&nbsp;&nbsp;&nbsp;&nbsp;
<a class="btn primary small round lowercase" id="btnSetDynamicIconCenter">CENTER 아이콘 표시</a>

각 컬럼에 아이콘 렌더러 적용 후 동적 아이콘 변경을 확인하기 위해 컬럼의 값을 변경해 보세요.

```js
//아이콘 표시방법 동일

//dynamicStyles 생성
var iconStyles = [{
    criteria: "value='Belgium'",
    styles: "iconIndex=0"
}, {
    criteria: "value='Brazil'",
    styles: "iconIndex=1"
}, {
    criteria: "value='France'",
    styles: "iconIndex=2"
}, {
    criteria: "value='Germany'",
    styles: "iconIndex=3"
}, {
    criteria: "value='USA'",
    styles: "iconIndex=4"
}, {
    criteria: "values['Country'] is empty",
    styles: "iconIndex=-1"
}];

//dynamicStyle 적용
gridView.setColumnProperty("right","dynamicStyles", iconStyles);
```

#### 텍스트 없이 아이콘만 표시

아이콘 렌더러 적용 시 텍스트는 감추고 아이콘만 표시하는 방법은 renderer의 `textVisible`속성을 false로 설정하면 됩니다.

<a class="btn primary small round lowercase" id="btnTextVisible">아이콘만 표시</a>

```js
renderer: {
    type: "icon",
    textVisible: false //텍스트 표시 여부
}
```



<script>
$('#btnSetIcon').click(function() {
	var imgs = new RealGridJS.ImageList("images1", "/demo/resource/image/icon/");
    imgs.addUrls([
        "be.png",
        "br.png",
        "fr.png",
        "de.png",
        "us.png"
    ]);

	gridView.registerImageList(imgs);
	gridView.setColumnProperty("left","imageList", "images1");
	gridView.setColumnProperty("left","renderer",{type:"icon"});
	gridView.setColumnProperty("left","styles", {
	    textAlignment: "near",
	    iconIndex: 0,
	    iconLocation: "left",
	    iconAlignment: "center",
	    iconOffset: 4,
	    iconPadding: 4
	});
});

$('#btnSetDynamicIconRight').click(function() {
	//아이콘 리스트 및 이름 생성
	var imgs = new RealGridJS.ImageList("images1", "/demo/resource/image/icon/");
	    imgs.addUrls([
	        "be.png",
	        "br.png",
	        "fr.png",
	        "de.png",
	        "us.png"
	    ]);

	gridView.registerImageList(imgs);

	//이미지 리스트에서 사용할 이름 설정
	gridView.setColumnProperty("right","imageList", "images1");

	//아이콘 타입의 렌더러 설정
	gridView.setColumnProperty("right","renderer",{type:"icon"}); 

	//아이콘 적용 설정
	gridView.setColumnProperty("right","styles", {
	    textAlignment: "near",
	    iconIndex: 0,
	    iconLocation: "right",
	    iconAlignment: "center",
	    iconOffset: 4,
	    iconPadding: 4
	});

	//dynamicStyles 생성
	var iconStyles = [{
	    criteria: "value='Belgium'",
	    styles: "iconIndex=0"
	}, {
	    criteria: "value='Brazil'",
	    styles: "iconIndex=1"
	}, {
	    criteria: "value='France'",
	    styles: "iconIndex=2"
	}, {
	    criteria: "value='Germany'",
	    styles: "iconIndex=3"
	}, {
	    criteria: "value='USA'",
	    styles: "iconIndex=4"
	}, {
	    criteria: "values['Country'] is empty",
	    styles: "iconIndex=-1"
	}];

	//dynamicStyle 적용
	gridView.setColumnProperty("right","dynamicStyles", iconStyles);
});

$('#btnSetDynamicIconTop').click(function() {
	//아이콘 리스트 및 이름 생성
	var imgs = new RealGridJS.ImageList("images1", "/demo/resource/image/icon/");
	    imgs.addUrls([
	        "be.png",
	        "br.png",
	        "fr.png",
	        "de.png",
	        "us.png"
	    ]);

	gridView.registerImageList(imgs);

	//이미지 리스트에서 사용할 이름 설정
	gridView.setColumnProperty("top","imageList", "images1");

	//아이콘 타입의 렌더러 설정
	gridView.setColumnProperty("top","renderer",{type:"icon"}); 

	//아이콘 적용 설정
	gridView.setColumnProperty("top","styles", {
	    textAlignment: "center",
	    iconIndex: 0,
	    iconLocation: "top",
	    iconAlignment: "center",
	    iconOffset: 4,
	    iconPadding: 4
	});

	//dynamicStyles 생성
	var iconStyles = [{
	    criteria: "value='Belgium'",
	    styles: "iconIndex=0"
	}, {
	    criteria: "value='Brazil'",
	    styles: "iconIndex=1"
	}, {
	    criteria: "value='France'",
	    styles: "iconIndex=2"
	}, {
	    criteria: "value='Germany'",
	    styles: "iconIndex=3"
	}, {
	    criteria: "value='USA'",
	    styles: "iconIndex=4"
	}, {
	    criteria: "values['Country'] is empty",
	    styles: "iconIndex=-1"
	}];

	//dynamicStyle 적용
	gridView.setColumnProperty("top","dynamicStyles", iconStyles);
});

$('#btnSetDynamicIconBottom').click(function() {
	//아이콘 리스트 및 이름 생성
	var imgs = new RealGridJS.ImageList("images1", "/demo/resource/image/icon/");
	    imgs.addUrls([
	        "be.png",
	        "br.png",
	        "fr.png",
	        "de.png",
	        "us.png"
	    ]);

	gridView.registerImageList(imgs);

	//이미지 리스트에서 사용할 이름 설정
	gridView.setColumnProperty("bottom","imageList", "images1");

	//아이콘 타입의 렌더러 설정
	gridView.setColumnProperty("bottom","renderer",{type:"icon"}); 

	//아이콘 적용 설정
	gridView.setColumnProperty("bottom","styles", {
	    textAlignment: "center",
	    iconIndex: 0,
	    iconLocation: "bottom",
	    iconAlignment: "center",
	    iconOffset: 4,
	    iconPadding: 4
	});

	//dynamicStyles 생성
	var iconStyles = [{
	    criteria: "value='Belgium'",
	    styles: "iconIndex=0"
	}, {
	    criteria: "value='Brazil'",
	    styles: "iconIndex=1"
	}, {
	    criteria: "value='France'",
	    styles: "iconIndex=2"
	}, {
	    criteria: "value='Germany'",
	    styles: "iconIndex=3"
	}, {
	    criteria: "value='USA'",
	    styles: "iconIndex=4"
	}, {
	    criteria: "values['Country'] is empty",
	    styles: "iconIndex=-1"
	}];

	//dynamicStyle 적용
	gridView.setColumnProperty("bottom","dynamicStyles", iconStyles);
});

$('#btnSetDynamicIconCenter').click(function() {
	//아이콘 리스트 및 이름 생성
	var imgs = new RealGridJS.ImageList("images1", "/demo/resource/image/icon/");
	    imgs.addUrls([
	        "be.png",
	        "br.png",
	        "fr.png",
	        "de.png",
	        "us.png"
	    ]);

	gridView.registerImageList(imgs);

	//이미지 리스트에서 사용할 이름 설정
	gridView.setColumnProperty("center","imageList", "images1");

	//아이콘 타입의 렌더러 설정
	gridView.setColumnProperty("center","renderer",{type:"icon"}); 

	//아이콘 적용 설정
	gridView.setColumnProperty("center","styles", {
	    textAlignment: "near",
	    iconIndex: 0,
	    iconLocation: "center",
	    iconAlignment: "center",
	    iconOffset: 4,
	    iconPadding: 4
	});

	//dynamicStyles 생성
	var iconStyles = [{
	    criteria: "value='Belgium'",
	    styles: "iconIndex=0"
	}, {
	    criteria: "value='Brazil'",
	    styles: "iconIndex=1"
	}, {
	    criteria: "value='France'",
	    styles: "iconIndex=2"
	}, {
	    criteria: "value='Germany'",
	    styles: "iconIndex=3"
	}, {
	    criteria: "value='USA'",
	    styles: "iconIndex=4"
	}, {
	    criteria: "values['Country'] is empty",
	    styles: "iconIndex=-1"
	}];

	//dynamicStyle 적용
	gridView.setColumnProperty("center","dynamicStyles", iconStyles);
});

$('#btnTextVisible').click(function() {
	var imgs = new RealGridJS.ImageList("images1", "/demo/resource/image/icon/");
	    imgs.addUrls([
	        "be.png",
	        "br.png",
	        "fr.png",
	        "de.png",
	        "us.png"
	    ]);

	gridView.registerImageList(imgs);

	//이미지 리스트에서 사용할 이름 설정
	gridView.setColumnProperty("textVisible","imageList", "images1");

	//아이콘 타입의 렌더러 설정
	gridView.setColumnProperty("textVisible","renderer",{type:"icon", textVisible:false}); 

	//아이콘 적용 설정
	gridView.setColumnProperty("textVisible","styles", {
	    textAlignment: "near",
	    iconIndex: 0,
	    iconLocation: "right",
	    iconAlignment: "center",
	    iconOffset: 4,
	    iconPadding: 4
	});

	//dynamicStyles 생성
	var iconStyles = [{
	    criteria: "value='Belgium'",
	    styles: {
	    	iconIndex: 0,
	    	iconLocation: "left"
	    }
	}, {
	    criteria: "value='Brazil'",
	    styles: {
	    	iconIndex: 1,
	    	iconLocation: "right"
	    }
	}, {
	    criteria: "value='France'",
	    styles: {
	    	iconIndex: 2,
	    	iconLocation: "left"
	    }
	}, {
	    criteria: "value='Germany'",
	    styles: {
	    	iconIndex: 3,
	    	iconLocation: "right"
	    }
	}, {
	    criteria: "value='USA'",
	    styles: {
	    	iconIndex: 4,
	    	iconLocation: "left"
	    }
	}, {
	    criteria: "values['Country'] is empty",
	    styles: "iconIndex=-1"
	}];

	//dynamicStyle 적용
	gridView.setColumnProperty("textVisible","dynamicStyles", iconStyles);
});
</script>