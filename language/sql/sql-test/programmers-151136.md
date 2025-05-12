---
layout: page
title: "[Programmers] SQL 고득점 Kit - 151136번"
author: "FulOfWrk"
date: "2025년 05월 12일"
---

# [Programmers] SQL 고득점 Kit, 151136번 문제

Last edited : 2025년 05월 12일, Created : 2025년 05월 12일

[Link : 151136번 문제](https://school.programmers.co.kr/learn/courses/30/lessons/151136)

---

<br>

# 문제 설명

다음은 어느 자동차 대여 회사에서 대여중인 자동차들의 정보를 담은 `CAR_RENTAL_COMPANY_CAR` 테이블입니다. `CAR_RENTAL_COMPANY_CAR` 테이블은 아래와 같은 구조로 되어있으며, `CAR_ID`, `CAR_TYPE`, `DAILY_FEE`, `OPTIONS` 는 각각 자동차 ID, 자동차 종류, 일일 대여 요금(원), 자동차 옵션 리스트를 나타냅니다. 

<table>
  <tr>
    <td><b>Column name</b></td>
    <td><b>Type</b></td>
    <td><b>Nullable</b></td>
  </tr>
  <tr>
    <td>CAR_ID</td>
    <td>INTEGER</td>
    <td>FALSE</td>
  </tr>
  <tr>
    <td>CAR_TYPE</td>
    <td>VARCHAR(255)</td>
    <td>FALSE</td>
  </tr>
  <tr>
    <td>DAILY_FEE</td>
    <td>INTEGER</td>
    <td>FALSE</td>
  </tr>
  <tr>
    <td>OPTIONS</td>
    <td>VARCHAR(255)</td>
    <td>FALSE</td>
  </tr>
</table>


자동차 종류는 '세단', 'SUV', '승합차', '트럭', '리무진' 이 있습니다. 자동차 옵션 리스트는 콤마(',')로 구분된 키워드 리스트(예: '열선시트', '스마트키', '주차감지센서')로 되어있으며, 키워드 종류는 '주차감지센서', '스마트키', '네비게이션', '통풍시트', '열선시트', '후방카메라', '가죽시트' 가 있습니다. 


<br>

# 문제

`CAR_RENTAL_COMPANY_CAR` 테이블에서 자동차 종류가 'SUV'인 자동차들의 평균 일일 대여 요금을 출력하는 SQL문을 작성해주세요. 이때 평균 일일 대여 요금은 소수 첫 번째 자리에서 반올림하고, 컬럼명은 `AVERAGE_FEE` 로 지정해주세요. 

<br>

# 풀이

```sql
SELECT ROUND(AVG(DAILY_FEE)) AS AVERAGE_FEE
FROM CAR_RENTAL_COMPANY_CAR
WHERE CAR_TYPE = "SUV";
```

<br>

