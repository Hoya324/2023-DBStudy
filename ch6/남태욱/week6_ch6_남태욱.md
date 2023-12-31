# Chapter 06 데이터 모델링

## 1. 데이터 모델링의 개념

### 데이터베이스 생명주기

1. 요구사항 수집 및 분석
   - 데이터베이스 구축의 범위를 정하는 단계
2. 설계
   - 주요 개념과 업무 프로세스 등을 식별, 설계
3. 구현
   - 스키마를 DBMS에 적용
4. 운영
   - 데이터베이스를 기반으로 소프트웨어를 구축
5. 감시 및 개선
   - 유지보수

### 데이터 모델링 과정

- 데이터베이스 생명주기 중 요구사항 수집 및 분석부터 설계까지의 과정에 해당함
- 설계 단계는 개념적 모델링, 논리적 모델링, 물리적 모델링으로 구성된다.

#### 개념적 모델링 (Conceptual Modeling)

- 요구사항을 수집하고 분석한 결과를 토대로 전체적인 뼈대를 만드는 과정
- 개체(Entity)를 추출하고 각 개체들 간의 관계(Relation)를 정의하여 ER 다이어그램(Entity Relationship Diagram)을 만드는 순서로 진행된다.

#### 논리적 모델링 (Logical Modeling)

- 개념적 모델링에서 만든 ERD를 사용하고자 하는 DBMS에 맞게 매핑하여 실제 모델을 만드는 과정
- 개념적 모델링에서 핵심적인 속성만 추출하였다면, 논리적 모델링에서는 실제 필요한 모든 속성을 추출한다.
- 여러 개체들이 데이터를 중복 저장하는 문제를 해결하기 위해 정규화를 수행한다.
- 데이터 용어 사전과 도메인을 정의하여 데이터의 표준화를 수행한다.

#### 물리적 모델링 (Physical Modeling)

- 작성된 논리적 모델을 실제 컴퓨터의 저장 장치에 저장하기 위한 물리적 구조를 정의하고 구현하는 과정
- DBMS의 특성에 맞게 저장 구조를 정의하여야 데이터베이스가 최적의 성능을 낼 수 있다.

## 2. ER 모델

- ER 모델은 데이터 모델링 과정 중 개념적 모델링에 사용되는 모델이다.
- 사물을 개체(Entity)와 개체 간의 관계(Relationship)로 표현한다.
- 개체는 독립적인 의미를 지니고 있는 유무형의 사람 또는 사물을 말하며, 각 개체는 속성(Attribute)으로 식별한다,
- 개체끼리는 서로 관계를 가진다.

### 개체와 개체 타입

- 개체는 사람, 사물, 장소, 개념 사건과 같이 유무형의 정보를 가지고 있는 독립적인 실체
- 개체 타입이 같은 개체들을 모은 것을 개체 집합이라 부른다.

개체는 다음과 같은 특징을 가진다

- 유일한 식별자에 의해 식별이 가능
- 꾸준한 관리를 필요로 하는 정보
- 반드시 자신의 특징을 나타내는 속성을 포함
- 다른 개체와 최소 한 개 이상의 관계를 맺고 있음

#### ERD에서의 개체 타입 표현

- ERD에서 개체 타입은 직사각형으로 나타낸다.
- 개체 타입은 강한 개체와 약한 개체 타입으로 구분할 수 있다.
- 강한 개체 타입은 일반 직사각형, 약한 개체 타입은 이중 직사각형으로 나타낸다.

#### 개체 타입의 유형

##### 강한 개체 타입

- 다른 개체의 도움없이 독자적으로 존재 가능

##### 약한 개체 타입

- 독자적으로 존재할 수 없고 반드시 상위 개체 타입을 가짐

### 속성

- 개체가 가진 성질

#### ERD에서의 속성 표현

- ERD에서 속성은 타원으로 표현하며, 개체 타입과 실선으로 연결한다.
- 속성명은 타원의 중앙에 표기한다.

#### 속성의 유형

##### 단순속성과 복합 속성

단순속성

- 더 이상 분해가 불가능한 속성

복합 속성

- 분해가 가능한 속성

##### 단일값 속성과 다중값 속성

단일값 속성

- 하나의 값만을 가지는 속성

다중값 속성

- 여러 개의 값을 가지는 속성

##### 저장 속성과 유도 속성

저장 속성

- 다른 속성의 영향 없이 단독으로 저장되는 속성
- 예) 생년월일

유도 속성

- 다른 저장 속성으로부터 유도(계산)된 속성
- 예) 나이

### 관계와 관계 타입

- 관계 타입은 개체 타입 간 연결 가능한 관계를 정의한 것이다.

#### ERD에서의 관계 타입 표현

- ERD에서 관계 타입은 마름모로 표현한다.
- 관계 타입명을 중앙에 표기한다.

#### 관계 타입의 유형

##### 차수에 따른 유형

- 관계 집합에 참여하는 개체 타입의 수를 관계 타입의 차수라고 한다.
- 차수에 따라 n진 관계로 표현한다.

##### 관계 대응 수에 따른 유형

