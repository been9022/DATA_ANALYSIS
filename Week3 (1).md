# 데이터분석 3주차 정규과제

📌데이터분석 정규과제는 매주 정해진 분량의 『*혼자 공부하는 데이터 분석 with 파이썬*』 을 읽고 학습하는 것입니다. 이번 주는 아래의 **DataAnalysis_3rd_TIL**에 나열된 분량을 읽고 공부하시면 됩니다.

아래의 문제를 풀어보며 학습 내용을 점검하세요. 문제를 해결하는 과정에서 개념을 스스로 정리하고, 필요한 경우 제시된 강의를 참고하여 보완하는 것이 좋습니다.

<!-- 강의 링크는 아래와 같습니다.
https://www.youtube.com/watch?v=CE3_InvbmLY&list=PLVsNizTWUw7FGzSRCkQrPEEe-ljVXgS7k&index=6
https://www.youtube.com/watch?v=hhbzUEQWdTg&list=PLVsNizTWUw7FGzSRCkQrPEEe-ljVXgS7k&index=7
-->


## DataAnalysis_3rd_TIL

### 3장 데이터 정제하기
#### 01. 불필요한 데이터 삭제하기
#### 02. 잘못된 데이터 수정하기


## Study Schedule

| 주차  | 공부 범위     | 완료 여부 |
| ----- | ------------- | --------- |
| 1주차 | p.24~81    | ✅         |
| 2주차 | p.84~151   | ✅         |
| 3주차 | p.154~219  | ✅         |
| 4주차 | p.222~279 | 🍽️         |
| 5주차 | p.282~325 | 🍽️         |
| 6주차 | p.328~379 | 🍽️         |
| 7주차 | p.382~430 | 🍽️         |

<br>

<!-- 여기까진 그대로 둬 주세요-->


# 1️⃣ 개념 정리 

01. 불필요한 데이터 삭제하기

데이터 정제: 잘못되거나 불필요한 데이터를 수정·삭제하는 과정
데이터 랭글링: 데이터를 분석에 적합한 형태로 변환하는 전체 과정
NaN: 데이터가 비어 있거나 누락된 상태
불리언 배열: 각 데이터가 조건을 만족하는지 True, False로 나타낸 배열
loc: 행과 열의 이름 또는 조건을 이용해 데이터를 선택
drop(): 특정 행이나 열을 삭제
dropna(): NaN이 있는 행이나 열을 삭제
duplicated(): 중복된 행을 찾아 True로 표시
drop_duplicates(): 중복된 행을 삭제
groupby(): 같은 값을 가진 데이터를 하나의 그룹으로 묶음
sum(): 그룹별 숫자 값을 합산
copy(): 원본에 영향을 주지 않는 데이터프레임 복사본 생성
set_index(): 특정 열을 인덱스로 설정
update(): 다른 데이터프레임의 값으로 기존 데이터프레임을 갱신
reset_index(): 인덱스를 다시 일반 열로 변경
to_csv(): 정제한 데이터프레임을 CSV 파일로 저장

## 02. 잘못된 데이터 수정하기

NaN: 판다스에서 누락된 값을 나타내는 표시
info(): 행과 열의 개수, 데이터 타입, 누락되지 않은 값의 개수 등을 출력
isna(): 값이 누락되었으면 True 반환
notna(): 값이 존재하면 True 반환
fillna(): NaN을 지정한 값으로 채움
replace(): 특정 값이나 문자열 패턴을 다른 값으로 변경
astype(): 열의 데이터 타입을 변경
np.nan: 넘파이에서 제공하는 누락값
정규표현식: 일정한 문자열 패턴을 찾거나 변경하기 위한 규칙
str.contains(): 문자열에 특정 패턴이 포함되었는지 확인
gt(): 지정한 값보다 큰지 확인
lt(): 지정한 값보다 작은지 확인
eq(): 지정한 값과 같은지 확인
dropna(): 누락값이 있는 행이나 열을 삭제
update(): 다른 데이터프레임의 값을 기존 데이터프레임에 반영
apply(): 데이터프레임의 행이나 열에 함수를 반복 적용


# 2️⃣ 수행 인증

<img width="1107" height="687" alt="데분6" src="https://github.com/user-attachments/assets/88de833c-f478-4de0-a194-2b45bab55654" />
<img width="1067" height="680" alt="데분5" src="https://github.com/user-attachments/assets/d43fe122-1f12-436a-8578-1a96ebeaa3da" />
<img width="1162" height="467" alt="인증키" src="https://github.com/user-attachments/assets/2de52b03-6775-4be4-bdd6-067297af40dd" />
<img width="1430" height="692" alt="데분3" src="https://github.com/user-attachments/assets/d9384760-b885-4139-af7f-c592ffa714aa" />
<img width="1720" height="697" alt="데분2" src="https://github.com/user-attachments/assets/93052d82-4f0c-45dd-a4df-9955cca31564" />
<img width="1840" height="672" alt="데분1" src="https://github.com/user-attachments/assets/fafb64bc-dc8f-4ccd-9e9f-5706583b4f36" />


<br>
<br>

# 3️⃣ 확인 문제

## 문제 1.

> **🧚Q. 다음 두 데이터프레임 df1, df2를 합쳐서 데이터프레임 df3를 만들려고 합니다.**  
> 적절한 판다스 명령을 선택해주세요.

<table>
<tr>

<td>

### df1

| index | col1 | col2 |
|-------|------|------|
| 0     | x    | 5    |
| 1     | y    | 6    |
| 2     | z    | 7    |

</td>

<td>

### df2

| index | col3 | col4 |
|-------|------|------|
| 0     | x    | 50   |
| 1     | y    | 60   |
| 2     | w    | 70   |

</td>

<td align="center" valign="middle">

<h2> ➜ </h2>

</td>

<td>

### df3 (결과)

| index | col1 | col2 | col3 | col4 |
|-------|------|------|------|------|
| 0     | x    | 5.0  | x    | 50.0 |
| 1     | y    | 6.0  | y    | 60.0 |
| 2     | z    | 7.0  | NaN  | NaN  |
| 3     | NaN  | NaN  | w    | 70.0 |

</td>

</tr>
</table>

```
1️⃣ pd.merge(df1, df2)
2️⃣ pd.merge(df1, df2, how='left')
3️⃣ pd.merge(df1, df2, left_on='col1', right_on='col3', how='outer')
4️⃣ pd.merge(df1, df2, left_on='col1', right_on='col3', how='inner')
```

```
정답: 3️⃣ pd.merge(df1, df2, left_on='col1', right_on='col3', how='outer')

이유: df1의 col1과 df2의 col3을 기준으로 같은 값을 합쳐야 한다. how='outer'를 사용하면 양쪽에 공통인 x, y뿐 아니라 한쪽에만 있는 z, w도 모두 결과에 남고 짝이 없는 값은 NaN으로 표시된다. 
```



### 🎉 수고하셨습니다.
