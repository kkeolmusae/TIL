# 138. AWS ECS를 사용한 배포: 관리형 Docker 컨테이너 서비스

ECS는 4가지 범주: 클러스터, 컨테이너, 태스크, 서비스

## Container Edit: docker run 을 실행하는 방법을 정의하는 부분

`docker run -d --rm -p 80:80 harry/node-example-1`

이미지에 docker hub의 저장소 이름을 넣으면 ECS가 자동으로 Docker Hub에서 이미지를 찾는다.

다른 컨테이너 레지스트리를 사용하는 경우 레지스트리 호스팅 도메인과 저장소 이름을 넣으면 된다.

개인 저장소인 경우 로그인 정보를 지정할 수 있다.

포트 매핑은 컨테이너 내부 포트는 항상 외부와 동일한 포트에 매핑하기 떄문에 `docker run` 처럼 외부/내부 두개 다 매핑할 필요가 없다. 

## 고급 컨테이너 구성 - 상태확인(Health Check)
AWS가 특정 명령을 실행하여 컨테이너가 성공적으로 실행 중인지 확인할 수 있도록 하는 AWS 관련 설정

## 고급 컨테이너 구성 - 환경(Environment)
예를 들어 컨테이너가 시작될 때, 이 컨테이너에 대해 실행되어야 하는 디폴트 entry point 또는 명령을 오버라이드 할 수 있는 곳

e.g. utility container 에서 사용했던 거 비슷한거

환경 변수(Environment variables) 는 `docker run --env` 에 들어갔던 키-값을 정의하는 곳

## 고급 컨테이너 구성 - Storage And Logging
`docker run -v` 옵션과 동일하게 마운트 지점과 볼륨을 정의할 수 있다.

## 고급 컨테이너 구성 - Log configuration
CloudWatch라는 AWS 서비스를 자동으로 사용하여 컨테이너에서 생성된 로그를 관리하고 저장할 수 있다.


## Task definition

태스크는 애플리케이션의 블루프린트. AWS에 컨테이너를 시작하는 방법을 알릴 수 있다. (`docker run` 을 실행하는 방법이 아니라 이를 실행하는 서버를 구성하는 방법)

## Task definition - Compatibilities
FARGATE: 컨테이너를 시작하는 특정 방법으로 서버리스 라고 부르는 모드에서 구동된다. AWS는 실제로 컨테이너를 실행하는 EC2 인스턴스를 생성하지 않고 대신 컨테이너와 그 실행 설정을 저장한다. 그리고 컨테이너가 무언가를 하도록하는 요청이 있을 때마다 컨테이너를 시작하고, 그 요청을 처리한 다음, 다시 중지 시킨다. (FARGATE를 EC2로 전환하여 AWS에 EC2 인스턴스를 생성하도록 하는 것도 가능하다.)

# Service
구성된 애플리케이션과 그를 포함하는 컨테이너를 실행하는 방법을 컨트롤한다. 예를들어 여기에 로드밸런드를 추가할 수 있다.

수신 요청을 리디렉션하고, 대기열을 쌓고, 컨테이너를 실행하는 등 백그라운드에서 모든것을 관리한다. 

# Cluster
서비스가 실행되는 전체 네트워크.