# SQL 검색의 기본
### sql 생성한 테이블 쿼리
CREATE TABLE AMart (  
  `납품일자` date NOT NULL,  
  `과일` VARCHAR(50) NOT NULL,  
  `크기cm` VARCHAR(50) NOT NULL,  
  `색상` VARCHAR(50) NOT NULL,  
  `재고` VARCHAR(50) NOT NULL,  
  PRIMARY KEY (`과일`)  
) DEFAULT CHARSET=utf8;  
INSERT INTO `AMart` (`납품일자`, `과일`,`크기cm`,`색상`, `재고`) VALUES  
  ('2019-11-01', '사과', '10', '초록색', '3'),  
  ('2019-11-01', '딸기', '3', '빨간색', '5'),  
  ('2019-11-05', '바나나', '15', '노란색', '4'),  
  ('2019-11-13', '메론', '25', '초록색', '3'),  
  ('2019-11-13', '참외', '13', '노란색', '11'),  
  ('2019-11-14', '토마토', '7', '빨간색', '14'),  
  ('2019-11-22', '포도', '15', '보라색', '5'),  
  ('2019-11-25', '수박', '30', '초록색', '2'),  
  ('2019-11-28', '망고', '9', '노란색', '8');  
  
---

- SAMPLE TABLE  

|납품일자|과일|크기cm|색상|재고|
|:---:|:---:|:---:|:---:|:---:|
|2019-11-01|사과|10|초록색|3|
|2019-11-01|딸기|3|빨간색|5|
|2019-11-05|바나나|15|노란색|4|
|2019-11-13|메론|25|초록색|3|
|2019-11-13|참외|13|노란색|11|
|2019-11-14|토마토|7|빨간색|14|
|2019-11-22|포도|15|보라색|5|
|2019-11-25|수박|30|초록색|2
|2019-11-28|망고|9|노란색|8|
---

### SELECT
`SELECT 뒤에는 찾고자하는 대상(Column)들을 입력`
### FROM
`FROM 뒤에는 찾을 대상이 현재 있는 공간(Table)을 입력`
### WHERE
`WHERE 뒤에는 찾고자하는 대상에 대한 구체적인 조건을 추가하여 입력`
`조건을 더 주고 싶은 경우 AND를 활용`  

---
#### SELECT, FROM, WHERE 활용 예제
- A마트에 있는 크기 10cm이상의 과일을 찾아라
```
SELECT 과일 FROM AMart WHERE 크기cm >= 10cm;
```
- A마트에서 파는 과일중에 색은 초록색이고 크기는10cm 이하인 것을 찾아라
```
SELECT 과일 FROM AMart WHERE 색 = "초록색" AND 크기cm <= 10;
```

---
### 그룹함수
`select 뒤에서 그룹함수(column) 와 같이 입력`
- SUM - 선택된 컬럼 값들에 대한 총합계를 구할 때 사용
- AVG - 선택된 컬럼 값들에 대한 평균을 구할 때 사용
- MAX - 선택된 컬럼 값들 중 최대값을 구할 때 사용
- MIN - 선택된 컬럼 값들 중 최소값을 구할 때 사용
- COUNT - 선택된 컬럼에 대한 행의 개수를 구할 때 사용
- VARIANCE - 분산 계산(추가 예정 내용)
- STDDEV - 표준편차 계산(추가 예정 내용)

### DISTINCT
`선택된 컬럼의 중복을 제외한 고유 개수를 구할 때 입력(중복 제거)`  

---
#### 그룹함수, DISTINCT 활용 예제
- 모든 과일의 재고수를 구하라
```
SELECT SUM(재고) FROM AMart;
```
- 크기가 10cm 이하인 과일들의 재고 평균 수를 구하라
```
SELECT AVG(재고) FROM AMart WHERE 크기cm <= 10;
```
- 색상이 노란색인 과일들 중 재고가 가장 많은 과일을 찾아라
```
SELECT 과일, 색상, MAX(재고) FROM AMart WHERE 색상 = '노란색';
```
- 크기가 20cm 이상이고 초록색인 과일들 중 재고가 가장 적은 과일을 찾아라
```
SELECT 과일, 색상, MIN(재고) FROM AMart WHERE 크기cm >= 20 AND 색상 = '초록색';
```
---
### GROUP BY
`일반적으로 집합 함수(COUNT, SUM, AVG 등)와 같이 사용되며 특정 컬럼을 기준으로 그룹화하여 테이블에 존재하는 행들을 그룹별로 구분하기위해 입력`


### HAVING
 `그룹화를 하고 난뒤의 컬럼에 대한 조건을 지정 시 입력(그룹화 하기전의 조건을 지정해주는 WHERE과 비슷함)`

### ORDER BY
`검색된 데이터를 순서대로 정렬시킬 때 입력(기본값은 ASC(오름차순)로 적용)`
- ASC - 오름차순으로 작은 값부터 큰 값으로의 순서 Ex)1,2,3,4,5(문자는 알파벳 순서대로 적용되어 출력)
- DESC - 내림차순으로 큰 값부터 작은 값으로의 순서 Ex)5,4,3,2,1(문자는 알파벳 순서대로 적용되어 출력)




