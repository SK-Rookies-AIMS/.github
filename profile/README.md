# 🏭 AIMS - AI 기반 자동차 스마트팩토리 관제 시스템 
> SK쉴더스 루키즈 지능형 애플리케이션 개발 5기 최종 프로젝트 - 1조 보안 관제
>
> 배포 주소: https://aims-factory.com

**AIMS**: 자동차 제조 공정의 **설비·센서 이벤트를 실시간으로 분석**하여 이상을 탐지하고, 관제사의 신속한 대응을 지원하는 스마트팩토리 통합 관제 플랫폼

- ML·SHAP 기반 불량 탐지 및 타 공정 전이 예측
- RAG·LLM 기반 관제사 숙련도별 AI 대응 매뉴얼 제공
- 위험도·발생 빈도·조치 이력 기반 알림 우선순위 산정
- AGV 운행 상태와 공정별 물류 흐름 실시간 시각화
- Kafka 기반 MSA와 Kubernetes를 활용한 확장·복구 가능한 운영 환경 구축

&nbsp;
## 📌 Application
<table>
  <tr>
    <th align="center">메인 대시보드</th>
  </tr>
  <tr>
    <td align="center">
      <img
        width="100%"
        alt="메인 대시보드"
        src="https://github.com/user-attachments/assets/b479308e-3a3c-4292-ba1a-51f949b5225a"
      />
    </td>
  </tr>
</table>
<table>
  <tr>
    <th align="center" width="50%">프레스 공정</th>
    <th align="center" width="50%">차체 공정</th>
  </tr>
  <tr>
    <td align="center" valign="middle">
      <img
        width="100%"
        height="340"
        alt="프레스 공정"
        src="https://github.com/user-attachments/assets/55b670c3-79e7-422b-ad40-cb2105a2a523"
      />
    </td>
    <td align="center" valign="middle">
      <img
        width="100%"
        height="165"
        alt="차체 공정"
        src="https://github.com/user-attachments/assets/71c63375-1128-4b97-8820-a7d64ebb1666"
      />
      <br />
      <img
        width="100%"
        height="165"
        alt="차체 공정 상세"
        src="https://github.com/user-attachments/assets/25d1b4ff-49d4-433f-afaa-495b308b3ba4"
      />
    </td>
  </tr>

  <tr>
    <th align="center" width="50%">도장 공정</th>
    <th align="center" width="50%">의장 공정</th>
  </tr>
  <tr>
    <td align="center" valign="middle">
      <img
        width="100%"
        height="165"
        alt="도장 공정"
        src="https://github.com/user-attachments/assets/cce03261-3b1a-490b-99ee-c1718ef87845"
      />
      <br />
      <img
        width="100%"
        height="165"
        alt="도장 공정 상세"
        src="https://github.com/user-attachments/assets/21d186a8-50e3-4643-8fe1-93512467e85e"
      />
    </td>
    <td align="center" valign="middle">
      <img
        width="100%"
        height="340"
        alt="의장 공정"
        src="https://github.com/user-attachments/assets/6fdc0b6e-a7df-4e89-b196-35831e8a6e3f"
      />
    </td>
  </tr>
</table>

<br />

<table>
  <tr>
    <th align="center" width="50%">검사 현황</th>
    <th align="center" width="50%">검사 분석 결과</th>
  </tr>
  <tr>
    <td align="center" valign="middle">
      <img
        width="100%"
        height="340"
        alt="검사 현황"
        src="https://github.com/user-attachments/assets/54c6f757-f744-46d3-841f-5eba239fac1d"
      />
    </td>
    <td align="center" valign="middle">
      <img
        width="100%"
        height="340"
        alt="검사 분석 결과"
        src="https://github.com/user-attachments/assets/aacd3943-f9e5-44c5-af39-95a825a32497"
      />
    </td>
  </tr>
</table>


