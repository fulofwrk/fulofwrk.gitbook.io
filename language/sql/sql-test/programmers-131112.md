---
layout: page
title: "[Programmers] SQL 고득점 Kit - 131112번"
author: "FulOfWrk"
date: "2025년 05월 14일"
---

# [Programmers] SQL 고득점 Kit, 131112번

Last edited: 2025년 05월 14일, Created: 2025년 05월 14일

[Link :131112번 문제](https://school.programmers.co.kr/learn/courses/30/lessons/131112)

---

<br>

# 문제 설명

다음은 식품공장의 정보를 담은 `FOOD_FACTORY` 테이블입니다. `FOOD_FACTORY` 테이블은 다음과 같으며 `FACTORY_ID`, `FACTORY_NAME`, `ADDRESS`, `TLNO`는 각각 공장 ID, 공장 이름, 주소, 전화번호를 의미합니다. 

<table>
  <tr>
    <td><b>Column name</b></td>
    <td><b>Type</b></td>
    <td><b>Nullable</b></td>
  </tr>
  <tr>
    <td>FACTORY_ID</td>
    <td>VARCHAR(10)</td>
    <td>FALSE</td>
  </tr>
  <tr>
    <td>FACTORY_NAME</td>
    <td>VARCHAR(50)</td>
    <td>FALSE</td>
  </tr>
  <tr>
    <td>ADDRESS</td>
    <td>VARCHAR(100)</td>
    <td>FALSE</td>
  </tr>
  <tr>
    <td>TLNO</td>
    <td>VARCHAR(20)</td>
    <td>TURE</td>
  </tr>
</table>

<br>

# 문제

`FOOD_FACTORY` 테이블에서 강원도에 위치한 식품공장의 공장 ID, 공장 이름, 주소를 조회하는 SQL문을 작성해주세요. 이때 결과는 공장 ID를 기준으로 오름차순 정렬해주세요. 

<br>

# 풀이

```sql
SELECT FACTORY_ID, FACTORY_NAME, ADDRESS
FROM FOOD_FACTORY
WHERE ADDRESS LIKE "강원%"
ORDER BY FACTORY_ID;
```

<br>