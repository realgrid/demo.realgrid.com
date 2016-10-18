# RealGrid DEMO 사이트

## Architectures

### Frameworks

- Jekyll
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

```
$(document).ready( function(){
    RealGridJS.setRootContext("{{ "/lib/realgrid/realgridjs_eval.1.1.19" | prepend: site.baseurl }}");
    ...
Provider);    
});   
```


## Deployment

- 배포 저장소(Public) : https://github.com/RealGridSites/demo.git
