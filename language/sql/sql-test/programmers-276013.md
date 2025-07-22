---
layout: page
title: "[Programmers] SQL 고득점 Kit - 276013번"
author: "FulOfWrk"
date: "2025년 07월 22일"
---

# [Programmers] SQL 고득점 Kit, 276013번

Last edited: 2025년 07월 22일, Created: 2025년 07월 22일

[Link : 276013번 문제](https://school.programmers.co.kr/learn/courses/30/lessons/276013)

---

<br>

# 문제 설명

`DEVELOPER_INFOS` 테이블은 개발자들의 프로그래밍 스킬 정보를 담은 테이블입니다. `DEVELOPER_INFOS` 테이블 구조는 다음과 같으며, `ID`, `FIRST_NAME`, `LAST_NAME`, `EMAIL`, `SKILL_1`, `SKILL_2`, `SKILL_3`는 각각 ID, 이름, 성, 이메일, 첫 번째 스킬, 두 번째 스킬, 세 번째 스킬을 의미합니다. 

<table>
  <tr>
    <td><b>NAME</b></td>
    <td><b>TYPE</b></td>
    <td><b>UNIQUE</b></td>
    <td><b>NULLABLE</b></td>
  </tr>
  <tr>
    <td>ID</td>
    <td>VARCHAR(N)</td>
    <td>Y</td>
    <td>N</td>
  </tr>
  <tr>
    <td>FIRST_NAME</td>
    <td>VARCHAR(N)</td>
    <td>N</td>
    <td>Y</td>
  </tr>
  <tr>
    <td>LAST_NAME</td>
    <td>VARCHAR(N)</td>
    <td>N</td>
    <td>Y</td>
  </tr>
  <tr>
    <td>EMAIL</td>
    <td>VARCHAR(N)</td>
    <td>Y</td>
    <td>N</td>
  </tr>
  <tr>
    <td>SKILL_1</td>
    <td>VARCHAR(N)</td>
    <td>N</td>
    <td>Y</td>
  </tr>
  <tr>
    <td>SKILL_2</td>
    <td>VARCHAR(N)</td>
    <td>N</td>
    <td>Y</td>
  </tr>
  <tr>
    <td>SKILL_3</td>
    <td>VARCHAR(N)</td>
    <td>N</td>
    <td>Y</td>
  </tr>
</table>


<br>

# 문제

`DEVELOPER_INFOS` 테이블에서 Python 스킬을 가진 개발자의 정보를 조회하려 합니다. Python 스킬을 가진 개발자의 ID, 이메일, 이름, 성을 조회하는 SQL 문을 작성해 주세요. 

결과는 ID를 기준으로 오름차순 정렬해 주세요. 

<br>

# 풀이

```sql
SELECT ID, EMAIL, FIRST_NAME, LAST_NAME
FROM DEVELOPER_INFOS
WHERE 1=1 
	AND SKILL_1 = "Python"
	OR SKILL_2 = "Python"
	OR SKILL_3 = "Python"
ORDER BY ID;
```

<br>