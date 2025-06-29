# ELK Stack이란?

ELK Stack는 세 개의 오픈소스 도구의 조합으로, 로그 및 이벤트 데이터를 수집, 저장, 분석, 시각화하는 데 사용되는 로그 분석 플랫폼

**ELK = Elasticsearch + Logstash + Kibana**

## 구성요소

### 1. Elasticsearch
#### 1. 개요
- 분산형 검색 및 분석 엔진
- JSON 형식의 데이터를 저장하고, 빠르게 검색 가능
- 실시간 로그 분석, 저체 텍스트 검색 등에 사용

#### 2. 주요 기능
- Inverted Index(역색인) 기반 빠른 검색 성능
- JSON 기반의 RESTful API 지원
- Full-text serach 지원
- 분산 클러스터 구성 가능
- Aggregation 기능을 통한 통계 분석

#### 3. 사용 사례
- 로그 및 이벤트 데이터 저장, 검색
- 상품 검색 엔진 (ex. 쿠팡, 아마존)
- 실시간 매트릭 수집 및 분석

### 2. Logstash
#### 1. 개요
- 데이터 수집 및 처리 파이프라인 도구
- 다양한 입력 소스(log file, DB, Kafka 등)로부터 데이터를 받아 필터링, 변환 후 Elasticsearch에 전달

#### 2. 주요 기능
- 다양한 input plugin 지원 (file, syslog, jdbc 등)
- 필터링 (grok, mutate, date 등)
- 출력 대상 다양 (Elasticsearch, file, stdout 등)
- 파이프라인 구성 유연

#### 3. 사용 사례
- 서버 로그 수집 및 전처리
- CSV 파일 → Elasticsearch 적재
- 정형/비정형 데이터 가공 처리

### 3. Kibana
#### 1. 개요
- Elasticsearch 데이터를 시각화하는 웹 UI 도구
- 대시보드 생성, 로그 탐색, 분석 기능 제공

#### 2. 주요 기능
- Discover: 데이터 탐색
- Visualize: 그래프/차트/히트맵 등 시각화 생성
- Dashboard: 여러 시각화 요소 조합
- Dev Tools: 콘솔을 통해 Elasticsearch 쿼리 실행

#### 3. 사용 사례
- 실시간 로그 분석 대시보드
- 이상 징후 탐지 및 시각화
- 보안 분석, 사용자 행동 분석

### 4. Beats
- 경량 데이터 수집기 (ex. Filebeat, Metricbeat 등)
- Filebeat : 로그 파일 수집
- Metricbeat : 시스템/애플리케이션 매트릭 수집

## ELK Stack의 동작 구조
```text
[로그 소스] 
    ↓
[Logstash] ← 수집/가공
    ↓
[Elasticsearch] ← 저장/검색
    ↓
[Kibana] ← 시각화
```

## ELK 스택 구축하기 in Docker
### 1. Java 설치
<pre>
sudo apt-get update
sudo apt-get install oepnjdk-11-jdk // OpenJDK 11 이상 버전 권고

java--version // java 버전 확인
</pre>

### 2. ELK 실행을 위한 디렉토리 구성
<pre>
mkdir elk-stack && cd elk-stack // 작업 대상 경로에서 파일 생성하기
mkdir logstash
touch docker-compose.yml
touch logstash/logstash.conf
</pre>

### 3. docker-compose.yml 파일 작성
elk-stack\docker-compse.yml 파일 참고

### 4. logstash.conf 파일 작성
elk-stack\logstash\logstash.conf 파일 참고

### 5. 실행
sudo apt install docker-compose

docker-compose up

### 6. 실행 확인
http://localhost:9200 → Elastic search
http://localhost:5601 → Kibana