&nbsp;
## ✨ Main Features
### 1. AI 지능형 분석 - 공정 불량 탐지 및 타공정 전이 예측(ML) 
<table>
  <tr>
    <th align="center">혼동행렬</th>
    <th align="center">성능지표</th>
  </tr>
  <tr>
    <td align="center" width="45%">
      <img
        width="100%"
        alt="혼동행렬"
        src="https://github.com/user-attachments/assets/50579fc0-ac86-4150-b64f-8c6f23fde54e"
      />
    </td>
    <td align="center" width="55%">
      <img
        width="100%"
        alt="성능지표"
        src="https://github.com/user-attachments/assets/c55b5b27-a0df-4a70-bcfd-3b5b749e0360"
      />
    </td>
  </tr>
</table>

<img width="1893" height="701" alt="image" src="https://github.com/user-attachments/assets/8cd35159-3efb-483f-ba94-5e90f8d036a3" />


* **LightGBM, CatBoost, XGBoost, Logistic Regression** 총 4가지 머신러닝 모델을 학습하고, **재현율·정밀도·F1-Score·정확도**를 기준으로 성능을 비교
* 제조 데이터의 **비선형 패턴과 특성 간 상호작용**, 학습 속도 및 예측 성능을 종합적으로 고려하여 **LightGBM을 최종 모델로 선정**
* 4개의 공개 제조 데이터셋을 AIMS 제조 이벤트 구조로 통합하고, 센서값과 공정·설비 정보를 기반으로 **35개의 주요 Feature**를 생성
* 결측값과 이상치를 처리하고, **데이터 불균형 및 Feature Leakage 문제**를 개선하여 모델의 불량 탐지 성능을 향상
* 최종 LightGBM 모델은 재현율 93.41%, 정밀도 76.74%, F1-Score 84.26%, 정확도 92.99%의 성능을 달성
* 제조 이벤트를 분석하여 **현재 공정의 불량 가능성과 다음 공정으로의 불량 전이 확률**을 예측하고, **SHAP 기반 주요 원인**을 함께 제공

&nbsp;
### 2. 맞춤형 대응 - AI 기반 이상 대응 매뉴얼
<img width="1751" height="898" alt="image" src="https://github.com/user-attachments/assets/852f0ff4-7e12-42e4-841e-bb5bfe8559ff" />

| 이상 이벤트 발생 | 주니어 | 시니어 |
|---|---|---|
| <img width="582" height="506" alt="이상 이벤트 발생" src="https://github.com/user-attachments/assets/faac7e24-4756-4ee7-be91-bf9e813e6a2c" /> | <img width="582" height="506" alt="주니어" src="https://github.com/user-attachments/assets/9e0900e0-50ef-4b2f-aafd-7d18428d8a58" /> | <img width="565" height="500" alt="시니어" src="https://github.com/user-attachments/assets/b8444157-0aad-4c70-b03f-dfe28db7b259" /> |
- **RAG**는 설비 조치 매뉴얼, 기술 문서·사양, 과거 장애 사례, 체크리스트 등 AI가 참고할 지식 문서를 벡터 데이터베이스에 저장
- 이상 이벤트가 입력되면 **Vector Search**를 통해 이벤트와 유사한 문서를 검색하고, 관련 정보를 LLM의 답변 근거인 **컨텍스트**로 제공
- **Prompt**에는 AI의 역할과 답변 기준을 정의하고, 답변이 `원인 분석 → 단계별 조치 방법 → 주의사항 → 추가 점검 사항` 순서로 생성되도록 구성
- 담당자의 **숙련도에 따라 설명 수준을 조절**하고, 전문 용어를 쉽게 설명하며 검색된 매뉴얼을 기반으로 답변하도록 프롬프트 조건을 설정
- **Data**에는 회사 정보, 업무 규정·정책, 설비·라인 정보, 내부 용어·코드 체계 등 회사 고유의 도메인 정보를 구성
- RAG에서 검색한 근거 문서와 Prompt의 답변 형식, 회사 Data를 함께 활용하여 **회사 환경에 맞는 일관되고 신뢰도 높은 대응 가이드**를 생성
- 생성된 가이드는 담당자가 즉시 활용할 수 있도록 **원인, 조치 절차, 주의사항 및 점검 항목**으로 구조화하여 대시보드에 제공

