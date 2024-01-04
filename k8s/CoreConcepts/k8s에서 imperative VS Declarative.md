## Imperative
- **생성/업데이트/삭제 명령어 사용해서 object관리 ⇒ 변화 수행 전 상황을 일일히 체크해야하고, 예외나 오류 발생시 직접 해결해줘야 함 (ex. 이미 exist 오브젝트시 오류메세지 발생)**
    1. 명령어만 사용해서 Object관리(시험에선 유용)
        
        - 단점1: 기능 정의에 한계가 있고, 고급설정시 커맨드가 매우 복잡해질 수 있음
            - ex. creating a multi-container pod or deployment.
        - 단점2: 커맨드가 실행되고 나면 없어지기 때문에 커맨드 추적이 어려움 → 다른 사람이 어떻게 이 오브젝트를 생성했는지 알수가 없음 → 크고 복잡한 환경에서는 이는 좋지 x
    2. YAML파일+명령어 사용해서 관리
        - 업데이트시, edit 명령어시 나오는 정의서
            - edit했을 때 나오는 옵젝트 정의서는 **실제 파일이 X**, 쿠버네티스 메모리에 있는 파드 정의 파일임.
            - edit로 수정시, 실제 live 오브젝트에 바로 change가 반영됨. but 기록되지 않음. 따라서 로컬 정의 파일은 여전히 old한 버전일 수 있음.
                
                
        - 그래서 업데이트시 반드시 **edit → replace** 해서 로컬 파일에도 반영 필수(그러나, 여전히 이 과정들은 imperative함!!)
            
            
## Declarative
- **YAML config 파일에 업데이트 ⇒ apply 명령어 수행(ex. 이미 exist 오브젝트여도 오류 메세지 발생 x, 알아서 처리함)**
    - apply 사용하면→ 기존의 설정을 보고 시스템에 어떤 변화가 필요한지 알아냄. 어떻게 할지는 알아서
    - 해당 디렉토리 아래에 있는 모든 object 한번에 변화 수행하려면? 그 디렉토리 경로 지정

### `kubectl apply -f nginx.yaml` 실행 시 동작 과정 - 3가지 비교
⇒ local config 파일, last applied config, live object config

1. 기존에 있는 오브젝트인지 확인 후 없으면 오브젝트 생성 → 쿠버네티스 메모리 내에 live object configuration(실제 오브젝트의 설정)이 생성됨
   - 이거는 create나 run도 마찬가지긴 하다.
2. 우리가 작성한 local config 파일이 json 포맷으로 변경 됨 → 가장 최신 적용한 설정(Last applied Configuration)으로 저장됨 
3. 이후 , live object에 어떤 changes가 이뤄져야 하는지 확인하기 위해 3가지가 모두 비교됨

### ex1) 로컬 파일에서 image에 nginx:1.18 → 1.19로 버전 변경 후 apply 실행
1. 변경된 값에 대해 live object configuration ↔ local file 비교
2. 차이가 있으면, live object configuration이 새 값으로 업데이트 됨
3. 이후 last applied config가 업데이트 됨

### ex2) 로컬파일에서 type label 삭제 후 apply 실행
1. last applied config에는 type 레이블이 있으나, local 파일엔 없음을 확인 
2. 실제 live config에서 type 레이블을 지움

- 즉, lac는 어떤 필드가 로컬파일에서 삭제되었는지 알아내는데에 도움을 줌. 
  
### 주의 사항
사실은 lac는 안에 live config안에 annotation으로 있음. 이거는 apply 명령어 사용 시에만 생김!!! create나 replace 명령어 사용하면 live config에 lac 저장 안함!!!

⇒ **따라서, 쿠버네티스 오브젝트 관리시 imperative와 declarative접근을 섞어 사용하지 말 것!**