---
title: SPA 웹앱 개발 시 고려해야할 사항은?
date: 2019-02-02 20:00:00
categories:
- qna
tags:
- spa
- web
---

> 원본 문서
> *[Heehong Moon - SPA 개발에서 고려할 사항](https://medium.com/@bbirec/spa-single-page-application-%EA%B0%9C%EB%B0%9C%EC%97%90%EC%84%9C-%EA%B3%A0%EB%A0%A4%ED%95%A0-%EC%82%AC%ED%95%AD-eedcb7cb618f)*
> *[로드스타 - SPA 도입 시 필수 고려 사항](https://eapp.tistory.com/entry/SPA-%EB%8F%84%EC%9E%85%EC%8B%9C-%ED%95%84%EC%88%98-%EA%B3%A0%EB%A0%A4%EC%82%AC%ED%95%AD)*


### 데이터(state) 관리는 어떻게 할 것인가?
- SPA에서는 페이지 당 State가 아닌, Application 전체의 State를 관리해야함
- ex) Redux in React, VueX in Vue...

### 언제 새로운 데이터를 가져올 것인가?
- 기존에는 사용자가 새로고침을 누르거나 링크를 클릭하는 시점이 새로운 데이터를 가져오는 시점
- 하지만, SPA에서는 페이지 새로고침이 기본적으로 없음

### 새로운 코드가 Deploy되었을 때 처리
- SPA 웹앱은 특성상 유저가 오랜기간 새로고침 없이 사용할 가능성이 높다
- 이에, 새로운 버전 배포 시 반영이 안되거나 일부만 반영되는 현상이 발생할 수 있음
- ex) API 호출 시 마다 버전 체크...

### 페이지 에러 핸들링
- SPA는 javascript로 하나의 앱이 개발되었다고 볼 수 있고 기존 처럼 간단한 오류를 내서는 안됨
- ex) `try...catch`, Sentry...

### SEO (검색 엔진 최적화)
- 검색 엔진의 Crawling Bot은 웹앱이 언제 DOM의 렌더링을 마칠지 가늠하기 힘듬
- Link Preview 문제

### 로딩 지연 문제
- 첫 호출 시에 과도하게 집중된 로딩 지연 문제
- 모바일 환경에서는 더욱 치명적임
