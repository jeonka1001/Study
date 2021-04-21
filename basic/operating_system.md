# 면접준비 - OS
> 나만의 언어로 준비하는 면접준비

## 목록
- [프로세스 vs 스레드](#프로세스-vs-스레드)
- [교착상태 vs 기아상태](#교착상태-vs-기아상태)

---

## 프로세스 vs 스레드

## 교착상태 vs 기아상태
#### 교착상태
- 여러 프로세스가 자신의 리소스를 보유한 상태에서 다른 프로세스의 리소스를 요청할 때 생가는 현상 ( 모든 프로세스가 순환 방식으로 리소스를 기다리는 경우 )
###### 발생 조건
- 상호배제 : 한 자원에 한 작업만 할당 가능
- 잠금 및 대기 : 자원을 할당받은 작업이 다른 자원을 대기중인 경우
- 선점 불가 : 하나의 작업이 다른 작업의 자원을 빼앗지 못함.
- 순환 대기 : 연쇄적으로 작업이 자원을 대기하는 것
###### 해결 방안
> 이 의 4가지 조건을 피해야 한다.
- 한 자원에 여러 작업 할당 : 공유 자원
- 자원 대기 시 현재 할당한 자원을 해제한 후 대기한다.
- 자원 요청 시 우선순위가 낮은 작업의 경우 자원을 해제 후 기다린다.
- 자원에 번호를 할당하여 순차적으로 진행

#### 기아상태
- 프로세스가 자원을 요청하는 경우 우선순위가 높게 할당된 프로세스가 우선적으로 자원을 할당받는다. 이 경우 우선순위가 낮은 프로세스의 경우 무제한적으로 자원 할당을 대기하는 현상