---
layout: page
title: "[Programmers] SQL 고득점 Kit - 301646번"
author: "FulOfWrk"
date: "2025년 07월 23일"
---

# [Programmers] SQL 고득점 Kit, 301646번

Last edited: 2025년 07월 23일, Created: 2025년 07월 23일

[Link : 301646번 문제](https://school.programmers.co.kr/learn/courses/30/lessons/301646)

---

<br>

# 문제 설명

대장균들은 일정 주기로 분화하며, 분화를 시작한 개체를 부모 개체, 분화가 되어 나온 개체를 자식 개체라고 합니다. 
다음은 실험실에서 배양한 대장균들의 정보를 담은 `ECOLI_DATA` 테이블입니다. `ECOLI_DATA` 테이블의 구조는 다음과 같으며, `ID`, `PARENT_ID`, `SIZE_OF_COLONY`, `DIFFERENTIATION_DATE`, `GENOTYPE` 은 각각 대장균 개체의 ID, 부모 개체의 ID, 개체의 크기, 분화되어 나온 날짜, 개체의 형질을 나타냅니다. 

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
    <td>PARENT_ID</td>
    <td>INTEGER</td>
    <td>TRUE</td>
  </tr>
  <tr>
    <td>SIZE_OF_COLONY</td>
    <td>INTEGER</td>
    <td>FALSE</td>
  </tr>
  <tr>
    <td>DIFFENRENTIATION_DATE</td>
    <td>DATE</td>
    <td>FALSE</td>
  </tr>
  <tr>
    <td>GENOTYPE</td>
    <td>INTEGER</td>
    <td>FALSE</td>
  </tr>
</table>


최초의 대장균 개체의 `PARENT_ID` 는 NULL 값입니다. 

<br>

# 문제

2번 형질이 보유하지 않으면서 1번이나 3번 형질을 보유하고 있는 대장균 개체의 수(`COUNT`)를 출력하는 SQL 문을 작성해주세요. 1번과 3번 형질을 모두 보유하고 있는 경우도 1번이나 3번 형질을 보유하고 있는 경우에 포함합니다. 

<br>

# 풀이

```sql
SELECT COUNT(ID) AS COUNT
FROM ECOLI_DATA
WHERE 1=1 
	AND (GENOTYPE & 2) != 2
	AND (
    (GENOTYPE & 1) = 1 
    OR (GENOTYPE & 4) = 4
  );
```

<br>