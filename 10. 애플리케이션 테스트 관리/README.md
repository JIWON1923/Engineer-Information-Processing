# ✏️애플리케이션 테스트 관리✏️

## 목차
- 1. 애플리케이션 테스트 케이스 설계
    - [애플리케이션 테스트 케이스 작성](#애플리케이션-테스트-케이스-작성)
    - (애플리케이션 테스트 시나리오 작성)(#애플리케이션-테스트-시나리오-작성)
- 2. 애플리케이션 통합 테스트
    - [애플리케이션 테스트 수행](#애플리케이션-테스트-수행)
    - [애플리케이션 테스트 결과 분석](#애플리케이션-테스트-결과-분석)
    - [애플리케이션 개선 조치사항 작성](#애플리케이션-개선-조치사항-작성)
- 3. 애플리케이션 성능 개선
    - [애플리케이션 성능 분석](#애플리케이션-성능-분석)
    - [애플리케이션 성능 개선](#애플리케이션-성능-개선)

---

# 1. 애플리케이션 테스트 케이스 설계
## 애플리케이션 테스트 케이스 작성
- SW 테스트의 이해
    - 개념
        - 개발된 응용 애플리케이션이나 시스템이 사용자가 요구하는 기능, 성능, 사용성, 안정성 등을 만족하는지 확인하고, 노출되지 않은 소프트웨어의 결함을 찾아내는 활동
    - 필요성
        - **발예향**
        - 오류 발전 관점
            - 잠재된 오류를 발견하고 수정하여 올바른 프로그램을 개발하기 위해 필요
        - 오류 예방 관점
            - 실행 전 동료 검토, 워크스루, 인스펙션 등을 통해 오류를 사전에 발견하는 예방 차원의 필요
        - 품질 향상 관점
            - 사용자의 요구사항 및 기대 수준을 만족하도록 반복적인 테스트를 거쳐 제품의 신뢰도를 향상하는 품질 보증을 위해 필요
        
    - 기본 원칙
        - **결완초집 살정오**
        - 결함이 존재
            - 결함이 존재함을 밝힘(결함을 줄이는 활동)
            - 결함이 없다는 것을 증명할 수는 없음
        - 완벽한 테스팅 불가능
            - 완벽하게 테스팅하려는 시도는 불필요한 시간과 자원 낭비
            - 무한 경로, 무한 입력값으로 인한 테스트 어려움
        - 초기에 테스팅 시작
            - 조기 테스트 설계 시 테스트 결과를 단시간에 알 수 있고, 테스팅 기간 단축, 재작업을 줄여 개발기간 단축 및 결함 예방
            - 요르돈의 법칙 적용
        - 결함 집중
            - 적은 수의 모듈에서 대다수의 결함이 발견 됨
            소프트웨어 테스트에서 오류의 80%는 전체 모듈의 2%에서 발견
            파레토 법친의 내용인 80:20 법칙 적용
        - 살충제 페러독스
            - 동일한 테스트 케이스에 의한 반복적 테스트는 새로운 버그를 찾지 못함
            - 테스트 케이스의 정기적 리뷰와 개선 및 다른 시각에서의 접근 필요
        - 정황에 의존
        - 오류 - 부재의 궤변
            - 요구사항을 충족시켜주지 못하면, 결함이 없어도 품질이 높다고 볼 수 없음.
            
    - 소프트웨어 테스트 프로세서
        - 테스트 계획 -> 테스트 분석 및 디자인 -> 테스트 케이스 및 시나리오 작성 -> 테스트 수행 -> 테스트 결과 평가 및 리포팅
        
    - 소프트웨어 테스트 산출물
        - 테스트 계획서, 테스트 베이시스, 테스트 케이스, 테스트 슈트, 테스트 시나리오, 테스트 스크립트, 테스트 결과서
        
    - 소프트웨어 테스트 유형
        - 프로그램 실행 여부
            - 정적 테스트, 동적 테스트
        - 테스트 기법에 따른 분류
            - 화이트박스 테스트
                - **구결조 조변다 기제데
                - 구문(문장) 커버리지
                - 결정 (선택, 분기) 커버리지
                - 조건 커버리지
                - 조건/결정 커버리지
                - 변경 조건/결정 커버리지
                - 다중 조건 커버리지
                - (기본)경로 커버리지
                - 제어 흐름 테스트
                - 테스트 흐름 테스트
                
            - 블랙 박스 테스트
                - **동경결상 유분페원비**
                - 동등분할 테스트
                - 경곗값 분석 테스트
                - 결정 테이블 테스트
                - 상태 전이 테스트
                - 유스케이스 테스트
                - 분류 트리 테스트
                - 페어와이즈 테스트
                - 원인-결과 그래프 테스트
                - 비교 테스트
                
        - 테스트 시각
            - 검증(Verification), 확인(Validation)
            
        - 테스트 목적
            - **회안성 구회병**
            - 회복 테스트, 안전 테스트, 성능 테스트, 구조 테스트, 회귀 테스트, 병행 테스트
            
        - 테스트 종류
            - 명세 기반 테스트, 구조 기반 테스트, 경험 기반 테스트
            
        - 테스트 케이스
            - 개념
                - 특정 요구사항에 준수하는지 확인하기 위해 개발된 입력값, 실행 조건, 예상된 결과의 집합이다.
            
            - 작성 절차
                - 테스트 계획 검토 및 자료 확보 -> 위험 평가 및 우선순위 결정 -> 테스트 요구사항 정의 -> 테스트 구조 설계 및 테스트 방법 결정 -> 테스트 케이스 정의 -> 테스트 케이스 타당성 확인 및 유지보수
                
            
        - 테스트 오라클
            - 개념
                - 테스트의 결과가 참인지 거짓인지를 판단하기 위해 사전에 정의된 참값을 입력하여 비교하는 기법
            - 종류
                - **참샘휴일**
                - 참 오라클
                - 샘플링 오라클
                - 휴리스틱 오라클
                - 일관성 검사 오라클
            
    
## 애플리케이션 테스트 시나리오 작성
- 테스트 레벨
    - 개념
        - 함꼐 편성되고 관리되는 테스트 활동의 그룹
        - 프로젝트에서 책임과 연관되어 있다.
        - 각각의 테스트 레벨은 서로 독립적이다. 
        
    - 종류
        - **단통시인**
        - 단위 테스트, 통합 테스트, 시스템 테스트, 인수 테스트

    - 테스트 시나리오
        - 개념
            - 테스트 수행을 위한 여러 테스트 케이스의 집합으로서, 테스트 케이스의 동작 순서를 기술한 문서이며 테스트를 위한 절차를 명세한 문서이다.


# 2. 애플리케이션 통합 테스트
## 애플리케이션 테스트 수행
- 단위 테스트
    - 개념
        - 개별적인 모듈을 테스트한다.
        - 구현 단계에서 각 모듈을 구현한 후 수행한다.
    
    - 목 객체 유형
        - **더스드 스가**
        - 더미 객체, 테스트 스텁, 테스트 드라이브, 테스트 스파이, 가짜 객체

- 통합 테스트
    - 개념
        - 소프트웨어 각 모듈 간 인터페이스 관련 오류 및 결함을 찾아내기 위한 체계적인 테스트 기법
    - 수행 방법 분류
        - 빅뱅 방식
        - 하향식 통합
        - 상향식 통합
        - 샌드위치 통합
        
- 테스트 자동화 도구
    - 개념
        - 반복적인 테스트 작업을 스크립트 형태로 구현함으로써, 테스트 시간 단축과 인력 투입 비용을 최소화하는 반면, 쉽고 효율적인 테스트를 진행할 수 있는 방법이다. 
    
    - 도구 유형
        - 정적 분석 도구
            - 애플리케이션을 실행하지 않고 분석하는 도구
            - 코딩 표준, 코딩 스타일, 코드 복잡도 및 남은 결함을 발견하기 위해 사용
        
        - 테스트 실행 도구
            - 작성된 스크립트를 실행하고, 각 스크립트마다 특정 데이터와 테스트 수행 방법을 포함하고 있다.
            - 데이터 주도 접근 방식, 키워드 주도 접근 방식
        
        - 성능 테스트 도구
            - 처리량, 응답시간, 경과시간, 자원 사용률에 대해 가상의 사용자를 생성하고 테스트를 수행함으로써 성능 목표를 달성했는지 확인하는 도구
        
        - 테스트 통제 도구

- 테스트 하네스
    - 개념
        - 컴포넌트 및 모듈을 테스트하는 환경의 일부분으로, 테스트를 지원하기 위한 코드와 데이터
        - 단위 또는 모듈 테스트에 사용하기 ㅜ이해 코드 개발자가 작성
    - 구성요소
        - **드 스슈케 스목**
        - 테스트 드라이버, 테스트 스텁, 테스트 슈트, 테스트 케이스, 테스트 스크립트, 목 오브젝트

## 애플리케이션 테스트 결과 분석
- 테스트 결과 분석 
    - 테스트 리포팅
        - **정요품 결실**
        - 테스트 결과 정리, 테스트 요약문서, 품질 상태, 테스트 결과서, 테스트 실행 절차 리뷰 및 평가
    
- 결함 관리
    - 결함관리 프로세스
        - ** 계기검수 재추최**
        - 결함 관리 계획 -> 결함 기록 -> 결함 검토 -> 결함 수정 -> 결함 재확인 -> 결함 상태 추적 및 모니터링 활동 -> 최종 결함 분석 및 보고서 작성

## 애플리케이션 개선 조치사항 작성 
- 테스트 커버리지
    - 개념
        - 주어진 테스트 케이스에 의해 수행되는 소프트웨어의 테스트 범위를 측정하는 테스트 품질 측정 기준
    - 유형
        - **기라코**
        - 기능 기반 커버리지, 라인 커버리지, 코드 커버리지
        
- 결함의 식별 및 관리
    - 결함의 분류
        - ** 시기지문**
        - 시스템 결함, 기능 결함, GUI 결함, 문서 결함
        
    - 결함 심각도별 분류
        - **치주 보경단**
        - 치명적 결함, 주요 결함, 보통 결함, 경미한 결함, 단순 결함
        

# 3. 애플리케이션 성능 개선
## 애플리케이션 성능 분석
- 애플리케이션 성능 점검 개요
    - 애플리케이션 성능 측정 지표
        - **처응경자**
        - 처리량, 응답시간, 경과시간, 자원 사용률
    
- 애플리케이션 성능 저하 원인
    - DB 관련 성능 저하
        - **락페릭사커**
        - 데이터베이스 락, 불필요한 데이터페이스 패치, 연결누수, 부적절한 커넥션 풀 크기, 확정 관련
        
    - 내부 로직으로 인한 성능 저하
        - 웹 애플리케이션의 인터넷 접속 불량, 특정 파일의 업로드 및 다운로드로 인한 성능 저하, 정상적으로 처리되지 않은 오류 처리로 인한 성능 저하
    
    - 외부 호출로 인한 성능 저하
        - 외부 트랜잭션(호출)이 장시간 수행되거나 타임아웃이 일어나는 경우
        
- 애플리케이션 성틍 테스트 프로세스
    - **도환시성**
    - 성능 테스트 도구 설치 -> 테스트 환경 설정 -> 시나리오 생성 -> 성능 테스트 실행 및 모니터링
    

## 애플리케이션 성능 개선 
- 베드 코드
    - 유형
        - **오문이결침**
        - 오염, 문서부족, 의미 없는 이름, 높은 결합도, 아키텍처 침식
        
- 클린코드
    - 작성 원칙
        - **가단의 중추**
        - 가독성, 단순성, 의존성 최소, 중복성 제거, 추상화
---

# 암기
