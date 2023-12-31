# 1. 데이터 모델링의 개념

- 건축에 비교
    - 지반 설계 : 데이터베이스 설계
    - 건물 설계 : 소프트웨어 설계

- 데이터 모델링
    - 현실 세계의 복잡한 개념을 단순화하고 추상화시켜 데이터베이스화하는 과정
    - 최종적으로 구축된 데이터베이스는 현실 세계의 대상이 되었던 개념과 일치한다.

### 1) 데이터베이스 생명주기

요구사항 수집 및 분석 → 설계 → 구현 → 운영 → 감시 및 개선 → 다시 처음

- 데이터베이스 생명주기
    - 데이터베이스의 생성과 운영에 관련된 특징

1. 요구사항 수집 및 분석

   사용자들의 요구사항을 듣고 분석하여 데이터베이스 구축의 범위를 정하는 단계


1. 설계

   분석된 요구사항을 기초로 주요 개념과 업무 프로세스 등을 식별하고(개념적 설계), 사용하는 DBMS의 종류에 맞게 변환(논리적 설계)한 후, 데이터베이스 스키마를 도출(물리적 설계)한다.

   → 개념적 설계 → 논리적 설계 → 물리적 설계

2. 구현

   생성된 스키마를 실제 DBMS에 적용하여 테이블 및 관련 객체(뷰, 인덱스 등)를 만든다.

3. 운영

   구현된 데이터베이스를 기반으로 소프트웨어를 구축하여 서비스를 제공한다.

4. 감시 및 개선

   운영에 따른 시스템의 문제를 관찰하고 데이터베이스 자체의 문제점을 파악하여 개선한다. 데이터베이스가 지속적으로 운영될 수 있도록 변경 및 유지 보수를 한다.


### 2. 데이터 모델링 과정

### 요구사항 수집 및 분석

- 담당자는 구축 할 데이터베이스와 관련된 전문적인 지식을 갖추고 있어야 한다. 관련 자료를 수집할 때도 가장 기초적인 내용에 중점을 두고 진행해야 한다.
- 요구사항 수집 및 분석 방법
    - 실제 문서를 수집하고 분석한다.
    - 담당자와의 인터뷰나 설문조사를 통해 요구사항을 직접 수렴한다.
    - 비슷한 업무를 처리하는 기존의 데이터베이스를 분석한다.
    - 각 업무와 연관된 모든 부문을 살펴본다.

  → 사용자의 요구사항은 대부분 모호하며 사용자마다 쓰는 용어도 달라 개념을 명확하게 파악하기 아렵다. 하지만 이런 모호성을 제거하고 최대한 구체적이고 명확하게 정리해야 한다.


### 개념적 모델링

- 요구사항을 수집하고 분석한 결과를 토대로 업무의 핵심적인 개념을 구분하고 전체적인 뼈대를 만드는 과정
- 핵심적인 개념을 구분
    - entity를 추출
    - entity간의 관계를 정의
    - ER다이어그램을 만드는 과정까지

- 가장 핵심적인 개체와 개별 개체를 식별할 수 있는 핵심 속성(PK), 각 개체 간의 관계를 정의

- 개념적 모델링은 데이터베이스의 큰 골격을 만드는 과정
- 완성된 ER다이어그램이 사용자의 요구사항을 제대로 반영하였는지, 업무 처리 절차에는 문제가 없었는지 점검.

### 논리적 모델링

- 개념적 모델링에서 만든 ER다이어그램을 사용하고자 하는 DBMS에 맞게 사상(매핑)하여 실제 데이터베이스로 구현하기 위한 모델을 만드는 과정
- 논리적 모델링의 몇 가지 과정
    - 개념적 모델링에서 추출하지 않았던 상세 속성들을 모두 추출한다.
    - 정규화 수행
    - 데이터의 표준화

### 물리적 모델링

- 작성된 논리적 모델을 실제 컴퓨터의 저장 장치에 저장하기 위한 물리적 구조를 정의하고 구현하는 과정
    - DBMS의 특성에 맞게 저장 구조를 정의하여야 최적의 성능을 낼 수 있다.

