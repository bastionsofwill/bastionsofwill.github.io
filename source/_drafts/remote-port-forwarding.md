---
title: remote-port-forwarding
tags:
---



### Remote Port Forwarding
앞서 살펴본 Local port forwarding을 토대로 Remote port forwarding을 생각하면, Remote host의 특정 포트를 다른 연결로 forward할 것이라는 것을 짐작할 수 있다.

```bash
ssh -R <remote port>:<target server>:<target port> <username>@<remote server>
```
- \<remote port\>: \<remote server\>의 포트
- \<target server\>: 목적지 서버
- \<target port\>: \<target server\>의 포트
- \<remote server\>: SSH 터널이 시작되는 서버(SSH 서버)

즉, 클라이언트 환경에서 위와 같은 프로세스가 실행되면, `remote host:<remote port>`로 전달되는 요청은 `<local server>`에서 `<target server>:<target port>`에 보내지는 요청으로 처리된다.

![](/images/rfp_local.png)
이미지 출처: https://unix.stackexchange.com/questions/115897/whats-ssh-port-forwarding-and-whats-the-difference-between-ssh-local-and-remot

위 예시는 \<remotehost\>:123 으로의 요청을 \<yourhost\> --> \<localhost\>:456 으로 forward한다. 

![](/images/rfp_near.png)
이미지 출처: https://unix.stackexchange.com/questions/115897/whats-ssh-port-forwarding-and-whats-the-difference-between-ssh-local-and-remot

위 예시는 \<remotehost\>:123 으로의 요청을 \<yourhost> --> \<nearhost>:456 으로 forward한다.

Remote port forwarding는 Local port forwarding보다 직관적으로 이해하기 어렵다. ssh 커맨드가 실행되는 위치가 SSH 서버(remotehost)이기 때문이다. -R 옵션을 통해 \<remotehost\>:\<remoteport\>로 전달되는 요청을 포워딩하는 SSH 연결을 생성하게 되면, 사용자는 이후 아웃바운드가
### 출처