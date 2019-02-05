---
title: RDBMS에서 PK와 Index는 무엇인가?
date: 2019-02-05 13:30:00
categories:
- qna
tags:
- db
- rdbms
---

### PK (기본키, Primary Key)
- 관계형 데이터베이스에서 Record를 고유하게 구분해주는 식별자 (최소한의 정보)
- PK는 `NULL` 값을 가질 수 없고, 다른 값과 중복되지 않는 유일한 값 (`UNIQUE`)을 가진다.
- 이런 PK가 될 수 있는 column들의 집합을 후보키 (Candidate Key)라고 한다.
- PK를 생성하면, 물리적으로 uniqueness를 보장하기 위해 unique index가 만들어지고, PK를 SARGs(Search Arguments)로 사용한 쿼리들의 성능은 현저하게 향상된다.

### Index
- RDBMS에서 검색 속도를 높이기 위해 사용하는 하나의 기술로, 특정 table의 column을 색인화(따로 저장)하여 검색 시 해당 table을 full scan 하는 것이 아닌, 색인화된 index를 검색하여 검색 속도를 빠르게 한다.
- 보통 index를 저장하는데는 [B+ Tree](https://ko.wikipedia.org/wiki/B%2B_%ED%8A%B8%EB%A6%AC) 자료구조를 사용한다.
- `WHERE` 절에 참조되는 column, 참조키(FK)가 설정된 column, JOIN에 사용되는 column, `ORDER BY`로 정렬되거나 `GROUP BY`로 그룹핑되는 column 등에 사용하면 데이터 조회 속도를 높일 수 있다.
- Index를 생성하는데 공간 비용이 필요하며, 데이터 조회 속도가 빨라지는 대신 데이터 삽입/수정/삭제 속도가 감소한다. 또한, 선택도(`찾을 데이터 / 전체 데이터`)가 큰 경우 굉장히 비효율적이다.
