---
layout: page
title: 스타일 속성
order: 3
devbox: false
published: true
categories:
  - 그리드 스타일
tags: ['Style', 'Dynamic Styles', 'Properties', '속성', '스타일', '동적스타일']
---

RealGrid의 각 데이터셀은 컬럼에 지정된 셀 렌더러에 의해 표시됩니다. 셀 렌더러는 실행 시간에 여러 계층을 통해 전달된 스타일 속성 셋을 이용하여 그리게 됩니다. 하나의 스타일 셋은 아래 표에 나열된 속성들을 갖습니다. 각 렌더러는 이들 중 자신이 필요한 값들을 가져가 사용합니다.

#### 색상 (color)
채우기나 보더 등에 지정하는 색상값은 "#AARRGGBB" 형식이나 "#RRGGBB" 형식으로 지정합니다. 두 번째일 경우 alpha 값은 0xFF 값으로 간주합니다.

#### 채우기 (fill)
background 등과 같은 채우기 속성의 값은 하나의 색상으로 지정하는 solid fill과, "linear,#aarrggbb,#aarrggbb,0" 형식으로 지정하는 linear gradient fill 로 지정할 수 있습니다. 네번째 값은 angle 입니다. 0에서 360미만 값으로 설정할 수 있습니다. 기본값은 0입니다.

#### 선 (stroke)
borderLeft 등과 같은 선 속성의 값은 "#aarrggbb,1" 형식으로 색상과 선의 두께를 지정합니다. 두께를 지정하지 않으면 1로 설정됩니다.

#### 폰트 (font)
폰트 속성 값은 "Arial,10,bold,italic,underline" 처럼 폰트명과 크기 그리고 폰트 속성들을 지정합니다. 속성들을 지정하지 않을 수 있습니다.

#### 스타일 속성

