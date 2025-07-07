---
layout: page
title: "[Programmers] SQL 고득점 Kit - 164673번"
author: "FulOfWrk"
date: "2025년 07월 07일"
---

# [Programmers] SQL 고득점 Kit, 164673번

Last edited: 2025년 07월 07일, Created: 2025년 07월 07일

[Link :131112번 문제](https://school.programmers.co.kr/learn/courses/30/lessons/164673)

---

<br>

# 문제 설명

다음은 중고거래 게시판 정보를 담은 `USED_GOODS_BOARD` 테이블과 중고거래 게시판 첨부파일 정보를 담은 `USED_GOODS_REPLY` 테이블입니다. `USED_GOODS_BOARD` 테이블은 다음과 같으며 `BOARD_ID`, `WRITER_ID`, `TITLE`, `CONTENTS`, `PRICE`, `CREATED_DATE`, `STATUS`, `VIEWS`은 게시글 ID, 작성자 ID, 게시글 제목, 게시글 내용, 가격, 작성일, 거래상태, 조회수를 의미합니다.  

<table>
  <tr>
    <td><b>Column name</b></td>
    <td><b>Type</b></td>
    <td><b>Nullable</b></td>
  </tr>
  <tr>
    <td>BOARD_ID</td>
    <td>VARCHAR(5)</td>
    <td>FALSE</td>
  </tr>
  <tr>
    <td>WRITER_ID</td>
    <td>VARCHAR(50)</td>
    <td>FALSE</td>
  </tr>
  <tr>
    <td>TITLE</td>
    <td>VARCHAR(100)</td>
    <td>FALSE</td>
  </tr>
  <tr>
    <td>CONTENTS</td>
    <td>VARCHAR(1000)</td>
    <td>FALSE</td>
  </tr>
  <tr>
    <td>PRICE</td>
    <td>NUMBER</td>
    <td>FALSE</td>
  </tr>
  <tr>
    <td>CREATED_DATE</td>
    <td>DATE</td>
    <td>FALSE</td>
  </tr>
  <tr>
    <td>STATUS</td>
    <td>VARCHAR(10)</td>
    <td>FALSE</td>
  </tr>
  <tr>
    <td>VIEWS</td>
    <td>NUMBER</td>
    <td>FALSE</td>
  </tr>
</table>

`USED_GOODS_REPLY` 테이블은 다음과 같으며 `REPLY_ID`, `BOARD_ID`, `WRITER_ID`, `CONTENTS`, `CREATED_DATE`는 각각 댓글 ID, 게시글 ID, 작성자 ID, 댓글 내용, 작성일을 의미합니다. 

<table>
  <tr>
    <td><b>Column name</b></td>
    <td><b>Type</b></td>
    <td><b>Nullable</b></td>
  </tr>
  <tr>
    <td>REPLY_ID</td>
    <td>VARCHAR(10)</td>
    <td>FALSE</td>
  </tr>
  <tr>
    <td>BOARD_ID</td>
    <td>VARCHAR(5)</td>
    <td>FALSE</td>
  </tr>
  <tr>
    <td>WRITER_ID</td>
    <td>VARCHAR(50)</td>
    <td>FALSE</td>
  </tr>
  <tr>
    <td>CONTENTS</td>
    <td>VARCHAR(1000)</td>
    <td>TRUE</td>
  </tr>
  <tr>
    <td>CREATED_DATE</td>
    <td>DATE</td>
    <td>FALSE</td>
  </tr>
</table>

<br>

# 문제

`USED_GOODS_BOARD`와 `USED_GOODS_REPLY` 테이블에서 2022년 10월에 작성된 게시글 제목, 게시글 ID, 댓글 ID, 댓글 작성자 ID, 댓글 내용, 댓글 작성일을 조회하는 SQL문을 작성해주세요. 결과는 댓글 작성일을 기준으로 오름차순 정렬해주시고, 댓글 작성일이 같다면 게시글 제목을 기준으로 오름차순 정렬해주세요. 

<br>

# 풀이

```sql
SELECT UGB.TITLE, UGB.BOARD_ID, UGR.REPLY_ID, UGR.WRITER_ID, UGR.CONTENTS, 
    DATE_FORMAT(UGR.CREATED_DATE, "%Y-%m-%d") AS CREATED_DATE

FROM USED_GOODS_REPLY AS UGR
JOIN USED_GOODS_BOARD AS UGB ON UGB.BOARD_ID=UGR.BOARD_ID

WHERE 1=1 
		AND YEAR(UGB.CREATED_DATE) = 2022
    AND MONTH(UGB.CREATED_DATE) = 10
ORDER BY UGR.CREATED_DATE, UGB.TITLE;
```

<br>