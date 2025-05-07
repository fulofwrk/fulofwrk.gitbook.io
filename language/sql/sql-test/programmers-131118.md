---
layout: page
title: "[Programmers] SQL 고득점 Kit"
author: "FulOfWrk"
date: "2025년 05월 07일"

---

# [Programmers] SQL 고득점 Kit, 13118번 문제

Last edited : 2025년 05월 07일, Created : 2025년 05월 07일

[Link : 131118번 문제](https://school.programmers.co.kr/learn/courses/30/lessons/131118)

---

<br>

## 문제 설명

다음은 식당의 정보를 담은 `REST_INFO` 테이블과 식당의 리뷰 정보를 담은 `REST_REVIEW` 테이블입니다. `REST_INFO` 테이블은 다음과 같으며 `REST_ID`, `REST_NAME`, `FOOD_TYPE`, `VIEWS`, `FAVORITES`, `PARKING_LOT`, `ADDRESS`, `TEL`은 식당 ID, 식당 이름, 음식 종류, 조회수, 즐겨찾기수, 주차장 유무, 주소, 전화번호를 의미합니다. 

<table>
  <tr>
    <td><b>Column name</b></td>
    <td><b>Type</b></td>
    <td><b>Nullable</b></td>
  </tr>
  <tr>
    	<td>REST_ID</td>
	    <td>VARCHAR(5)</td>
  	  <td>FALSE</td>
  </tr>
  <tr>
    	<td>REST_NAME</td>
	    <td>VARCHAR(50)</td>
  	  <td>FALSE</td>
  </tr>
  <tr>
    	<td>FOOD_TYPE</td>
	    <td>VARCHAR(20)</td>
  	  <td>TRUE</td>
  </tr>
  <tr>
    	<td>VIEWS</td>
	    <td>NUMBER</td>
  	  <td>TRUE</td>
  </tr>
  <tr>
    	<td>FAVORITES</td>
	    <td>NUMBER</td>
  	  <td>TRUE</td>
  </tr>
  <tr>
    	<td>PARKING_LOT</td>
	    <td>VARCHAR(1)</td>
  	  <td>TRUE</td>
  </tr>
  <tr>
    	<td>ADDRESS</td>
	    <td>VARCHAR(100)</td>
  	  <td>TRUE</td>
  </tr>
  <tr>
    	<td>TEL</td>
	    <td>VARCHAR(100)</td>
  	  <td>TRUE/td>
  </tr>
</table>


`REST_REVIEW` 테이블은 다음과 같으며 `REVIEW_ID`, `REST_ID`, `MEMBER_ID`, `REVIEW_SCORE`, `REVIEW_TEXT`,`REVIEW_DATE`는 각각 리뷰 ID, 식당 ID, 회원 ID, 점수, 리뷰 텍스트, 리뷰 작성일을 의미합니다. 

<table>
  <tr>
    <td><b>Column name</b></td>
    <td><b>Type</b></td>
    <td><b>Nullable</b></td>
  </tr>
  <tr>
  	<td>REVIEW_ID</td>
    <td>VARCHAR(10)</td>
    <td>FALSE</td>
  </tr>
  <tr>
  	<td>REST_ID</td>
    <td>VARCHAR(10)</td>
    <td>TRUE</td>
  </tr>
  <tr>
  	<td>MEMBER_ID</td>
    <td>VARCHAR(100)</td>
    <td>TRUE</td>
  </tr>
  <tr>
  	<td>REVIEW_SCORE</td>
    <td>NUMBER</td>
    <td>TRUE</td>
  </tr>
  <tr>
  	<td>REVIEW_TEXT</td>
    <td>VARCHAR(1000)</td>
    <td>TRUE</td>
  </tr>
  <tr>
  	<td>REVIEW_DATE</td>
    <td>DATE</td>
    <td>TRUE</td>
  </tr>
</table>


<br>

## 문제

`REST_INFO`와 `REST_REVIEW` 테이블에서 서울에 위치한 식당들의 식당 ID, 식당 이름, 음식 종류, 즐겨찾기수, 주소, 리뷰 평균 점수를 조회하는 SQL문을 작성해주세요. 이때 리뷰 평균점수는 소수점 세 번째 자리에서 반올림 해주시고 결과는 평균점수를 기준으로 내림차순 정렬해주시고, 평균점수가 같다면 즐겨찾기수를 기준으로 내림차순 정렬해주세요. 

<br>

## 풀이

```sql
SELECT RI.REST_ID, RI.REST_NAME, RI.FOOD_TYPE, RI.FAVORITES, RI.ADDRESS, RR.SCORE
FROM REST_INFO AS RI
LEFT JOIN (
    SELECT REST_ID, ROUND(AVG(REVIEW_SCORE), 2) AS SCORE
    FROM REST_REVIEW
    GROUP BY REST_ID
) AS RR ON RR.REST_ID=RI.REST_ID
WHERE RI.ADDRESS LIKE "서울%" AND RR.SCORE > 0
ORDER BY SCORE DESC, RI.FAVORITES DESC
;

```

평소에 `JOIN`을 할 때, `LEFT JOIN`을 자주 사용해서 해당 문제도 기본 식당 정보에 식당 별로  `REVIEW_SCORE`을 평균 낸 테이블을 `JOIN` 했다. 그렇게 시도 했을 때, 리뷰가 없는 식당의 경우도 있어 리뷰가 없는 식당도 같이 출력이 되어서 조건절에 `RR.SCORE > 0` 조건을 별도로 넣어줬다. 

```sql
# 다른 풀이 참고
SELECT RI.REST_ID, RI.REST_NAME, RI.FOOD_TYPE, RI.FAVORITES, RI.ADDRESS, ROUND(AVG(RR.REVIEW_SCORE), 2) AS SCORE
FROM REST_INFO AS RI
JOIN REST_REVIEW AS RR ON RR.REST_ID=RI.REST_ID
WHERE RI.ADDRESS LIKE "서울%"
GROUP BY RI.REST_ID, RI.REST_NAME, RI.FOOD_TYPE, RI.FAVORITES, RI.ADDRESS
ORDER BY SCORE DESC, RI.FAVORITES DESC;
```

다른 풀이를 참고했을 때, 더 간결하고 추가된 조건을 주지 않아도 문제가 해결될 수 있다는 것을 깨달았다. 애초에 `INNER JOIN`을 활용하면, 두 테이블에서 공통된 부분만 추출 가능하기 떄문이다. 

