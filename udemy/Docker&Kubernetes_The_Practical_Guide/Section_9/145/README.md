# 145. ECS로 EFS 볼륨 사용하기

태스크가 실행되고 있는 한 데이터는 영구적이다. 하지만 새 컨테이너 이미지를 사용하려고 하면 서비스를 업데이트할 때 태스크가 종료되고 재시작되면 모든 데이터가 손실된다. 

로컬에서 `볼륨`을 사용하여 데이터를 보존했다면, ECS에서는 `EFS(Elastic File System)`을 사용하여 데이터를 보존한다.

보안 그룹과 인바운드 규칙없이 ECS의 컨테이너와 태스크는 EFS와 통신할 수 없기때문에 새로운 보안 그룹을 만들어야 한다.