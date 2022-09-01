#### 동적 스타일 설정

styleCallback 속성으로 셀에 동적 className을 추가합니다.
<a class="btn primary small round lowercase" id="btnSetStyleCallback">동적 스타일 적용</a>

index.columns, index.rows 는 json형태로 넘어옵니다.

```js
var styleCallback = function(pivot, index, value){
    if (index.rows["국가"] === "국산" && index.rows["브랜드명"] === "기아" && index.valueField === "차량가격") {
        var st = 'background';
        if (value < 10000) {
            st += '-low';
        } else if (value > 50000) {
            st += '-high';
        }
        return st;
    }
};

pivot.setDisplayOptions({styleCallback: styleCallback});
pivot.drawView();
```


<script>
	$('#btnSetStyleCallback').click(function() {	
	    var styleCallback = function(pivot, index, value){
	        if (index.rows["국가"] === "국산" && index.rows["브랜드명"] === "기아" && index.valueField === "차량가격") {
	            var st = 'background';
	            if (value < 10000) {
	                st += '-low';
	            } else if (value > 50000) {
	                st += '-high';
	            }
	            return st;
	        }
	    };

	    pivot.setDisplayOptions({styleCallback: styleCallback});
	    pivot.drawView();
    });
</script>