- 물리적 모델링을 할 때 트랜잭션, 저장 공간 설계 측면에서 고려할 사항
    - 응답시간을 최소화
        - 응답시간 : 트랜잭션이 시작되어 종료될 때까지 걸리는 시간
    - 얼마나 많은 트랜잭션을 동시에 발생시킬 수 있는지 검토
    - 데이터가 저장될 공간을 효율적으로 배치
        - 인덱스 설계


---

# 2. ER 모델

- ER 모델
    - 개체(entity)와 개체 간의 관계(relationship)로 표현한다.
    - 각 개체마다 고유한 특성을 나타내는 속성이 있다.
    - 개념적 모델링 단계에서 사용하는 모델이다.

## 1. 개체와 개체 타입

- 개체 : 사람, 사물, 장소, 개념, 사건과 같이 유무형의 정보를 가지고 있는 독립적인 실체 ex) 각각의 책
- 개체 타입 : 비슷한 속성을 가진 개체 ex) 도서 (프로그래밍 언어의 데이터 타입)
- 개체 집합 : 공통된 속성을 가진 개체들의 모임

- 개체의 특징
    - 유일한 식별자에 의해 식별이 가능하다.
    - 꾸준한 관리를 필요로 하는 정보이다.
    - 업무 프로세스에 이용
    - 두 개 이상 영속적으로 존재
    - 반드시 자신의 특징을 나타내는 속성을 포함한다.
    - 다른 개체와 최소 한개 이상의 관계를 맺고 있다.

### 개체 타입의 ER 다이어그램 표현

ER 다이어그램 상에서 개체 타입은 직사각형으로 나타낸다.

- 개체
    - 강한 개체 : 보통 개체타입, 직사각형으로 나타냄
    - 약한 개체 : 이중 직사각형

### 개체 타입의 유형

- 강한 개체
    - 다른 개체 도움 없이 독자적으로 존재 가능
- 약한 개체
    - 독자적으로 존재할 수 없고, 상위 개체 타입을 가진다.

ex) 직원의 부양가족은 직원이 존재해야 존재 가능. 직원이 강한 개체, 부양가족이 약한 개체이다.

## 2. 속성

속성(attribute)은 개체가 가진 성질을 말한다.

ex) ‘축구의 역사’의 경우 도서이름은 ‘축구의 역사’, 출판사는 ‘굿스포츠’, 가격은 ‘8000’원이다.

→ 개체 타입은 ‘도서’이고, 속성은 ‘도서이름’, ‘출판사’, ‘도서단가’가 되겠다.

### 속성의 ER 다이어그램 표현

- 개체 타입을 나타내는 직사각형과 실선으로 연결된다.
- 속성의 이름은 타원의 중앙에 표기
- 개체를 유일하게 식별할 수 있는 키일 경우 밑줄을 긋는다.

### 속성의 유형

- 단순 속성과 복합 속성
    - 단순 속성 : 더 이상 분해가 불가능한 속성
        - ex)학생번호
    - 복합 속성 : 독립적인 의미를 가진 속성, 분해 가능한 속성, 큰 타원 아래 작은 타원으로 연결
        - ex) 주소(시, 동)
- 단일값 속성과 다중값 속성
    - 단일값 속성 : 하나의 값만 가지는 속성
        - ex)학생번호
    - 다중값 속성 : 여러 개의 값을 가지는 속성, 이중타원으로 표현
        - ex) 취미, 학위
- 저장 속성과 유도 속성
    - 저장 속성 : 다른 속성의 영향 없이 단독으로 저장되는 속성
        - ex) 생년월일의 경우 학생 개개인이 가지고 있는 고유한 값
    - 유도 속성 : 다른 저장 속성으로부터 유도된 속성, 점선타원 표현
        - ex) 나이는 생년월일로부터 계산될 수 있는 값이므로 유도 속성

## 3. 관계와 관계 타입

- ER모델은 개체와 개체 사이의 관계를 표현한다.
    - 관계 : 개체 사이의 연관성
    - ex) 고객이 도서를 구입한다.
        - 고객 개체 타입과 도서 개체 타입은 구입한다라는 개념으로 연결된다.
