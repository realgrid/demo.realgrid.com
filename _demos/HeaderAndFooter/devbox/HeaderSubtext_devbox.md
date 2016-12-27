#### 헤더 추가 문자열

- `subText`: 컬럼 헤더에 추가로 표시할 문자열을 지정합니다.
- `subTextGap`: 헤더 text와의 간격을 pixel 단위로 설정합니다.
- `subTextLocation`: 헤더 text를 기준으로 표시할 위치를 지정합니다.
- `subStyle`: 추가 문자열에 적용할 스타일을 지정합니다.

Help 사이트의 [subTextLocation](http://help.realgrid.com/api/types/subTextLocation/){:target="_blank"} 참고 바랍니다.  
스타일 속성에 대한 추가 설명은 [스타일 속성]({{ "/GridStyle/StyleProperties/" | prepend: site.baseurl }}) 참고 바랍니다.

subTextLocation 과 subTextGap 는 별도로 지정하지 않을 경우 HeaderOptions에서 지정한 값으로 사용됩니다.

<script>

  $('#btnSetImageLocationRight').click(function() {
    gridView.setColumnProperty("Country Column", "header", {imageLocation: "right"});
  });

  $('#btnSetImageLocationLeft').click(function() {
    gridView.setColumnProperty("Country Column", "header", {imageLocation: "left"});
  });

</script>
