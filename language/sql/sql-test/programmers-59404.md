---
layout: page
title: "[Programmers] SQL 고득점 Kit - 59404번"
author: "FulOfWrk"
date: "2025년 07월 21일"
---

# [Programmers] SQL 고득점 Kit, 59404번

Last edited: 2025년 07월 21일, Created: 2025년 07월 21일

[Link : 59404번 문제](https://school.programmers.co.kr/learn/courses/30/lessons/59404)

---

<br>

# 문제 설명

`ANIMAL_INS` 테이블은 동물 보호소에 들어온 동물의 정보를 담은 테이블입니다. `ANIMAL_INS` 테이블 구조는 다음과 같으며, `ANIMAL_ID`, `ANIMAL_TYPE`, `DATETIME`, `INTAKE_CONDITION`, `NAME`, `SEX_UPON_INTAKE`는 각각 동물의 아이디, 생물 종, 보호 시작일, 보호 시작 시 상태, 이름, 성별 및 중성화 여부를 나타냅니다. 

<table>
  <tr>
    <td><b>NAME</b></td>
    <td><b>TYPE</b></td>
    <td><b>NULLABLE</b></td>
  </tr>
  <tr>
    <td>ANIMAL_ID</td>
    <td>VARCHAR(N)</td>
    <td>FALSE</td>
  </tr>
  <tr>
    <td>ANIMAL_TYPE</td>
    <td>VARCHAR(N)</td>
    <td>FALSE</td>
  </tr>
  <tr>
    <td>DATETIME</td>
    <td>DATETIME</td>
    <td>FALSE</td>
  </tr>
  <tr>
    <td>INTAKE_CONDITION</td>
    <td>VARCHAR(N)</td>
    <td>FALSE</td>
  </tr>
  <tr>
    <td>NAME</td>
    <td>VARCHAR(N)</td>
    <td>TRUE</td>
  </tr>
  <tr>
    <td>SEX_UPON_INTAKE</td>
    <td>VARCHAR(N)</td>
    <td>FALSE</td>
  </tr>
</table>

<br>

# 문제

동물 보호소에 들어온 모든 동물의 아이디와 이름, 보호 시작일을 이름 순으로 조회하는 SQL문을 작성해주세요. 단, 이름이 같은 동물 중에서는 보호를 나중에 시작한 동물을 먼저 보여줘야 합니다. 

<br>

# 풀이

```sql
SELECT ANIMAL_ID, NAME, DATETIME
FROM ANIMAL_INS
ORDER BY NAME, DATETIME DESC;
```

<br>