&nbsp;
### 3. 현장 대응형 알림 우선순위
<table>
  <tr>
    <th align="center" width="50%">알림 우선순위 구조</th>
    <th align="center" width="50%">알림 목록</th>
  </tr>
  <tr>
    <td align="center" valign="middle">
      <img
        width="100%"
        alt="알림 우선순위 구조"
        src="https://github.com/user-attachments/assets/3904ce4a-794d-46fb-b5f2-1d5ecef65e93"
      />
    </td>
    <td align="center" valign="middle">
      <img
        width="100%"
        alt="알림 목록"
        src="https://github.com/user-attachments/assets/7d5e0620-d89d-4cd5-bb2b-b0581a05ef4e"
      />
    </td>
  </tr>

  <tr>
    <th align="center" width="50%">알림 조치</th>
    <th align="center" width="50%">알림 상세</th>
  </tr>
  <tr>
    <td align="center" valign="middle">
      <img
        width="100%"
        alt="알림 조치"
        src="https://github.com/user-attachments/assets/7eea0f61-5bdf-4b07-8db4-b91353237202"
      />
    </td>
    <td align="center" valign="middle">
      <img
        width="100%"
        alt="알림 조치 후 상세"
        src="https://github.com/user-attachments/assets/99de086e-f817-445e-ad7f-f37d17bae989"
      />
    </td>
  </tr>
</table>

- 기존 관제에는 **Risk Score만으로 설비 위험도를 판단**하여 반복 발생 여부와 과거 조치 이력이 반영되지 않고, 다수의 알림 발생 시 우선순위를 구분하기 어려운 한계가 존재
- FMEA 개념을 현장 관제 환경에 적용하여 **Risk Score, Occurrence, Detection**을 반영한 **Adaptive eRPN 기반 알림 우선순위 알고리즘**을 설계
- **Risk Score**는 현재 이벤트의 물리적 위험도, **Occurrence**는 동일·유사 이벤트의 반복 발생 빈도, **Detection**은 과거 조치 이력과 실제 대응 필요성을 기준으로 산정
- `Priority Score = Risk × (1 + Occurrence) × (1 + Detection)` 공식을 적용하여 여러 이상 알림의 중요도를 정량적으로 계산
- 산정된 우선순위 점수를 기준으로 **온도·진동·전류 이상 알림을 높은 점수순으로 정렬**하여 관제 화면 상단에 우선 노출
- 우선순위가 산정된 알림은 **WebSocket을 통해 실시간으로 전송**하여 관제사가 긴급한 이상 상황을 즉시 확인하고 대응할 수 있도록 구성


&nbsp;
### 4. 실시간 데이터 수집 및 스트리밍 - WebSocket 기반 AGV 운반
<img width="2490" height="1186" alt="AGV" src="https://github.com/user-attachments/assets/cefa013b-83f0-424b-bb96-04ec057348e3" />

- **Kafka Consumer**가 제조 분석 결과를 수신하고, 공정 위험도가 높거나 `isAbnormal=true`인 이상 이벤트를 선별하여 **AGV 출발 요청을 자동 등록**
- **1초 주기의 AGV 배차 스케줄러**를 구성하고, **ShedLock**을 적용하여 여러 서버에서 동일 작업이 중복 실행되지 않도록 제어
- AGV 배차 시 상태를 **선점 잠금 방식으로 갱신**하여 동일한 AGV가 여러 작업에 중복 배정되는 문제를 방지
- 사용 가능한 AGV가 없으면 배차 요청을 **Redis 기반 FIFO 대기열**에 저장하고, AGV가 확보되면 대기 순서에 따라 작업을 다시 배정
- AGV의 이동 과정을 **4단계 상태 머신**으로 관리하여 운반 상태를 실시간으로 전이하고, 장애 발생 시 상태를 자동 복구하도록 구성
- AGV의 위치와 운반 상태를 **WebSocket/STOMP의 `/topic/agv` 채널**을 통해 대시보드로 실시간 전송
- **React와 Three.js**를 활용해 공정별 AGV 이동 경로와 상태를 3D로 시각화하여 관제 화면에서 운반 현황을 즉시 확인할 수 있도록 구성


&nbsp;
## ⚙️ System Flow & Core Technologies

### 서비스 흐름도
<img width="10268" height="6806" alt="Group 97 (2)" src="https://github.com/user-attachments/assets/38b3852e-07f1-4505-8b40-5d3cf4d65a91" />

