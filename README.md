# sigma-elastalert-Rules
이 리포지토리는 Elasticsearch에 저장된 OCSF 로그의 공격을 탐지하기 위한 Sigma Rules과 Elastalert Rules의 정보를 담고 있습니다.
> 해당 리포지토리의 Sigma Rules과 Elastalert Rules은 [ELK](https://github.com/OCSF-Logrrr/ELK) 내부에 포함되어 동작합니다.

# 목차

# 아키텍처 구조
<img width="685" alt="스크린샷 2025-06-25 오후 6 34 30" src="https://github.com/user-attachments/assets/ef11e66b-1511-4b12-acb6-eb373c40215a" />

1. Logstash에서 OCSF 포맷으로 변환된 로그를 가져오면 Elasticsearch에 저장되고 Kibana로 시각화합니다.
2. 이 때 Elastalert는 Elasticsearch에 저장된 로그를 주기적으로 검사합니다. (ElastAlert는 Sigma Rules를 ElastAlert Rules 포맷으로 변환된 Rules을 사용)
4. Rules에 따라 탐지된 공격은 Slack으로 전송됩니다.

# 디렉토리 구조
```bash
.
├── logstash/
│   └── pipeline/
│       └── logstash.conf
├── sigma/
│	└── rules/            #sigma rules 저장소
├── elastalert/
│	├── config.yml        #elastalert 설정 파일
│	└── rules/            #elastalert rules 저장소
├── docker-compose.yml
├── convert_sigma.sh        #sigma rules -> elastalert rules 변환 스크립트
└── .env
```
