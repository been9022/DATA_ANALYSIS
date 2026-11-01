# 📘 SQL_BASIC 6주차 정규 과제

SQL_BASIC 정규 과제는 매주 정해진 분량의 `초보자를 위한 BigQuery(SQL) 입문` 강의를 듣고, 핵심 개념을 정리한 뒤 간단한 SQL 문제를 직접 풀어보는 방식으로 진행합니다.

이번 주는 SQL 입문 과정의 핵심 고비인 `JOIN`을 학습합니다.

JOIN은 여러 테이블을 연결해서 분석 질문에 답하기 위해 반드시 필요한 개념입니다. 이번 주 과제에서는 정답 코드뿐 아니라 **어떤 테이블을 어떤 키로 연결했는지**를 꼭 기록해주세요.

완성된 과제는 Github에 업로드하고, 링크를 스프레드시트 'SQL' 시트에 입력해 제출해주세요.

**👀 수행 인증란은 필수입니다.**

---

## 📚 SQL_BASIC_6th_TIL

### 섹션 6. 다량의 자료를 연결 : JOIN

### 5-2. JOIN 이해하기

### 5-3. 다양한 JOIN 방법

### 5-4. JOIN 쿼리 작성하기

### 5-5. JOIN을 처음 공부할 때 헷갈리는 부분

---

## ✨ 선택 강의

- 5-6. JOIN 연습문제: JOIN 문제를 더 연습하고 싶을 때 선택 수강

---

## 🏁 전체 강의 수강 계획

| 주차 | 필수 강의 범위 | 선택 강의 | 완료 여부 |
| --- | --- | --- | --- |
| 1주차 | 1-1 ~ 2-1 | 1 | ✅ |
| 2주차 | 2-2 ~ 2-3 | 2-4 | ✅ |
| 3주차 | 2-5, 2-7 ~ 2-8 | 2-6 | ✅ |
| 4주차 | 3-2 ~ 4-3 | 3-4 | ✅ |
| 5주차 | 4-4 ~ 4-6 | 4-5, 4-7 | ✅ |
| 6주차 | 5-2 ~ 5-5 | 5-6 | ✅ |
| 7주차 | 필수 강의 없음 | 6-2, 6-3, 6-4, 6-5 | 🍽️ |

---

<br>

<!-- 여기까진 그대로 둬 주세요-->

---

# 1️⃣ 개념 정리

아래 키워드 중 중요하다고 생각한 개념을 2개 이상 골라 짧게 정리해주세요. 3개보다 더 많이 정리하고 싶다면 자유롭게 항목을 추가해도 좋습니다.

이번 주 키워드:
- JOIN
- INNER JOIN
- LEFT JOIN
- JOIN key
- alias
- NULL
- 다중 JOIN

## 01.

```
개념 이름: JOIN
개념 설명: 서로 다른 데이터 테이블을 연결하는 것
예시 쿼리:
SELECT
    A.col1,
    A.col2,
    B.col11,
    B.col12
FROM table_a AS A
LEFT JOIN table_b AS B
ON A.key = B.key
```

## 02.

```
개념 이름: INNER JOIN
개념 설명: 두 테이블에서 JOIN 조건에 일치하는, key가 양쪽에 모두 있는 행만 연결하는 JOIN
예시 쿼리:
 SELECT
 col
FROM table_a AS A
INNER JOIN table_b AS B
ON A.key=B.key

```

## (선택) 03.

```
개념 이름:
개념 설명:
헷갈린 점:
```

---

# 2️⃣ 수행 인증란

아래 중 하나 이상을 첨부해주세요.

<img width="457" height="372" alt="강의수강" src="https://github.com/user-attachments/assets/fcc0fba4-b4d0-4521-8504-3ebc1964bb1d" />


---

# 3️⃣ 확인 문제

프로그래머스는 로그인이 필요하므로, 로그인 후 문제 풀이를 진행해주세요.

## 🧩 문제 1

