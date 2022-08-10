# RealGrid DEMO 사이트

[![demo.realgrid.com](https://github.com/realgrid/demo.realgrid.com/actions/workflows/pages.yml/badge.svg)](https://github.com/realgrid/demo.realgrid.com/actions/workflows/pages.yml)


## 구조

### Frameworks

- jekyll 4.2.2
- github pages with Actions

### Libraries

- realgrid
- jquery
- bootstrap
- realpivot

## 개발

로컬에서 개발시

```
JEKYLL_ENV=development jekyll serve
```

## 배포

- 그냥 커밋 하면 demo.realgrid.com으로 배포됨.
- 배포정보는 settings 의 pages 를 보면 됨.

## 지킬에서 이상한 오류시 조치

- ruby inatall 필요 (윈도우에서 다를 수 있음)
  - `brew install ruby`
- 지킬 업데이트 필요 (윈도우에서 다를 수 있음)
  - `sudo gem pristine ffi --version 1.12.2`
  - `sudo gem pristine ffi --version 1.11.3`
  - `sudo gem install jekyll bundler`