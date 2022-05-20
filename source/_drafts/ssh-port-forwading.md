---
title: SSH Port Forwarding이란?
tags:
---

## SSH Port Forwarding과 그 종류
- SSH Tunneling이라고도 부름
- 특정 포트를 *다른 연결에 연결하는* 행위 
- 프록시와 유사한 역할을 수행
- Local, Remote, Dynamic 포트 포워딩이 있음

### Local Port forwarding
로컬 포트 포워딩은 localhost의 특정 포트를 대상으로 하며, 아래와 같이 사용할 수 있다.
```bash
ssh -L <local port>:<remote server>:<remote port> <username>@<gateway server>
```
- \<local port\>: 클라이언트에서 사용하는 포트
- \<remote server\>: 접근하고자 하는 서버 주소
- \<remote port\>: \<remote server\>의 포트
- \<gateway server\>: Gateway(Bastion) 역할을 하는 서버

즉, 클라이언트 환경에서 위 명령을 실행한 후 `localhost:<local port>`로 접근하게 되면, 사용자는 자동으로 `<SSH server>`에 `<username>`으로 로그인하여 `<remote server>:<remote port>`에 접근하게 된다.

```bash
ssh -L 10030:localhost:8180 root@1.2.3.4
```
위와 같은 프로세스를 실행한 클라이언트에서 localhost:10030에 접근하게 되면 아래와 같은 절차를 수행하게 된다.
1. (클라이언트) `ssh root@1.2.3.4`로 1.2.3.4 서버 접속
2. (root@1.2.3.4) `localhost:8180`으로 8180 포트의 서비스에 접근

즉, 위 프로세스는 클라이언트 - localhost:\<local port\> 간 연결을 Gateway 서버 - \<remote server\>:\<remote port\> 간 연결로 연결해주는 프로세스이다. 
위 프로세스는 Gateway 서버 - Remote 서버 간 방화벽 설정과 불특정 다수 클라이언트 - Gateway 서버 간 방화벽 설정으로 클라이언트와 Remote 서버/포트 간의 직접적인 연결을 수행할 수 있다는 데에 의미가 있다.

### Remote Port Forwarding

### 출처
https://linux.systemv.pe.kr/ssh-%ED%8F%AC%ED%8A%B8-%ED%8F%AC%EC%9B%8C%EB%94%A9/
https://blog.naver.com/PostView.naver?blogId=alice_k106&logNo=221364560794
https://www.hanbit.co.kr/network/category/category_view.html?cms_code=CMS5064906327
https://unix.stackexchange.com/questions/115897/whats-ssh-port-forwarding-and-whats-the-difference-between-ssh-local-and-remot