문제 링크: [조건에 맞는 도서와 저자 리스트 출력하기](https://school.programmers.co.kr/learn/courses/30/lessons/144854)

풀이 과정: SELECT B.BOOK_ID,
       A.AUTHOR_NAME,
       DATE_FORMAT(B.PUBLISHED_DATE, '%Y-%m-%d') AS PUBLISHED_DATE
FROM BOOK AS B
JOIN AUTHOR AS A
    ON B.AUTHOR_ID = A.AUTHOR_ID
WHERE B.CATEGORY = '경제'
ORDER BY B.PUBLISHED_DATE ASC;

```
- 사용한 테이블: BOOK, AUTHOR
- JOIN key AUTHOR_ID — 두 테이블에서 저자 ID가 같은 행끼리 연결
- 날짜를 출력한 형식: YYYY-MM-DD

```
<img width="1602" height="627" alt="1" src="https://github.com/user-attachments/assets/43763276-a333-4098-b6f0-8c8d93a1d972" />



## 🧩 문제 2

문제 링크: [상품 별 오프라인 매출 구하기](https://school.programmers.co.kr/learn/courses/30/lessons/131533)

풀이 과정: SELECT P.PRODUCT_CODE,
       SUM(P.PRICE * O.SALES_AMOUNT) AS SALES
FROM PRODUCT AS P
JOIN OFFLINE_SALE AS O
    ON P.PRODUCT_ID = O.PRODUCT_ID
GROUP BY P.PRODUCT_CODE
ORDER BY SALES DESC, P.PRODUCT_CODE ASC;

```
- 연결한 테이블: PRODUCT, OFFLINE_SALE
- JOIN key: PRODUCT_ID
- 집계한 값: 상품코드별 매출액 합계 → SUM(판매가 × 판매량)

```
<img width="1122" height="487" alt="2" src="https://github.com/user-attachments/assets/f76ed841-7efe-4ce7-b7b4-d5adfc8325b2" />


## 🧩 문제 3

문제 링크: [없어진 기록 찾기](https://school.programmers.co.kr/learn/courses/30/lessons/59042)

풀이 과정: SELECT O.ANIMAL_ID, O.NAME
FROM ANIMAL_OUTS AS O
LEFT JOIN ANIMAL_INS AS I
    ON O.ANIMAL_ID = I.ANIMAL_ID
WHERE I.ANIMAL_ID IS NULL
ORDER BY O.ANIMAL_ID ASC;

```
- 기준이 되는 왼쪽 테이블: ANIMAL_OUTS
- LEFT JOIN이 필요한 이유: 보호소 입소 기록이 없는 동물도 결과에 남겨야 하기 때문이다.
- NULL이 발생하는 경우: 입양 기록의 ANIMAL_ID와 일치하는 입소 기록이 없으면, 오른쪽 테이블인 ANIMAL_INS의 열들이 NULL로 표시된다.

```

<img width="1180" height="645" alt="3" src="https://github.com/user-attachments/assets/0e271f60-c7bc-4705-aee2-4e00440c7926" />


## 🧩 문제 4

문제 링크: [있었는데요 없었습니다](https://school.programmers.co.kr/learn/courses/30/lessons/59043)

풀이 과정: SELECT I.ANIMAL_ID, I.NAME
FROM ANIMAL_INS AS I
JOIN ANIMAL_OUTS AS O
    ON I.ANIMAL_ID = O.ANIMAL_ID
WHERE O.DATETIME < I.DATETIME
ORDER BY I.DATETIME ASC;

```
- 사용한 테이블: ANIMAL_INS, ANIMAL_OUTS
- JOIN key: ANIMAL_ID
- 비교한 날짜 컬럼: O.DATETIME(입양일)과 I.DATETIME(보호 시작일)
- 정렬 기준: I.DATETIME ASC

```
<img width="1177" height="545" alt="4" src="https://github.com/user-attachments/assets/c534631f-7eae-4d30-a39e-6d5ec1b2c436" />



---

# 4️⃣ 참고 자료

JOIN 개념이 헷갈린다면 아래 자료를 함께 참고해도 좋습니다.

1. https://data-marketing-bk.tistory.com/entry/SQL-JOIN-%ED%95%9C-%EB%B0%A9%EC%97%90-%EC%A0%95%EB%A6%AC-%EA%B0%9C%EB%85%90%EB%B6%80%ED%84%B0-%EC%BD%94%EB%93%9C%EA%B9%8C%EC%A7%80-%EC%9D%B4%EA%B2%83%EB%A7%8C-%EB%B3%B4%EC%9E%90
2. https://velog.io/@wijoonwu/JOIN

---

# 5️⃣ 이번 주 회고

```
1. INNER JOIN과 LEFT JOIN의 차이를 어떻게 이해했는지: INNER JOIN은 두 테이블에서 연결 조건이 일치하는 행만 가져오고, LEFT JOIN은 왼쪽 테이블의 모든 행을 남긴다. 이때 오른쪽 테이블에 일치하는 행이 없으면 오른쪽 컬럼들이 NULL로 표시된다.
2. JOIN 문제를 풀 때 가장 먼저 확인해야 할 것: 두 테이블을 어떤 공통 컬럼으로 연결할지 확인해야 한다. 그다음 두 테이블에 모두 있는 데이터만 필요한지, 연결되지 않는 데이터도 남겨야 하는지 판단해 JOIN 종류와 기준 테이블을 정한다.
3. JOIN 결과가 예상과 달랐던 경험이 있다면: 입양 기록은 있지만 입소 기록이 없는 동물을 찾는 문제에서 INNER JOIN을 사용하면 찾으려는 동물이 결과에서 빠진다는 점을 알게 되었다. 입양 기록을 기준으로 LEFT JOIN한 뒤, 입소 테이블의 동물 ID가 NULL인 행을 골라야 했다.
```

수고하셨습니다!