- 관계 타입(relationship type)
    - 개체 타입과 개체 타입 간의 연결 가능한 관계를 정의한 것
- 관계 집합(relationship set)
    - 관계로 연결된 집합

### 관계 타입의 ER 다이어그램 표현

- 마름모로 표현하면 관계 타입의 이름은 기호의 중앙에 표기

### 관계 타입의 유형

- 관계 타입의 차수 : 관계 집합에 참가하는 개체 타입의 수
- 차수에 따른 관계 타입의 유형
    - 1진 관계
        - 자기 자신과 관계를 맺는 경우
        - ex) 학생 개체에서 학생들 간 멘토링 관계를 맺은 경우
    - 2진 관계
        - 두 개의 개체가 관계를 맺는 경우
        - ex) 학생 개체 타입과 학과 개체 타입은 소속이라는 관계
    - 3진 관계
        - 세 개의 개체가 관계를 맺는 경우
        - ex) 자동차 회사 직원은 부품을 조립하여 하나의 자동차를 만드는 프로젝트를 ‘수행’하는 관계

- 관계 대응 수에 따른 유형
    - 일대일(1:1) 관계
        - 개체와 개체가 일대일로 대응하는 관계
        - ex) 사원이 개인별로 한 대의 컴퓨터만 사용하는 경우
    - 일대다(1:N), 다대일(N:1) 관계
        - 하나의 개체가 다른 타입의 여러 개체와 관계를 맺는 경우
        - ex) 하나의 학과에는 여러 명의 학생이 소속되어 있는 경우
    - 다대다(N:N) 관계
        - 서로 복합적인 관계를 맺고 있는 경우
        - ex) 한 학생은 여러 강좌를 수강할 수 있고, 한 강좌 역시 여러 학생이 들을 수 있다.

- 관계 대응 수의 최솟값과 최댓값
    - 1:1, 1:N, M:N 에서 1, M, N은 각 개체가 관계에 참여하는 최댓값을 의미

  | 관계 | (min1, max1) | (min2, max2) |
      | --- | --- | --- |
  | 1:1 | (0, 1) | (0, 1) |
  | 1:N | (0, *) | (0, *) |
  | M:N | (0, *) | (0, *) |

    - ex) 학과와 학생 (1 : N)
        - 학과의 관점에서 ‘소속’관계는 최소 0번(학생이 없는 경우)에서 최대 *번(학과에 학생이 여러 명인 경우)으로 표기할 수 있다.


### ISA 관계

- ISA관계
    - 상위 개체 타입의 특성에 따라 하위 개체 타입이 결정되는 형태
    - 상위 개체 타입 : 슈퍼 클래스
    - 하위 개체 타입 : 서브 클래스
    - ISA관계는 역삼각형으로 표현한다. 역삼각형 위에는 슈퍼클래스, 아래에는 서브클래스를 관계 실선으로 연결

### 참여 제약 조건

- 관계의 특성 중 하나
- 개체 집합 내 모든 개체가 관계에 참여하는지 유무에 따라 전체 참여와 부분 참여로 구분 가능하다.
    - 전체 참여 : 개체 집합의 모든 개체가 관계에 참여
        - 개체 타입과 관계를 두 줄 실선으로 표현
        - (최솟값, 최댓값) : 최솟값 1 이상
    - 부분 참여 : 일부만 참여
        - 단일 실선
        - (최솟값, 최댓값) : 최솟값 0 이상

### 역할

- 개체 타입 간의 관계를 표현할 때 각 개체들은 고유한 역할을 담당한다.
    - ex) 교수와 학생의 관계
      교수 개체 타입은 ‘지도한다’. 학생 개체 타입은 ‘지도받는다’라는 역할을 한다.
- 일반적으로 역할은 관계만으로 알 수 있으므로 생략한다.

### 순환적 관계

- 하나의 개체 타입이 동일한 개체 타입(자기 자신)과 순환적으로 관계를 가지는 형태를 말한다.

## 4. 약한 개체 타입과 식별자