&nbsp;
### 데이터 흐름도
<img width="10217" height="5316" alt="데이터 기능 흐름도" src="https://github.com/user-attachments/assets/f329c398-0e11-4e21-b1c4-b83d46aaf211" />


&nbsp;
### Kafka
| Kafka Topic                      | Message Key     | Consumer Group                      | Consumer                        | 주요 처리 내용                                              |
| -------------------------------- | --------------- | ----------------------------------- | ------------------------------- | ----------------------------------------------------------- |
| `factory.manufacturing.raw`      | `carId`         | `manufacturing-consumer-group`      | `Assembly Service`              | 프레스·차체·도장·의장 공정 이벤트를 Rule 기반으로 분석      |
| `factory.manufacturing.raw`      | `carId`         | `ai-consumer-group`                 | `AI Service`                    | 생산 지표·병목 분석 및 ML 기반 불량 탐지·타 공정 전이 예측   |
| `factory.manufacturing.analysis` | `carId`         | `analysis-result-consumer-group`    | `AnalysisResultService`         | 공정별 분석 결과를 분류하여 Main DB에 저장                  |
| `factory.manufacturing.analysis` | `carId`         | `ai-analysis-consumer-group`        | `AI Service`                    | 병목·불량 탐지·전이 예측 결과와 주요 예측 근거를 저장        |
| `factory.manufacturing.analysis` | `carId`         | `ai-analysis-sync-consumer-group`   | `ES Sync Service`               | 제조 및 AI 분석 결과를 Elasticsearch에 동기화              |
| `factory.manufacturing.analysis` | `carId`         | `agv-dispatch-consumer-group`       | `ManufacturingAnalysisConsumer` | 이상 공정 이벤트를 선별하여 AGV 배차 및 공정 흐름을 처리     |
| `factory.equipment.status`       | `equipmentCode` | `dashboard-consumer-group`          | `EquipmentStateService`         | 설비의 현재 상태와 상태 변경 이력을 DB에 저장               |
| `factory.equipment.status`       | `equipmentCode` | `alert-analysis-consumer-group`     | `ManufacturingKafkaProducer`    | 설비 상태를 분석하고 이상 발생 시 알림 이벤트를 발행         |
| `factory.manufacturing.alert`    | `carId`         | `alert-notification-consumer-group` | `AlertEventService`             | 알림 정보를 저장하고 처리 상태를 관리                       |
| `factory.manufacturing.alert`    | `carId`         | `dashboard-alert-consumer-group`    | `DashboardAlertService`         | 관제 대시보드에 표시할 알림 데이터를 조회·가공              |
| `factory.manufacturing.alert`    | `carId`         | `websocket-alert-consumer-group`    | `WebSocketAlertService`         | 알림을 WebSocket을 통해 관제 대시보드에 실시간 전송          |
| `quality.inspection.sample`      | `inspection_no` | `quality-sample-consumer-group`     | `QualityKafkaProducer`          | 품질 검사 원천 데이터를 수신하여 분석용 이벤트로 변환·발행   |
| `quality.inspection.main`        | `inspection_no` | `quality-main-consumer-group`       | `RepositoryService`             | 품질 분석 데이터를 DataFrame으로 변환하여 Main DB에 저장     |


- Kafka를 통해 비동기 이벤트 처리를 적용하여 서비스 간 의존도를 낮추고, 일부 서비스 장애 상황에서도 이벤트를 안정적으로 전달
- MSA 환경에서 서비스의 **독립성·확장성·장애 격리**를 확보할 수 있는 이벤트 중심 아키텍처를 구축
- 제조 이벤트를 **Kafka Topic에 한 번 발행**하고, 각 서비스가 필요한 이벤트를 독립적으로 구독하여 처리하도록 구성
- 기존 서비스 간 직접 연결 방식에서 발생하던 **강한 결합과 변경 영향 범위 확대 문제**를 Kafka 기반 이벤트 스트리밍으로 개선
- 서비스별로 **Kafka Topic과 Consumer Group**을 분리하여 동일 이벤트를 각 서비스의 목적에 맞게 독립적으로 처리
- 신규 분석 기능이나 서비스 추가 시 기존 서비스의 직접적인 수정 없이 **Consumer를 추가하여 유연하게 확장**

