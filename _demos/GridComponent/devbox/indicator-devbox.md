#### 인디케이터를 설정하는 방법
인디케이터의 설정을 변경하는 것은 [setIndicator()](http://help.realgrid.com/api/GridBase/setIndicator/)를 사용 합니다.   
현재 설정된 상태를 확인하는 것은 [getIndicator()](http://help.realgrid.com/api/GridBase/getIndicator/)을 사용 합니다.  

#### 인디케이터의 화면 표시여부를 지정   

- `visible`: 인디케이터 영역의 화면 표시여부를 지정합니다. 

<a class="btn primary small round lowercase" id="btnSetVisibleFalse">표시하지 않음</a>

```js
gridView.setIndicator({
  visible: false  
});
```

<a class="btn primary small round lowercase" id="btnSetVisibleTrue">표시</a>

```js
gridView.setIndicator({
  visible: true  
});
```


#### 인디케이터의 표시 값(displayValue)을 변경하는 방법  

- `none`: 값을 표시 하지 않습니다.  
- `index`: 1부터 시작하여 순서대로 표시합니다. (정렬에 무관하게 1번부터 시작)  
- `row`: Row의 고유번호를 표시합니다. (정렬에 따라서 섞여서 표시)  

<a class="btn primary small round lowercase" id="btnSetDisplayValueNone">표시하지 않음</a>

```js
gridView.setIndicator({
  displayValue: "none"  
});
```

<a class="btn primary small round lowercase" id="btnSetDisplayValueIndex">순번으로 표시</a>

```js
gridView.setIndicator({
  displayValue: "index"  
});
```

<a class="btn primary small round lowercase" id="btnSetDisplayValueRow">Row의 고유번호로 표시</a>

```js
gridView.setIndicator({
  displayValue: "row"  
});
```

#### Zero Base
기본적으로 인디케이터에 표시되는 값은 1부터 시작합니다. 이 값을 0부터 시작하고자 할때 `zeroBase` 속성을 True로 설정합니다.  

- `zeroBase`: true 인 경우 인디케이터 값은 0부터 시작합니다.  

<a class="btn primary small round lowercase" id="btnSetZeroBaseTrue">0부터 시작</a>

```js
gridView.setIndicator({
  zeroBase: true  
});
```

<a class="btn primary small round lowercase" id="btnSetZeroBaseFalse">1부터 시작</a>

```js
gridView.setIndicator({
  zeroBase: false  
});
```

#### Head/Foot
인디케이터의 헤드와 풋 영역에 글자나 이미지를 표시할 수 있습니다.

- `headText`: head 영역에 표시할 text를 지정한다.    
- `footText`: foot 영역에 표시할 text를 지정한다.   
- `headImageUrl`: head 영역에 표시할 이미지의 Url을 지정한다.  
- `footImageUrl`: foot 영역에 표시할 이미지의 Url을 지정한다.  

<a class="btn primary small round lowercase" id="btnSetText">Text 표시</a>

```js
gridView.setIndicator({
  headText: "head",  
  footText: "foot",
  headImageUrl: null,  
  footImageUrl: null  
});
```

<a class="btn primary small round lowercase" id="btnSetImage">Image 표시</a>

```js
gridView.setIndicator({
  headText: null,  
  footText: null,
  headImageUrl: "/resource/image/common/dot_arrow2_top.gif",  
  footImageUrl: "/resource/image/common/dot_arrow2_bottom.gif"  
});
```


<script>

  $('#btnSetVisibleFalse').click(function() {
    gridView.setIndicator({
      visible: false  
    });
  });

  $('#btnSetVisibleTrue').click(function() {
    gridView.setIndicator({
      visible: true  
    });
  });

  $('#btnSetDisplayValueNone').click(function() {
    gridView.setIndicator({
      displayValue: "none"  
    });
  });

  $('#btnSetDisplayValueIndex').click(function() {
    gridView.setIndicator({
      displayValue: "index"  
    });
  });

  $('#btnSetDisplayValueRow').click(function() {
    gridView.setIndicator({
      displayValue: "row"  
    });
  });

  $('#btnSetZeroBaseTrue').click(function() {
    gridView.setIndicator({
      zeroBase: true  
    });
  });  

  $('#btnSetZeroBaseFalse').click(function() {
    gridView.setIndicator({
      zeroBase: false  
    });
  });

   $('#btnSetText').click(function() {
    gridView.setIndicator({
      headText: "head",  
      footText: "foot",
      headImageUrl: null,  
      footImageUrl: null  
    });
  });

  $('#btnSetImage').click(function() {
    gridView.setIndicator({
      headText: null,  
      footText: null,
      headImageUrl: "{{"/resource/image/common/" | prepend: site.baseurl}}" + "/dot_arrow2_top.gif",  
      footImageUrl: "{{"/resource/image/common/" | prepend: site.baseurl}}" + "/dot_arrow2_bottom.gif"  
    });
  });  

</script>
