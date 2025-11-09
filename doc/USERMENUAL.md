## 사용법

### 사전 세팅
1. 볼륨 위치 지정
- git 이라는 이름의 계정에 harbor 폴더 생성
- harbor/data 폴더 생성
- harbor/cert 폴더 생성

2. 인증서 생성
- openssl genrsa -out [IP].key 2048
- openssl req -new -key [IP].key -out [IP].csr -subj "/C=KR/ST=Seoul/L=Seoul/O=MyCompany/OU=IT/CN=[IP]"
- openssl x509 -req -days 3650 -in [IP].csr -signkey [IP].key -out [IP].crt

3. 설치 및 컨테이너 실행
- wget https://github.com/goharbor/harbor/releases/download/v2.9.0/harbor-online-installer-v2.9.0.tgz
- tar xvf harbor-online-installer-v2.9.0.tgz
- cd harbor
- cp harbor.yml.tmpl harbor.yml
- harbor.yml 수정
- ./prepare
- ./install.sh

### 참고
1. harbor.yml 수정
- hostname 수정
- port 설정
- certificate, private_key 경로 설정
- harbor_admin_password, db password 설정
- data_volume 데이터 볼륨 설정 (사전 세팅에서 생성했던 data 폴더 경로로)