&nbsp;
### Elastic Search
<img width="1575" height="515" alt="ES" src="https://github.com/user-attachments/assets/f082ee9c-ed12-4ce8-895a-6688de31c8c1" />

| 인덱스 구분 | 설정값 | 주요 역할 |
| --- | --- | --- |
| Bottleneck Index | `settings.elasticsearch_bottleneck_index` | 공정별 병목 분석 결과를 저장하고 검색·조회 |
| Defect Transfer Index | `settings.elasticsearch_defect_transfer_index` | 불량 전이 예측 결과와 주요 원인 분석 데이터를 저장하고 검색·조회 |

- Kafka를 통해 수신한 제조 이벤트와 공정 분석 결과를 **Elasticsearch에 실시간으로 인덱싱**하여 대용량 데이터를 저장
- 불량 탐지 결과, 공정 병목 정보, 설비 상태 및 위험도 분석 결과를 **인덱스별로 분리**하여 효율적으로 관리
- 차량 ID, 공정 코드, 설비 정보, 분석 유형, 위험도 등 **다양한 조건을 조합한 고속 검색·조회 기능**을 제공
- **Kibana 대시보드**를 통해 Elasticsearch에 저장된 분석 결과를 그래프 및 로그 형태로 시각화
- Kafka와 Elasticsearch를 연계하여 데이터 수집부터 검색·분석·대시보드 시각화까지 이어지는 **실시간 제조 데이터 분석 환경**을 구축

&nbsp;
### WebSocket
<img width="1899" height="855" alt="스크린샷(22)" src="https://github.com/user-attachments/assets/853b6375-7d8c-42c5-8360-fedfa2fa90de" />

- 이상 이벤트가 발생하면 분석 결과와 알림 정보를 **WebSocket/STOMP**를 통해 관제 대시보드로 실시간 전송
- 알림 우선순위, 위험도, 공정·설비 정보 및 발생 시각을 **`/topic/alerts` 채널**로 전달하여 즉시 화면에 반영
- AGV의 현재 위치, 운반 상태 및 이동 경로 정보를 **`/topic/agv` 채널**로 실시간 전송
- AGV의 출발·이동·도착 등 상태 변화를 대시보드에 즉시 반영하여 공정별 운반 현황을 실시간으로 관제

&nbsp;
## 🚀 Infrastructure & Deployment
<img width="841" height="911" alt="AIMS drawio (1)" src="https://github.com/user-attachments/assets/ff277345-18e7-4fe9-9c1f-a937a7d3cde6" />

&nbsp;
### AWS 네트워크 및 인프라 구성

- **Route 53**을 통해 서비스 도메인 요청을 처리하고, **ACM 인증서**를 적용하여 HTTPS 기반의 안전한 통신 환경을 구성
- **Public Subnet**에는 외부 요청을 수신하는 **ALB**와 Private Subnet의 외부 통신을 지원하는 **NAT Gateway**를 배치
- **ALB Ingress Controller**를 통해 외부 요청을 서비스별 경로에 따라 EKS 내부 애플리케이션으로 라우팅
- **Private Subnet**에는 EKS 애플리케이션, Amazon MSK, RDS MySQL, ElastiCache Redis 및 OpenSearch를 배치하여 외부 접근을 제한
- 애플리케이션과 데이터 저장소를 내부 네트워크에서만 통신하도록 분리하여 **공격 표면을 최소화하고 데이터 보안을 강화**

&nbsp;
### EKS 기반 MSA 운영

<img width="1896" height="862" alt="EKS 기반 MSA 운영 구조" src="https://github.com/user-attachments/assets/25c3a7e8-6816-42c4-a303-addf7af0a444" />

- Frontend, Backend, Assembly Service, Quality Service, AI Service를 각각 독립적인 컨테이너 서비스로 구성
- 각 서비스의 애플리케이션을 **Docker Image**로 빌드하고, **Amazon ECR**에서 이미지와 버전을 관리
- 서비스를 Kubernetes의 **Deployment와 Service 단위**로 배포하여 기능별 독립적인 운영과 확장이 가능하도록 구성
- **AWS Load Balancer Controller와 Ingress**를 적용하여 `Route 53 → ALB → Ingress → Service → Pod` 순서로 요청을 전달하고, 경로에 따라 각 MSA 서비스로 라우팅
- 특정 서비스의 장애나 트래픽 증가 시 해당 서비스의 Pod만 개별적으로 복구·확장하여 다른 서비스에 미치는 영향을 최소화

