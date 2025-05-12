---
layout: page
title: "[Programmers] SQL 고득점 Kit - 132203번"
author: "FulOfWrk"
date: "2025년 05월 12일"
---

# [Programmers] SQL 고득점 Kit, 132203번 문제

Last edited : 2025년 05월 12일, Created : 2025년 05월 12일

[Link : 132203번 문제](https://school.programmers.co.kr/learn/courses/30/lessons/132203)

---

<br>

# 문제 설명

다음은 종합병원에 속한 의사 정보를 담은`DOCTOR` 테이블입니다. `DOCTOR` 테이블은 다음과 같으며 `DR_NAME`, `DR_ID`, `LCNS_NO`, `HIRE_YMD`, `MCDP_CD`, `TLNO`는 각각 의사이름, 의사ID, 면허번호, 고용일자, 진료과코드, 전화번호를 나타냅니다. 

<table>
  <tr>
    <td><b>Column name</b></td>
    <td><b>Type</b></td>
    <td><b>Nullable</b></td>
  </tr>
  <tr>
    <td>DR_NAME</td>
    <td>VARCHAR(20)</td>
    <td>FALSE</td>
  </tr>
  <tr>
    <td>DR_ID</td>
    <td>VARCHAR(10)</td>
    <td>FALSE</td>
  </tr>
  <tr>
    <td>LCNS_NO</td>
    <td>VARCHAR(30)</td>
    <td>FALSE</td>
  </tr>
  <tr>
    <td>HIRE_YMD</td>
    <td>DATE</td>
    <td>FALSE</td>
  </tr>
  <tr>
    <td>MCDP_CD</td>
    <td>VARCHAR(6)</td>
    <td>TRUE</td>
  </tr>
  <tr>
    <td>TLNO</td>
    <td>VARCHAR(50)</td>
    <td>TRUE</td>
  </tr>
</table>


<br>

# 문제

`DOCTOR` 테이블에서 진료과가 흉부외과(CS)이거나 일반외과(GS)인 의사의 이름, 의사ID, 진료과, 고용일자를 조회하는 SQL문을 작성해주세요. 이때 결과는 고용일자를 기준으로 내림차순 정렬하고, 고용일자가 같다면 이름을 기준으로 오름차순 정렬해주세요(주의사항: 날짜 포맷은 예시와 동일하게 나와야합니다). 

<br>

# 풀이

```sql
SELECT DR_NAME, DR_ID, MCDP_CD, 
    DATE_FORMAT(HIRE_YMD, "%Y-%m-%d") AS HIRE_YMD
FROM DOCTOR
WHERE MCDP_CD IN ("CS", "GS")
ORDER BY HIRE_YMD DESC, DR_NAME;
```

<br>

