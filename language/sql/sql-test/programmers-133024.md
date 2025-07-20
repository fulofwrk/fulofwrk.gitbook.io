---
layout: page
title: "[Programmers] SQL 고득점 Kit - 133024번"
author: "FulOfWrk"
date: "2025년 07월 20일"
---

# [Programmers] SQL 고득점 Kit, 133024번

Last edited: 2025년 07월 20일, Created: 2025년 07월 20일

[Link :133024번 문제](https://school.programmers.co.kr/learn/courses/30/lessons/133024)

---

<br>

# 문제 설명

`FIRST_HALF` 테이블은 아이스크림 가게의 상반기 주문 정보를 담은 테이블입니다.`FIRST_HALF` 테이블 구조는 다음과 같으며, `SHIPMENT_ID`, `FLAVOR`, `TOTAL_ORDER`는 각각 아이스크림 공장에서 아이스크림 가게까지의 출하 번호, 아이스크림 맛, 상반기 아이스크림 총주문량을 나타냅니다. 

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

<br>

# 문제

상반기에 판매된 아이스크림의 맛을 총주문량을 기준으로 내림차순 정렬하고 총주문량이 같다면 출하 번호를 기준으로 오름차순 정렬하여 조회하는 SQL 문을 작성해주세요. 

<br>

# 풀이

```sql
SELECT FLAVOR
FROM FIRST_HALF
ORDER BY TOTAL_ORDER DESC, SHIPMENT_ID;
```

<br>