&nbsp;
### 실시간 데이터 수집 및 저장

- **Amazon MSK**를 통해 제조 이벤트와 분석 결과를 실시간으로 수집하고, 각 서비스가 Kafka 이벤트를 독립적으로 구독하여 처리
- **RDS MySQL**의 SampleDB와 MainDB를 분리하여 원천 제조 데이터와 서비스 운영 데이터를 목적에 따라 저장
- **ElastiCache Redis**를 활용하여 세션, 실시간 상태 및 반복 조회 데이터를 캐싱하고 데이터 조회 부하를 감소
- **OpenSearch**에 제조 이벤트와 분석 결과를 저장하여 공정·설비·위험도 등 다양한 조건의 빠른 검색과 분석을 지원

&nbsp;
### 보안 정보 관리

- 데이터베이스 계정, API Key 등 민감한 설정값을 **AWS Systems Manager Parameter Store**에서 중앙 관리
- External Secrets Operator(ESO)가 Parameter Store의 값을 조회하여 Kubernetes Secret으로 자동 동기화
- 애플리케이션은 Kubernetes Secret을 통해 필요한 설정값을 주입받아, 중요 정보가 소스 코드나 배포 파일에 직접 노출되지 않도록 구성

&nbsp;
### GitOps 기반 CI/CD

- 개발자가 GitHub Repository에 코드를 Push하면 **GitHub Actions**가 애플리케이션 테스트와 빌드를 자동으로 수행
- 빌드가 완료되면 Docker Image를 생성하여 **Amazon ECR**에 저장하고 이미지 태그를 통해 버전을 관리
- 신규 이미지 버전에 맞게 Kubernetes Manifest의 이미지 태그를 자동으로 갱신
- **Argo CD**가 Infra Repository의 변경 사항을 감지하고, 선언된 Manifest와 실제 EKS 클러스터 상태를 비교하여 자동 동기화
- 애플리케이션 코드와 배포 설정을 분리하고 모든 변경 이력을 Git으로 관리하여 **추적 가능성, 운영 일관성 및 롤백 편의성**을 확보

&nbsp;
### 무중단 배포

- **Kubernetes Rolling Update** 방식을 적용하여 기존 Pod를 유지한 상태에서 신규 버전의 Pod를 순차적으로 생성
- 신규 Pod가 **Readiness Probe**를 통과한 경우에만 서비스 트래픽을 전달하여 준비되지 않은 Pod로 요청이 유입되는 상황을 방지
- 정상적으로 실행 중인 신규 Pod로 트래픽을 점진적으로 전환한 뒤 기존 Pod를 종료하여 배포 중 서비스 중단을 최소화
- 배포 과정에서 문제가 발생하면 이전 ReplicaSet으로 빠르게 롤백하여 안정적인 서비스 운영이 가능하도록 구성
- 서비스별 독립 배포 구조를 통해 특정 기능의 변경이나 장애가 전체 시스템으로 확산되는 것을 최소화


&nbsp;
## 🔧 Tech Stack

