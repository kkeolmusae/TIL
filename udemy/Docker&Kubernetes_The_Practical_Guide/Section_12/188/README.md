# 188. "Service" 객체 (리소스)
Pod 과 Pod에서 실행되는 컨테이너에 접근하려면 service 가 필요하다.

service 객체는 k8s가 알고 있는 또 다른 객체이기에 클러스터의 다른 pod에 pod을 노출한다.

pod에는 디폴트로 내부 IP가 있는데 이 내부 IP에는 2가지 문제가 있다.
1. 클러스터 외부에서 pod에 액세스하는데 사용할 수 없다.
2. pod이 교체될 때 마다 IP가 변경된다.

service는 pod을 그룹화하고, 공유 주소와 공유 IP를 제공한다. 이 주소는 변경되지 않는다.

즉 service를 사용하여 여러 pod을 해당 service로 이동하고 그 service에서 변경할 수 없는 IP 주소에 연결할 수 있도록 할 수 있다. 그리고 클러스터 내부 뿐만 아니라 클러스터 외부에도 이 변경되지 않는 주소를 노출하도록 service 에 지시할 수 있다. 이로 인해 클러스터 외부에서 pod에 액세스할 수 있게 된다.

디폴트 값은 내부 전용이지만 service를 사용하면 덮어쓸 수 있다. 즉 service가 없으면 내부적으로 pod에 접근하기 매우 어렵다.