# RealGrid DEMO 사이트

## Architectures

### Frameworks

- Jekyll 3.2.1
- github pages

### Libraries

- realgrid
- jquery
- bootstrap

## Development

### 저장소

- 개발 저장소(Private) : https://github.com/realgrid/demo.realgrid.com.git

### 메뉴 카테고리 구분

- 카테고리 없는 일반 페이지
  - 카테고리 없는 일반페이지는 어디에서든 *.md 또는 *.html 등의 파일로 만들고 page를 layout으로 정해주면 된다.
  - 카테고리 없는 일반페이지는 왼쪽 메뉴의 상단에 표시되며 순서는 order 머릿말에 의해 결정된다.
- 카테고리로 구분된 demo 페이지
  - 왼쪽 메뉴 카테고리는 _config.yml 파일에 categories 속성으로 정의한다.
  - 카테고리로 구분되는 데모페이지는 _demos 폴더에, 각 카테고리명에 해당하는 하위폴더를 생성하고 그 아래에 .md 파일을 만든다.
  - 오른쪽 개발자를 위한 소스코드들어가는 영역을 devbox라 한다.
  - 이곳은 devbox라는 이름의 하위 폴더에 devboxfile 머릿말에 해당하는 파일명으로 .md파일을 만들면 자동으로 페이지에 로드된다.
  - markdown 파일에서 공백이 들어간 카테고리명을 사용하려면 ['카테고리 명'] 또는 행 구분 하여 - 카테고리 명 으로 넣어 주어야 한다.
- Release 카테고리
  - release 카테고리는 고정된 이름의 카테고리이다.
  - _release 폴더에 들어 있는 .md파일은 release로 구분 된다.

### demo 페이지에서 RealGrid 사용하기

- RealGrid는 lib/realgrid/realgridjs_{eval}.{version} 폴더 밑에 버전별 폴더를 만들어 넣어준다.
- 데모페이지에 로드되는 RealGrid의 버전은 _config.yml파일에 realgrid_version 속성에 지정한다.
- include 코드는 /_include/footer.html 파일에 있다.

### URL 링크

- 사용자가 접근 하는 root URL은 www.realgrid.com/demo
- 개발은 /demo 부분만 따로 관리하게 되므로 항상 앞쪽에 /demo가 붙어야 한다.
- 이러한 처리를 위해 지킬에서는 prepend 필터를 써서 아래와 같이 코딩 한다.
- markdown 파일 내에서도 사용가능.

```
$(document).ready( function(){
    RealGridJS.setRootContext("{{ "/lib/realgrid/realgridjs_eval.1.1.19" | prepend: site.baseurl }}");
    ...
Provider);    
});   
```

### 페이지 머릿말(frontmatter)

- 일반 page
  - layout: page
  - title: {타이틀} 상단 제목
  - description: {설명} 제목 아래 부제목 또는 페이지 설명

- demo page
  - layout: page
  - title: {타이틀} 상단 제목
  - devbox: {true|false} devbox표시여부
  - devboxfile: {filename.md} devbox에 표시될 markdown filename
  - version: 해당 페이지의 기능을 사용할 수 있는 최소 버전을 명식한다. 잘 모르면 1.0.11로 한다.
  - tags: 페이지검색용 태그
  - description: {설명} 제목 아래 부제목 또는 페이지 설명
  - categories: 데모 페이지 카테고리명

- release page
  - layout: page
  - title: {타이틀} 상단 제목
  - releaseDate: {배포일자} 정렬 순서를 결정한다.
  - sidebar: {true|false} 왼쪽 메뉴에 보일지 말지 결정한다.
  - releaseVersion: {배포버전}

## Deployment

### 배포소스

- 배포는 _site폴더의 내용을 github-pages 서비스를 위한 배포 저장소에 올린다.

### 저장소

- 배포 저장소(Public): https://github.com/RealGridSites/demo.git
- branch: 배포 브랜치는 gh-pages 이며 기본 도메인은 www.realgrid.com/demo 가 된다.

### 배포방법

- ./branch 스크립트를 실행
- 스크립트 내부에는
  - `JEKYLL_ENV=production jekyll build` 로 환경값을 production으로 해서 _posts폴더의 내용을 메뉴에서 감춘다.
  - _site 폴더의 내용을 모두 commit 하고 push한다.