- 강한 개체 타입
    - 직원 개체 타입처럼 독립적으로 식별할 수 있는 개체를 가지고 있는 개체 타입
    - 직원 개체 타입의 ‘직원번호’와 같이 각 개체를 식별할 수 있는 기본키를 가진다.
- 약한 개체 타입
    - 가족 개체 타입처럼 상위 개체 타입이 결정되지 않으면 개별 개체를 식별할 수 없는 종속된 개체 타입
    - 자신의 기본키만으로 식별이 어려우므로 상위의 강한 개체 타입의 기본키와 결합하여 식별하는데, 그 속성을 식별자 혹은 부분키라고 한다.

- 약한 개체 타입과 식별자

| 의미 | 설명                                                                  |
| --- |---------------------------------------------------------------------|
| 약한 개체 타입 | - 강한 개체 타입이 있어야 존재할 수 있음,이중 직사각형으로 표현                               |
| 식별 관계 타입 | - 강한 개체 타입과 약한 개체 타입의 관계를 나타냄, 강한 개체 타입의 기본키를 상속받아 사용함, 이중 마름모꼴로 표현 |
  | 키 | - 강한 개체 타입의 키 속성                                                    |
  | 식별자 | - 약한 개체 타입에서 개별 개체를 구분하는 속성, 키라고 하지 않고 식별자라고 부름                     |

## 5. IE 표기법

- 피터 첸이 제안한 ER 모델의 기본적인 표기법과 다른 표기법인 IE표기법이 존재한다.
- IE 표기법에서 개체 타입과 속성은 직사각형으로 표현한다.
- 관계는 마름모꼴 대신 개체 타입인 직사각형을 관계 실선으로 연결하고 여러가지 모양의 기호를 이용하여 관계 대응 수 등을 표현한다.

---

# 3. ER모델을 관계 데이터 모델로 사상

- 관계 데이터 모델은 릴레이션 하나로 데이터베이스의 논리적 구조를 표현하지만 ER모델은 개체 타입, 관계 타입, 속성으로 표현한다.
- ER모델을 관계 데이터 모델로 사상하는 방법은 7단계 알고리즘으로 나타낼 수 있다.

### 1. 개체 타입의 사상

[1단계] 강한 개체 타입

- 정규 개체 타입 E의 경우 대응하는 릴레이션 R을 생성한다.
- 각 개체 타입의 일반 속성은 각각 새로 생성하는 릴레이션의 속성으로 표시하고, 기본키와 외래키는 PK나 FK 등으로 표시한다.

[2단계] 약한 개체 타입

- 자신의 키와 함께 강한 개체 타입의 키를 외래키로 사상하여 자신의 기본키를 구성한다.

### 2. 관계 타입의 사상

[방법1] 오른쪽 개체 타입 E2를 기준으로 관계 R을 표현한다.

- 오른쪽 개체가 왼쪽 개체 타입의 기본키를 자신의 외래키로 가진다.
    - E1(KA1, A2)
    - E2(KA2,A4,Ka1)

[방법2] 왼쪽 개체 타입 E1를 기준으로 관계 R을 표현

- 왼쪽 개체가 오른쪽 개체 타입의 기본키를 자신의 외래키로 가진다.
    - E1(KA1, A2, KA2)
    - E2(KA2,A4)

[방법3] 단일 릴레이션 ER로 모두 통합하여 관계 R을 표현한다.

- ER(KA1, A2, KA2, A4)

[방법4] 개체 타입 E1, E2와 관계 타입 R 모두 독립된 릴레이션으로 표현한다.

[3단계] 이진 1:1 관계 타입

- 방법1과 방법2 사용

[4단계] 이진 1:N 관계 타입

- 방법1과 방법2 사용

[5단계] 이진 M:N 관계 타입

- 방법 4 사용
- 새롭게 만든 릴레이션을 교차 테이블이라고 한다.

[6단계] N진 관계 타입

- 방법 4 사용
- 생성되는 릴레이션의 키는 각 개체 타입의 기본키를 모은 복합 키 사용

[7단계] 다중값 속성

- 다중값 속성의 개수를 알 수 없는 경우 [방법4]를 사용
- 다중값 속성의 개수가 적고 제한 가능한 경우 [방법3]을 사용