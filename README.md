# 📚TIL : Infra/cloud
- 인프라, 클라우드 공부 기록
- 1차 목표 : CKA 자격증 취득 (2024년 2월 이내)

## 📝내용 정리
### CKA 
[2. Core Concepts](https://mint-thread-249.notion.site/2-Core-Concepts-8ef6239295794cac8f5255c0b26693f3?pvs=4)<br>
[3. Scheduling](https://mint-thread-249.notion.site/3-Scheduling-3fe273e950bf4a8aa6fb234425ed2237?pvs=4)<br>
[4. Logging & Monitoring](https://mint-thread-249.notion.site/4-Logging-Monitoring-fc311e46c42d418ab162622f88b50593?pvs=4) <br>
[5. Application Lifecycle Management](https://mint-thread-249.notion.site/5-Application-Lifecycle-Management-7339342bfe764326a903d4e8bdc27f8c?pvs=4)

## 🖊️기록
|날짜|학습 내용|
|---|---|
|240104|[[리뷰] Replicaset VS Deployment 차이](https://github.com/jjhh0210/TIL_infra-cloud/blob/main/k8s/CoreConcepts/Replicaset%20VS%20Deployment.md)<br>[[리뷰] Namespace](https://github.com/jjhh0210/TIL_infra-cloud/blob/main/k8s/CoreConcepts/Namespace.md)<br>[[리뷰] Imperative VS Declarative](https://github.com/jjhh0210/TIL_infra-cloud/blob/main/k8s/CoreConcepts/k8s%EC%97%90%EC%84%9C%20imperative%20VS%20Declarative.md)|
|240105|**<Section 3 - Scheduling>** <br>- 스케쥴링 기본 및 수동 스케쥴링하기<br>- Labels, Selector, Annotation|
|240108|**특정 노드로의 파드 스케쥴링 제어하기** <br>- Taints & Tolerations<br>- Node Selector , Node Affinity <br> - Taints&Tolerations VS Node Affinity 차이|
|240109|**리소스 할당 및 사용량 제어하기** <br>- Resource Requirements and Limits<br>- Demonsets <br>- Static Pods |
|240111|- Multiple Schedulers|
|240116|- 스케쥴링 실습<br>**<Seciton 4 - Logging and Monitoring>**<br>- Metrics Server로 클러스터 자원 사용량 모니터링<br>- 로그 확인하기|
|240122|- Nodeport, ClusterIP, LoadBalancer 서비스 및 kube-proxy 복습<br> **<Seciton 5 - Application Lifecycle Management>**<br>- Strategy in Deployments(롤링 업데이트, Recreate)|
|240123|- 컨테이너 시작 명령어 설정법<br> - 파드 시작 명령어 & 인자 설정<br>- 환경변수 설정|
|240124|- 설정데이터 다루는법 1) ConfigMap<br> - 설정데이터 다루는법 2) Secrets<br>- Encrypting Secret data at rest (암호화)|
|240126|- 다중 컨테이너 파드, 로깅 구현<br> - InitContainers|
|240127|**<Seciton 6 - Cluster Maintenance>**<br>- OS Upgrade (노드 offline동안의 대처법)|
|240130|- 쿠버네티스 releases and versions<br>- cluster upgrade 프로세스<br>- kubeadm 클러스터 업그레이드 실습|
|240202|- ETCD Backup & Restore|
|240203|**<Seciton 7 - Security>**<br>- 보안 기초 <br>- Authentication<br>- TLS basics  |
|240207|- TLS in k8s <br> - client/server 인증서 생성|


## 🔗관련 강의 및 자료
### CKA
- [강의 정보](https://www.udemy.com/course/certified-kubernetes-administrator-with-practice-tests/) <br>
- [시험 등록](https://trainingportal.linuxfoundation.org/learn/dashboard/) <br>
- [시험 정보](https://velog.io/@jkseo50/Kubernetes-CKA-Certified-Kubernetes-Administrator-취득-후기) <br>
- [K8S 공식 사이트](https://kubernetes.io/ko/)