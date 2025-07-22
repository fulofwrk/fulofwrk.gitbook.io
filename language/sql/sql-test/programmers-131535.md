---
layout: page
title: "[Programmers] SQL 고득점 Kit - 131535번"
author: "FulOfWrk"
date: "2025년 07월 22일"
---

# [Programmers] SQL 고득점 Kit, 131535번

Last edited: 2025년 07월 22일, Created: 2025년 07월 22일

[Link : 131535번 문제](https://school.programmers.co.kr/learn/courses/30/lessons/131535)

---

<br>

# 문제 설명

다음은 어느 의류 쇼핑몰에 가입한 회원 정보를 담은 `USER_INFO` 테이블입니다. `USER_INFO` 테이블은 아래와 같은 구조로 되어있으며 `USER_ID`, `GENDER`, `AGE`, `JOINED`는 각각 회원 ID, 성별, 나이, 가입일을 나타냅니다. 

<table>
  <tr>
    <td><b>Column name</b></td>
    <td><b>Type</b></td>
    <td><b>Nullable</b></td>
  </tr>
  <tr>
    <td>USER_ID</td>
    <td>INTEGER</td>
    <td>FALSE</td>
  </tr>
  <tr>
    <td>GENDER</td>
    <td>TINYINT(1)</td>
    <td>TRUE</td>
  </tr>
  <tr>
    <td>AGE</td>
    <td>INTEGER</td>
    <td>TRUE</td>
  </tr>
  <tr>
    <td>JOINED</td>
    <td>DATE</td>
    <td>FALSE</td>
  </tr>
</table>

`GENDER` 컬럼은 비어있거나 0 또는 1의 값을 가지며 0인 경우 남자를, 1인 경우는 여자를 나타냅니다. 

<br>

# 문제

`USER_INFO` 테이블에서 2021년에 가입한 회원 중 나이가 20세 이상 29세 이하인 회원이 몇 명인지 출력하는 SQL문을 작성해주세요. 

<br>

# 풀이

```sql
SELECT COUNT(USER_ID) AS USERS
FROM USER_INFO
WHERE 1=1 
	AND YEAR(JOINED) = 2021
	AND AGE BETWEEN 20 AND 29;
```

<br>