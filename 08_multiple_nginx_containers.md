# 08_다수의 Nginx 컨테이너 실행

이번에는 여러 개의 Nginx 컨테이너를 동시에 실행하는 방법을 알아봅니다. 핵심은 각 컨테이너가 호스트 머신의 서로 다른 포트에 연결되도록 설정하는 것입니다. 컨테이너 내부의 포트는 이미지를 만든 사람이 지정한 것이므로 일반적으로 변경할 수 없지만, 호스트의 포트는 자유롭게 설정할 수 있습니다.

## 1. 여러 Nginx 컨테이너 실행

다음 명령어를 사용하여 세 개의 Nginx 컨테이너를 실행합니다. 각 컨테이너는 고유한 호스트 포트에 매핑됩니다.

```bash
docker run --name my_nginx1 -d -p 8081:80 nginx
docker run --name my_nginx2 -d -p 8082:80 nginx
docker run --name my_nginx3 -d -p 8083:80 nginx

명령어 설명:

--name my_nginx1, --name my_nginx2, --name my_nginx3: 각 컨테이너의 이름을 지정합니다.

-d: 컨테이너를 백그라운드에서 실행합니다.

-p 8081:80, -p 8082:80, -p 8083:80: 호스트의 각기 다른 포트(8081, 8082, 8083)를 각 컨테이너의 80 포트에 매핑합니다. 컨테이너 내부의 Nginx는 80번 포트에서 동작하지만, 호스트에서는 다른 포트를 통해 접근해야 충돌을 피할 수 있습니다.

nginx: 사용할 이미지 이름입니다.

2. 컨테이너 실행 상태 확인
docker ps 명령어를 사용하여 세 개의 Nginx 컨테이너가 모두 정상적으로 실행 중인지 확인합니다.

docker ps

출력 결과에서 my_nginx1, my_nginx2, my_nginx3 컨테이너가 모두 STATUS가 Up으로 표시되어야 하며, PORTS 항목에서 각각 0.0.0.0:8081->80/tcp, 0.0.0.0:8082->80/tcp, 0.0.0.0:8083->80/tcp와 같이 호스트 포트와 컨테이너 포트가 올바르게 매핑되었는지 확인합니다.

3. 웹 브라우저를 통한 접근 확인
웹 브라우저를 열고 다음 주소로 각각 접속하여 Nginx의 기본 시작 페이지가 나타나는지 확인합니다.

http://localhost:8081/

http://localhost:8082/

http://localhost:8083/

각 주소에 접속했을 때 Nginx 시작 페이지가 정상적으로 표시되면 컨테이너들이 독립적으로 잘 실행되고 있으며, 포트 포워딩 설정도 올바르게 되었다는 것을 의미합니다.

4. 컨테이너 정지
실행 중인 세 개의 Nginx 컨테이너를 정지합니다.

docker stop my_nginx1
docker stop my_nginx2
docker stop my_nginx3

5. 컨테이너 삭제
정지된 세 개의 Nginx 컨테이너를 삭제합니다.

docker rm my_nginx1
docker rm my_nginx2
docker rm my_nginx3

6. 컨테이너 삭제 확인
docker ps -a 명령어를 사용하여 컨테이너들이 성공적으로 삭제되었는지 확인합니다.

docker ps -a

출력 결과에 my_nginx1, my_nginx2, my_nginx3 컨테이너가 나타나지 않으면 삭제가 완료된 것입니다.