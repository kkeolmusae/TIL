# 165. Docker Compose

`Docker Compose`는 긴 도커 명령어의 불편함을 해결하기 위해 만들어졌다. 특히 다중 컨테이너 환경에서 빠르게 많은 작업이 수행될 수 있게 도와준다.

Docker Compose를 사용하면 컨테이너 시작 구성 파일을 구성 파일에 넣을 수 있다. 구성 파일은 `docker-compose up` 을 실행할 때 자동으로 선택되어 전송되며, 구성파일에 정의된 모든 컨테이너를 시작하고 초기화 한다.

시작된 모든 컨테이너를 중지하고 싶다면 `docker-compose down` 명령으로 중지한다.