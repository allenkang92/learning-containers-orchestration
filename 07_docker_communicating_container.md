# 07_통신 가능 컨테이너 생성

이번에는 호스트와 통신이 가능한 컨테이너를 생성하고 실행하는 방법을 알아보겠습니다. `docker run` 명령어의 포트 포워딩 기능을 사용하여 컨테이너 내부의 서비스에 접근할 수 있도록 설정합니다.

## 1. Nginx 컨테이너 실행 및 포트 포워딩

다음 명령어를 사용하여 `my_nginx`라는 이름의 Nginx 컨테이너를 백그라운드에서 실행하고, 호스트의 8080 포트를 컨테이너의 80 포트에 연결합니다.

```bash
docker run --name my_nginx -d -p 8080:80 nginx
옵션 설명:

--name my_nginx: 생성될 컨테이너의 이름을 my_nginx로 지정합니다.

-d: 컨테이너를 백그라운드 모드로 실행합니다.

-p 8080:80: 호스트 머신의 8080 포트를 컨테이너의 80 포트로 포워딩합니다. 이를 통해 호스트의 8080 포트로 접속하면 컨테이너 내부에서 실행 중인 Nginx 웹 서버에 접근할 수 있게 됩니다.

nginx: 사용할 이미지 이름입니다. 별도의 버전 지시가 없으므로 최신 버전(latest)이 사용됩니다.

2. 컨테이너 실행 상태 확인
docker ps 명령어를 사용하여 my_nginx 컨테이너가 정상적으로 실행 중인지 확인합니다.

docker ps

STATUS 항목의 값이 Up으로 표시되면 컨테이너가 현재 실행 중임을 의미합니다. 또한 PORTS 항목에서 호스트와 컨테이너의 포트 매핑 정보를 확인할 수 있습니다.

3. 웹 브라우저를 통한 접근 확인
웹 브라우저를 열고 http://localhost:8080/ 주소로 접속합니다. Nginx가 정상적으로 실행 중이라면 Nginx의 기본 시작 페이지가 브라우저에 표시됩니다. 이는 호스트의 8080 포트로의 요청이 컨테이너의 80 포트로 성공적으로 전달되었음을 의미합니다.

4. 컨테이너 정지
생성한 my_nginx 컨테이너를 정지합니다.

docker stop my_nginx

docker stop 명령어는 지정된 컨테이너를 안전하게 종료합니다.

5. 컨테이너 삭제
정지된 my_nginx 컨테이너를 삭제합니다. docker container rm 또는 docker rm 명령어를 사용할 수 있습니다.

docker container rm my_nginx또는

docker rm my_nginx

6. 컨테이너 삭제 확인
docker ps -a 명령어를 사용하여 my_nginx 컨테이너가 성공적으로 삭제되었는지 확인합니다.

docker ps -a
삭제된 컨테이너는 목록에 표시되지 않습니다.