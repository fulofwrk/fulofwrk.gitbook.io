---
layout: page
title: "[Programmers] SQL 고득점 Kit - 132201번"
author: "FulOfWrk"
date: "2025년 07월 08일"
---

# [Programmers] SQL 고득점 Kit, 132201번

Last edited: 2025년 07월 07일, Created: 2025년 07월 07일

[Link :132201번 문제](https://school.programmers.co.kr/learn/courses/30/lessons/132201)

---

<br>

# 문제 설명

다음은 종합병원에 등록된 환자정보를 담은 `PATIENT` 테이블입니다. `PATIENT` 테이블은 다음과 같으며 `PT_NO`, `PT_NAME`, `GEND_CD`, `AGE`, `TLNO`는 각각 환자번호, 환자이름, 성별코드, 나이, 전화번호를 의미합니다. 

<table>
  <tr>
    <td><b>Column name</b></td>
    <td><b>Type</b></td>
    <td><b>Nullable</b></td>
  </tr>
  <tr>
    <td>PT_NO</td>
    <td>VARCHAR(10)</td>
    <td>FALSE</td>
  </tr>
  <tr>
    <td>PT_NAME</td>
    <td>VARCHAR(20)</td>
    <td>FALSE</td>
  </tr>
  <tr>
    <td>GEND_CD</td>
    <td>VARCHAR(1)</td>
    <td>FALSE</td>
  </tr>
  <tr>
    <td>AGE</td>
    <td>INTEGER</td>
    <td>FALSE</td>
  </tr>
  <tr>
    <td>TLNO</td>
    <td>VARCHAR(50)</td>
    <td>TRUE</td>
  </tr>
</table>


<br>

# 문제

`PATIENT` 테이블에서 12세 이하인 여자환자의 환자이름, 환자번호, 성별코드, 나이, 전화번호를 조회하는 SQL문을 작성해주세요. 이때 전화번호가 없는 경우, 'NONE'으로 출력시켜 주시고 결과는 나이를 기준으로 내림차순 정렬하고, 나이 같다면 환자이름을 기준으로 오름차순 정렬해주세요. 

<br>

# 풀이

```sql
-- 코드를 입력하세요
SELECT PT_NAME, PT_NO, GEND_CD, AGE, 
    CASE WHEN TLNO IS NULL OR TLNO = "" THEN "NONE" 
        ELSE TLNO
    END AS TLNO
FROM PATIENT
WHERE 1=1 
	AND AGE <= 12 
	AND GEND_CD = "W"
ORDER BY AGE DESC, PT_NAME;
```

<br>