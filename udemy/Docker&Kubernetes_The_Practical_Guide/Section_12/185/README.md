# 185. "Deployment" 객체 (리소스)

일반적으로 수동으로 pod을 생성하여 특정 워커 노드로 이동하지는 않는다.

보통 deployment 객체를 생성하고, 생성하고 관리해야하는 pod의 수와 컨테이너 수에 대한 지침을 제공한다.

- 하나 이상의 pod을 제어한다.
- 원하는 상태를 설정할 수 있고 설정에 따라 k8s가 실제 상태를 변경한다.
- 실행할 pod 및 컨테이너와 인스턴스 수를 정의할 수 있다.
- deployments는 멈출 수 있고, 삭제할 수 있으며 롤백도 된다.
- 스케일링 될 수 있다. 더 많은 pod 혹은 더 적은 pod을 가지고 싶다고 k8s에 알릴 수 있다. 
- 특정 메트릭을 설정할 수 있는 오토 스케일링 기능이 있다. (수신 트래픽이나 CPU 사용률 등)