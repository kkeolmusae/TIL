# 180. Kubernetes는 인프라를 관리하지 않습니다.

쿠버네티스는 pod의 모니터링, pod 컨테이너 모니터링, 실패한 pod 교체 및 스케일링 등 pod을 관리하는데 도움을 준다. pod 내부에 있는 이러한 컨테이너들을 오케스트레이션하고 워커 노드간에 컨테이너를 이동하는 등 배포된 애플리케이션을 관리하는 역할을 한다.

이외에 인스턴스 생성과 인스턴스 관리 및 sw 설치는 직접해야 한다. 이러한 작업들을 도와주는 것들로 ECS나 EKS 등이 있다.

EKS(Elastic Kubernetes Service)는 k8s 구성으로 필요한 모든 리소스 또한 설정한다.