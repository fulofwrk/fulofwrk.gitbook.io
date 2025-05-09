---
layout: page
title: "[Programmers] SQL 고득점 Kit - 133025번"
author: "FulOfWrk"
date: "2025년 05월 09일"
---

# [Programmers] SQL 고득점 Kit, 133025번 문제

Last edited : 2025년 05월 09일, Created : 2025년 05월 09일

[Link : 133025번 문제](https://school.programmers.co.kr/learn/courses/30/lessons/133025)

---

<br>

# 문제 설명

다음은 아이스크림 가게의 상반기 주문 정보를 담은 `FIRST_HALF` 테이블과 아이스크림 성분에 대한 정보를 담은 `ICECREAM_INFO` 테이블입니다. `FIRST_HALF` 테이블 구조는 다음과 같으며, `SHIPMENT_ID`, `FLAVOR`, `TOTAL_ORDER` 는 각각 아이스크림 공장에서 아이스크림 가게까지의 출하 번호, 아이스크림 맛, 상반기 아이스크림 총주문량을 나타냅니다. `FIRST_HALF` 테이블의 기본 키는 `FLAVOR`입니다. 

<table>
  <tr>
    <td><b>NAME</b></td>
    <td><b>TYPE</b></td>
    <td><b>NULLABLE</b></td>
  </tr>
  <tr>
    <td>SHIPMENT_ID</td>
    <td>INT(N)</td>
    <td>FALSE</td>
  </tr>
  <tr>
    <td>FLAVOR</td>
    <td>VARCHAR(N)</td>
    <td>FALSE</td>
  </tr>
  <tr>
    <td>TOTAL_ORDER</td>
    <td>INT(N)</td>
    <td>FALSE</td>
  </tr>
</table>

`ICECREAM_INFO` 테이블 구조는 다음과 같으며, `FLAVOR`, `INGREDITENT_TYPE` 은 각각 아이스크림 맛, 아이스크림의 성분 타입을 나타냅니다. `INGREDIENT_TYPE`에는 아이스크림의 주 성분이 설탕이면 `sugar_based`라고 입력되고, 아이스크림의 주 성분이 과일이면 `fruit_based`라고 입력됩니다. `ICECREAM_INFO`의 기본 키는 `FLAVOR`입니다. `ICECREAM_INFO`테이블의 `FLAVOR`는 `FIRST_HALF` 테이블의 `FLAVOR`의 외래 키입니다. 

<table>
  <tr>
    <td><b>NAME</b></td>
    <td><b>TYPE</b></td>
    <td><b>NULLABLE</b></td>
  </tr>
  <tr>
    <td>FLAVOR</td>
    <td>VARCHAR(N)</td>
    <td>FALSE</td>
  </tr>
  <tr>
    <td>INGREDIENT_TYPE</td>
    <td>VARCHAR(N)</td>
    <td>FALSE</td>
  </tr>
</table>

<br>

# 문제

상반기 아이스크림 총주문량이 3,000보다 높으면서 아이스크림의 주 성분이 과일인 아이스크림의 맛을 총주문량이 큰 순서대로 조회하는 SQL 문을 작성해주세요. 

<br>

# 풀이

```sql
SELECT FLAVOR
FROM (
    SELECT FH.*, II.INGREDIENT_TYPE
    FROM FIRST_HALF AS FH
    JOIN ICECREAM_INFO AS II ON II.FLAVOR=FH.FLAVOR
    WHERE FH.TOTAL_ORDER > 3000
        AND II.INGREDIENT_TYPE = "fruit_based"
    ORDER BY FH.TOTAL_ORDER DESC
) AS T;
```

Ordering이 해당 컬럼이 `SELECT`절에 명시가 되어야 되는 줄 알아서 한번 더 감싸줬는데, 그럴 필요가 없다. 

```sql
# 다른 풀이 참고 - 1
SELECT FIRST_HALF.FLAVOR
FROM FIRST_HALF, ICECREAM_INFO
WHERE FIRST_HALF.FLAVOR = ICECREAM_INFO.FLAVOR 
	AND FIRST_HALF.TOTAL_ORDER > 3000 
	AND ICECREAM_INFO.INGREDIENT_TYPE = 'fruit_based'
ORDER BY TOTAL_ORDER DESC;
```

<br>