- 관계 대응 수는 두 개체 타입의 관계에 실제로 참여하는 개별 개체 수를 의미한다.
- 관계 대응 수는 개체 타입과 관계 타입을 연결하는 실선 위에 표기하며, 하나만 참여할 경우 1, 두 개 이상 다중으로 참여할 경우 N 혹은 M으로 표기한다.
- 일대일(1:1), 일대다(1:N), 다대일(N:1), 다대다(M:N) 관계가 있다.

##### ISA 관계

- 일부 개체 집합들이 맺고 있는 관계 중에는 상하 관계를 보이는 관계가 있는데, 이때 상위 개체 타입의 특성에 따라 하위 개체 타입이 결정되는 형태를 말한다.
- ERD에서 ISA 관계는 역삼각형으로 표현한다.

##### 참여 제약 조건

- 개체 집합 내 모든 개체가 관계에 참여하는지에 따라 전체 참여와 부분 참여로 구분된다.
- 전체 참여 : 두 줄 실선으로 표현
- 부분 참여 : 단일 실선으로 표현

##### 역할

- 개체 타입 간의 관계에서 각 개체가 담당하는 역할
- 관계에서 역할이 명확하지 않는 경우 명시해야 한다.
- 관계선 위에 표기한다.

##### 순환적 관계

- 하나의 개체 타입이 동일한 개체 타입(자기 자신)과 순환적으로 관계를 가지는 형태
- 개체 타입과 관계 타입 양쪽에 두 개의 관계선을 그려 나타낸다.

### 약한 개체 타입과 식별자

- 약한 개체 타입은 상위 개체 타입의 기본키를 상속받아 사용한다.
- 독립적인 키로는 존재할 수 없지만, 상위 개체 타입의 키와 결합하여 약한 개체 타입의 개별 개체를 고유하게 식별하는 속성을 식별자 혹은 부분키라고 부른다.

### IE 표기법

- 개체 타입과 속성을 직사각형으로 표현
- 관계는 관계 실선을 사용하여 표햔

## 3. ER 모델을 관계 데이터 모델로 사상

- 완성된 ER 모델을 실제 데이터베이스로 구축하기 위해 사상(mapping)을 거처야 한다.

ER 모델을 관계 데이터 모델로 사상하는 방법은 다음과 같이 7단계로 나타낼 수 있다.

| 단계 | 사상할 대상 | 구분 |
|:---:|:---:|:---:|
| 1단계 | 개체 타입 | 강한 개체 타입 |
| 2단계 | 개체 타입 | 약한 개체 타입 |
| 3단계 | 관계 타입 | 이진 1:1 관계 타입 |
| 4단계 | 관계 타입 | 이진 1:N 관계 타입 |
| 5단계 | 관계 타입 | 이진 M:N 관계 타입 |
| 6단계 | 관계 타입 | N진 관계 타입 |
| 7단계 | 속성 | 다중값 속성 |


### 개체 타입의 사상

1. 강한(정규) 개체 타입
   - 정규 개체 타입 E의 경우 대응하는 릴레이션 R을 생성
   - 각 개체 타입의 일반 속성은 각각 새로 생성하는 릴레이션의 속성으로 표시하고, 기본키와 외래키는 PK나 FK 등으로 표시

2. 약한 개체 타입
   - 강한 개체 타입의 키와 자신의 키를 함께 외래키로 사용

### 관계 타입의 사상

- 관계 타입은 각 관계 타입이 맺고 있는 차수와 관계 대응 수에 따라 사상 방식을 구분할 수 있다.
- 이진 관계 타입을 사상하는 방법에는 다음과 같이 네 가지 방법이 있다.

방법 1. 오른쪽 개체 타입 E2를 기준으로 관계 R을 표현

방법 2. 왼쪽 개체 타입 E1을 기준으로 관계 R을 표현

방법 3. 단일 릴레이션 ER로 모두 통합하여 관계 R을 표현

방법 4. 개체 타입 E1, E2와 관계 타입 R을 모두 독립된 릴레이션으로 표현

3. 이진 1:1 관계 타입

- 방법 1~4 까지 모든 유형으로 사상 가능
- 방법 4는 불필요한 개체를 생성하기 때문에 잘 사용하지 않는다.

4. 이진 1:N 관계 타입

- 방법 1 또는 방법 2 유형 사용

5. 이진 M:N 관계 타입

- 방법 4 유형 사용

6. N진 관계 타입

- 방법 4 유형 사용

### 다중값 속성의 사상

- 다중값 속성의 경우 관계 데이터 모델로 직접 사상할 수 없다.
- 아래의 두 가지 방법을 사용하여 사상할 수 있다.

7. 다중값 속성

- 다중값 속성의 개수를 알 수 없는 경우
  - 새로운 릴레이션을 생성한다.
  - 이때 해당 릴레이션은 기존의 키와 함께 자신의 값이 모두 키로 지정되어야 한다.
- 다중값 속성의 개수가 적고 제한 가능한 경우
  - 속성을 릴레이션에 같이 포함한다.
  - 고려해야 할 속성 값이 많아지면 불필요한 속성이 생겨 비효율적이다.
