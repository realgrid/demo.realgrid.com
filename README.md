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

### URL

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
  - description: {설명} 제목 아래 부제목 또는 페이지 설명

- release page
  - layout: page
  - title: {타이틀} 상단 제목
  - releaseDate: {배포일자} 정렬 순서를 결정한다.
  - version: {배포버전}

## Deployment

- 배포 저장소(Public) : https://github.com/RealGridSites/demo.git
