---
layout: page
title: "[Programmers] SQL 고득점 Kit - 293258번"
author: "FulOfWrk"
date: "2025년 07월 22일"
---

# [Programmers] SQL 고득점 Kit, 293258번

Last edited: 2025년 07월 22일, Created: 2025년 07월 22일

[Link : 293258번 문제](https://school.programmers.co.kr/learn/courses/30/lessons/293258)

---

<br>

# 문제 설명

낚시앱에서 사용하는 `FISH_INFO` 테이블은 잡은 물고기들의 정보를 담고 있습니다. `FISH_INFO` 테이블의 구조는 다음과 같으며 `ID`, `FISH_TYPE`, `LENGTH`, `TIME`은 각각 잡은 물고기의 ID, 물고기의 종류(숫자), 잡은 물고기의 길이(cm), 물고기를 잡은 날짜를 나타냅니다. 

<table>
  <tr>
    <td><b>Column name</b></td>
    <td><b>Type</b></td>
    <td><b>Nullable</b></td>
  </tr>
  <tr>
    <td>ID</td>
    <td>INTEGER</td>
    <td>FALSE</td>
  </tr>
  <tr>
    <td>FISH_TYPE</td>
    <td>INTEGER</td>
    <td>FALSE</td>
  </tr>
  <tr>
    <td>LENGTH</td>
    <td>FLOAT</td>
    <td>TRUE</td>
  </tr>
  <tr>
    <td>TIME</td>
    <td>DATE</td>
    <td>FALSE</td>
  </tr>
</table>


단, 잡은 물고기의 길이가 10cm 이하일 경우에는 `LENGTH` 가 NULL 이며, `LENGTH` 에 NULL 만 있는 경우는 없습니다. 

<br>

# 문제

잡은 물고기 중 길이가 10cm 이하인 물고기의 수를 출력하는 SQL 문을 작성해주세요.

물고기의 수를 나타내는 컬럼 명은 FISH_COUNT로 해주세요. 

<br>

# 풀이

```sql
SELECT COUNT(ID) AS FISH_COUNT
FROM FISH_INFO
WHERE LENGTH IS NULL;
```

<br>