|속성명|타입|내용|
|:--|:--:|:--|
|**background**|	Fill|	셀의 배경색을 지정합니다. 이 속성은 모든 렌더러에 적용됩니다.|
|**border**|	Stroke|	panel에 표시된 셀 등에서 셀의 전체 경계선을 표시하는 경우에 사용됩니다. 데이터/헤더/푸터 셀 등에서는 사용하지 않습니다.|
|**borderLeft**|	Stroke|	셀의 왼쪽 경계선을 지정합니다.|
|**borderRight**|	Stroke|	셀의 오른쪽 경계선을 지정합니다.|
|**borderTop**|	Stroke|	셀의 위쪽 경계선을 지정합니다.|
|**borderBottom**|	Stroke|	셀의 아래쪽 경계선을 지정합니다.|
|**line**|  Stroke|	panel에 표시되는 셀들의 경계선 등 선을 표시할 때 사용됩니다.|
|**fontFamily**|	String|	폰트 이름을 지정합니다. 기본값은 "Tahoma"입니다.|
|**fontSize**|	Integer|	폰트 크기를 지정합니다. 기본값은 12입니다.|
|**fontBold**|	Boolean|	텍스트를 굵게 표시할 지를 지정합니다. 기본값은 false입니다.|
|**fontItalic**|	Boolean|	텍스트를 기울여서 표시할 지를 지정합니다. 기본값은 false입니다.|
|**fontUnderline**|	Boolean|	텍스트 아래 밑줄을 표시할 것인 지를 지정합니다. 기본값은 false입니다.|
|**fontLinethrough**|	Boolean|	취소선을 표시합니다. RealGridJS 1.1.35 이상 지원|
|**font**|	String|	위의 폰트 속성들을 한꺼번에 지정합니다. 예를 들어 "Arial,11,bold" 라고 지정하면 fontFamily는 "Arial", fontSize는 11, 그리고 fontBold가 true가 됩니다. 첫번째와 두번째 폰트 이름 및 크기는 반드시 지정합니다. bold, italic, underline은 지정하면 true가 됩니다.|
|**foreground**|	Fill|	텍스트의 색상을 지정합니다.|
|**textAlignment**|	Alignment|	텍스트의 수평 정렬 상태를 지정합니다. "near", "center", "far" 중 한 값을 지정합니다.|
|**lineAlignment**|	Alignment|	텍스트의 수직 정렬 상태를 지정합니다. "near", "center", "far" 중 한 값을 지정합니다.|
|**numberFormat**|	String|	number 형 값을 표시할 형식을 지정합니다.소수점 자리수 지정: "0.00" 처럼 형식에 소수점과 표시할 자리수만큼 "0"을 지정합니다.천자리수 지정: "#,###.00" 처럼 천자리수 위치에 ","를 지정합니다.채우기: "00.00" 처럼 정수부에 설정한 "0" 만큼 0으로 채워집니다.|
|**dateFormat**|	String|	이 속성 대신 아래의 datetimeFormat을 사용하십시오. 이 속성은 폐기될 예정입니다.datetime 형 값을 표시할 형식을 지정합니다.YYYY: 년, YY: 2000년 기준 년, MM:월, DD:일, HH:시간, NN:분, SS:초 의 조합으로 설정합니다.|
|**datetimeFormat**|	String|	datetime 형 값을 표시할 형식을 지정합니다.자세한 설명은 DataType을 참조하십시오.|
|**booleanFormat**|	String|	boolean 형 값을 표시할 형식을 지정합니다."거짓말;참말"과 같이 세미콜론(;)이나 콜론(:)으로 분리하여 false/true 값을 지정합니다. 자세한 설명은 DataType을 참조하십시오.|
|**prefix**|	String|	값의 앞쪽에 덧붙여 표시할 텍스트를 지정합니다.|
|**postfix**|	String|	suffix 를 대신 사용하십시오.|
|**suffix**|	String|	값의 뒤쪽에 덧붙여 표시할 텍스트를 지정합니다.|
|**paddingLeft**|	Integer|	렌더러가 표시할 영역과 셀 사이의 왼쪽 간격입니다.|
|**paddingRight**|	Integer|	렌더러가 표시할 영역과 셀 사이의 오른쪽 간격입니다.|
|**paddingTop**|	Integer|	렌더러가 표시할 영역과 셀 사이의 위쪽 간격입니다.|
|**paddingBottom**|	Integer|	렌더러가 표시할 영역과 셀 사이의 아래쪽 간격입니다.|
|**iconIndex**|	Integer|	렌더러가 표시할 영역과 셀 사이의 왼쪽 간격입니다.|
|**iconLocation**|	IconLocation|	아이콘이 표시되는 셀에서 아이콘을 표시할 위치를 지정합니다."left", "right", "top", "bottom", "center", "none" 들 중에서 지정합니다.|
|**iconAlignment**|	Alignment|	아이콘의 정렬 상태를 "near", "center", "far" 중 한 값으로 지정합니다.|
|**iconOffset**|	Integer|	iconAlignment로 지정한 위치에서 얼만큼 비켜나 표시할 것인 지를 지정합니다.|
|**iconPadding**|	Integer|	icon과 텍스트 등 사이의 간격을 지정합니다.|
|**contentFit**|	ContentFit|	이미지 등을 표시할 때 크기를 셀에 어떻게 맞출 것인 지를 지정합니다."none", "center", "both", "width", "height", "auto" 중에서 지정합니다.|
|**hoveredBackground**|	Fill|	마우스가 올라간 셀의 배경 속성을 지정합니다.|
|**hoveredForeground**|	Fill|	마우스가 올라간 셀의 텍스트 색상을 지정합니다.|
|**figureBackground**|	Fill|	이미지 외에 렌더러가 직접 표시하는 도형 등의 배경색을 지정합니다.|
|**figureInactiveBackground**|	Fill|	이미지 외에 렌더러가 직접 표시하는 도형 등의 비활성시 배경색을 지정합니다.|
|**figureBorder**|	Stroke|	도형 등의 경계선을 지정합니다.|
|**figureSize**|	Dimension|	도형 등의 크기를 지정합니다. "20" 처럼 고정 값으로 지정하거나, "50%" 처럼 셀의 크기에 대한 비율값으로 지정할 수 있습니다.|
|**figureName**|	String|	표시되는 도형 등의 종류가 하나 이상일 때 표시할 도형의 이름을 지정합니다.|
|**figureState**|	String|	상태를 갖는 복잡한 도형일 경우 그 상태값을 지정합니다.|