### Backend
![Java](https://img.shields.io/badge/Java-007396?style=flat-square&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-6DB33F?style=flat-square&logo=springboot&logoColor=white)
![REST API](https://img.shields.io/badge/REST_API-000000?style=flat-square)
![WebSocket](https://img.shields.io/badge/WebSocket-010101?style=flat-square)


### Frontend
![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=nodedotjs&logoColor=white)
![React](https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=black)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-646CFF?style=flat-square&logo=vite&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white)

### AI
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikitlearn&logoColor=white)
![LightGBM](https://img.shields.io/badge/LightGBM-02569B?style=flat-square)
![OpenAI](https://img.shields.io/badge/OpenAI_RAG-412991?style=flat-square&logo=openai&logoColor=white)


### Database

![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white)


### Infrastructure

#### Container & Orchestration
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=flat-square&logo=kubernetes&logoColor=white)
![Amazon EKS](https://img.shields.io/badge/Amazon_EKS-FF9900?style=flat-square&logo=amazoneks&logoColor=white)
![Amazon ECR](https://img.shields.io/badge/Amazon_ECR-FF9900?style=flat-square&logo=amazonaws&logoColor=white)
![Amazon EC2](https://img.shields.io/badge/Amazon_EC2-FF9900?style=flat-square&logo=amazonec2&logoColor=white)

#### Event Streaming & Cache
![Apache Kafka](https://img.shields.io/badge/Apache_Kafka-231F20?style=flat-square&logo=apachekafka&logoColor=white)
![Amazon MSK](https://img.shields.io/badge/Amazon_MSK-FF9900?style=flat-square&logo=amazonaws&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white)
![Amazon ElastiCache](https://img.shields.io/badge/Amazon_ElastiCache-C925D1?style=flat-square&logo=amazonaws&logoColor=white)

#### Database & Search
![Amazon RDS](https://img.shields.io/badge/Amazon_RDS-527FFF?style=flat-square&logo=amazonrds&logoColor=white)
![Elasticsearch](https://img.shields.io/badge/Elasticsearch-005571?style=flat-square&logo=elasticsearch&logoColor=white)
![OpenSearch](https://img.shields.io/badge/OpenSearch-005EB8?style=flat-square&logo=opensearch&logoColor=white)

#### Network
![Amazon VPC](https://img.shields.io/badge/Amazon_VPC-8C4FFF?style=flat-square&logo=amazonaws&logoColor=white)
![Application Load Balancer](https://img.shields.io/badge/ALB-FF9900?style=flat-square&logo=awselasticloadbalancing&logoColor=white)
![Route 53](https://img.shields.io/badge/Route_53-8C4FFF?style=flat-square&logo=amazonroute53&logoColor=white)
![Nginx Ingress](https://img.shields.io/badge/Nginx_Ingress-009639?style=flat-square&logo=nginx&logoColor=white)

#### Infrastructure as Code & CI/CD
![Terraform](https://img.shields.io/badge/Terraform-844FBA?style=flat-square&logo=terraform&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white)
![Argo CD](https://img.shields.io/badge/Argo_CD-EF7B4D?style=flat-square&logo=argo&logoColor=white)

#### Project Management
![Redmine](https://img.shields.io/badge/Redmine-B32024?style=flat-square&logo=redmine&logoColor=white)

&nbsp;
## 🔗 Repository

- [**Main Backend Repository**](https://github.com/SK-Rookies-AIMS/backend)
- [**Assembly Repository**](https://github.com/SK-Rookies-AIMS/assembly-service)
- [**Quality Repository**](https://github.com/SK-Rookies-AIMS/quality-service)
- [**AI Repository**](https://github.com/SK-Rookies-AIMS/ai-service)
- [**Frontend Repository**](https://github.com/SK-Rookies-AIMS/frontend)
- [**Infra Repository**](https://github.com/SK-Rookies-AIMS/infra)


&nbsp;
## 👤 Developers

| <a href="https://github.com/hyein0514" target="_blank"><img width="120" height="120" src="https://github.com/hyein0514.png" /></a> | <a href="https://github.com/kimgeon0802" target="_blank"><img width="120" height="120" src="https://github.com/kimgeon0802.png" /></a> | <a href="https://github.com/mmije0ng" target="_blank"><img width="120" height="120" src="https://github.com/mmije0ng.png" /></a> | <a href="https://github.com/qwer9679" target="_blank"><img width="120" height="120" src="https://github.com/qwer9679.png" /></a> | <a href="https://github.com/chani2104" target="_blank"><img width="120" height="120" src="https://github.com/chani2104.png" /></a> | <a href="https://github.com/sknm1106" target="_blank"><img width="120" height="120" src="https://github.com/sknm1106.png" /></a> |
|:-------------:|:------:|:------:|:------:|:------:|:------:|
| [최혜인(팀장)](https://github.com/hyein0514) | [김건](https://github.com/kimgeon0802) | [박미정](https://github.com/mmije0ng) | [이준호](https://github.com/qwer9679) | [임종찬](https://github.com/chani2104) | [하서경](https://github.com/sknm1106) |

