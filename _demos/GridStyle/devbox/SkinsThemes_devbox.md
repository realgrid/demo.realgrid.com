
#### 태마 설정하기

태마 선택: 
<select id="selGridTheme">
	<option selected="selected">basicBlueSkin</option>
	<option>OfficeBlueSkin</option>
	<option>OrangeGlowSkin</option>
	<option>basicBlackSkin</option>
	<option>goldenBlackSkin</option>
	<option>blackMambaSkin</option>
	<option>allBlackSkin</option>
	<option>basicGrayBlueSkin</option>
	<option>basicGreenSkin</option>
	<option>basicVioletSkin</option>
	<option>blueSkySkin</option>
	<option>deepGreenSkin</option>
	<option>espressoSkin</option>
	<option>moonlitSkin</option>
	<option>generalBlueSkin</option>
	<option>generalGreenSkin</option>
	<option>generalGraySkin</option>
	<option>generalGreenYellowSkin</option>
	<option>generalNavySkin</option>
	<option>generalOrangeSkin</option>
	<option>generalRedSkin</option>
	<option>generalYellowSkin</option>
	<option>generalGraySkin</option>
	<option>glowBlueSkin</option>
	<option>glowDarkGraySkin</option>
	<option>generalRedWineSkin</option>
	<option>glowGreenSkin</option>
	<option>glowGreenYellowSkin</option>
	<option>glowNavySkin</option>
	<option>glowOrangeSkin</option>
	<option>glowRedSkin</option>
	<option>glowRedWineSkin</option>
	<option>glowYellowSkin</option>
	<option>waveLightBlueSkin</option>
	<option>waveDarkBlueSkin</option>
	<option>officeGraySkin</option>
	<option>officeGoldSkin</option>
	<option>officeSilverSkin</option>
	<option>generalDarkGraySkin</option>
</select>

<a class="btn primary small round lowercase" id="btnSetTheme">태마 적용</a>


```js
var skins = $('#selGridTheme').val();
gridView.setStyles(eval(skins));
```

#### 스킨파일 예제

basicBlueSkin.js

```js
var basicBlueSkin = {  
   "grid":{  
      "foreground":"#ff000000",
      "iconOffset":"0",
      "paddingRight":"2",
      "paddingTop":"2",
      "background":"#ffffffff",
      "paddingBottom":"2",
      "iconPadding":"0",
      "fontFamily":"돋움",
      "border":"#ff84a3c0,1",
      "selectedBackground":"#ff696969",
      "contentFit":"auto",
      "inactiveBackground":"#ffd3d3d3",
      "line":"#ffa6b9ca,1",
      "selectionDisplay":"mask",
      "selectedForeground":"#ffffffff",
      "textAlignment":"near",
      "hoveredMaskBackground":"#1f5292f7",
      "iconIndex":"0",
      "hoveredMaskBorder":"#335292f7,1",
      "figureBackground":"#ff6f9ac5",
      "borderBottom":"#ffc9d5e0,1",
      "iconLocation":"left",
      "inactiveForeground":"#ff808080",
      "iconAlignment":"center",
      "lineAlignment":"center"
   },
   "panel":{ 
      ...
   },
   ...
}
```


<script>
  $('#btnSetTheme').click(function() {
  	var skin = $('#selGridTheme').val();
    gridView.setStyles(eval(skin));
  });
  </script>