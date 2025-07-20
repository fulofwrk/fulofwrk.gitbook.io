---
layout: page
title: "[Programmers] SQL 고득점 Kit - 144853번"
author: "FulOfWrk"
date: "2025년 07월 20일"
---

# [Programmers] SQL 고득점 Kit, 144853번

Last edited: 2025년 07월 20일, Created: 2025년 07월 20일

[Link :144853번 문제](https://school.programmers.co.kr/learn/courses/30/lessons/144853)

---

<br>

# 문제 설명

다음은 어느 한 서점에서 판매중인 도서들의 도서 정보(`BOOK`) 테이블입니다. `BOOK` 테이블은 각 도서의 정보를 담은 테이블로 아래와 같은 구조로 되어있습니다.

<table>
  <tr>
    <td><b>Column name</b></td>
    <td><b>Type</b></td>
    <td><b>Nullable</b></td>
    <td><b>Description</b></td>
  </tr>
  <tr>
    <td>BOOK_ID</td>
    <td>INTEGER</td>
    <td>FALSE</td>
    <td>도서 ID</td>
  </tr>
  <tr>
    <td>CATEGORY</td>
    <td>VARCHAR(N)</td>
    <td>FALSE</td>
    <td>카테고리 (경제, 인문, 소설, 생활, 기술)</td>
  </tr>
  <tr>
    <td>AUTHOR_ID</td>
    <td>INTEGER</td>
    <td>FALSE</td>
    <td>저자 ID</td>
  </tr>
  <tr>
    <td>PRICE</td>
    <td>INTEGER</td>
    <td>FALSE</td>
    <td>판매가 (원)</td>
  </tr>
  <tr>
    <td>PUBLISHED_DATE</td>
    <td>DATE</td>
    <td>FALSE</td>
    <td>출판일</td>
  </tr>
</table>


<br>

# 문제

`BOOK` 테이블에서 `2021년`에 출판된 `'인문'` 카테고리에 속하는 도서 리스트를 찾아서 도서 ID(`BOOK_ID`), 출판일 (`PUBLISHED_DATE`)을 출력하는 SQL문을 작성해주세요.
결과는 출판일을 기준으로 오름차순 정렬해주세요. `PUBLISHED_DATE`의 데이트 포맷이 예시와 동일해야 정답처리 됩니다. 

<br>

# 풀이

```sql
SELECT BOOK_ID, 
	DATE_FORMAT(PUBLISHED_DATE, "%Y-%m-%d") AS PUBLISHED_DATE
FROM BOOK
WHERE 1=1
	AND YEAR(PUBLISHED_DATE) = 2021
	AND CATEGORY = "인문"
ORDER BY PUBLISHED_DATE;
```

<br>