---
title: SSL/TLS, 인증서
tags:
    - infrastructure
    - network
---
출처
https://www.cloudflare.com/learning/ssl/what-is-ssl/
https://www.cloudflare.com/learning/ssl/what-is-an-ssl-certificate/
https://engineering.linecorp.com/ko/blog/best-practices-to-secure-your-ssl-tls/

## SSL/TLS란?
    - SSL(Secure Socket Layer)은 암호 기반의 인터넷 보안 프로토콜이다.
    - 여러 번의 보완이 있었으며, 넷스케이프와 무관한 IETF가 이를 관리하면서 TLS(Transport Layer Security)로 이름이 변경되었다.
    - 현재 SSL은 업데이트가 중단되어 많은 보안 취약점이 있고, 대다수의 웹 브라우저는 SSL을 지원하지 않는다.
    - 따라서 대부분의 경우, 엄밀하게 말하자면 TLS라 표기하는 것이 맞지만, SSL이 TLS를 지칭하는 용어로 자주 혼용된다.

## SSL/TLS의 기능
    - Encryption: 웹 상에서 전송되는 데이터를 암호화하여, 전송 중인 데이터를 탈취하여도 의미없게 만든다.
    - Authentication: Handshake라는 두 기기 간 인증 절차를 거침으로서 서로가 서로임을 보장해준다.
    - Integrity: 디지털 서명을 통해 데이터 무결성, 즉 데이터가 변조되지 않았음을 검증한다.

## SSL certificate(TLS certificate)란?
    - 웹사이트의 서버 또는 앱 서버에 저장되어 웹사이트를 인증해주는 일종의 신분증이다.
    - 인증서에는 아래와 같은 정보가 포함되어 있다.
        - 도메인 네임
        - 발급받은 주체(개인, 단체, 기기)
        - 발급 주체(CA)
        - CA의 디지털 서명
        - 적용받는 서브도메인들
        - 발급 날짜
        - 만료 날짜
        - 퍼블릭 키
    - 인증서에는 웹사이트의 퍼블릭 키가 포함되어 사용자 디바이스는 이를 통해 웹사이트와 안전한 연결을 할 수 있도록 한다.
    - 웹사이트는 별도 관리하는 프라이빗 키로 사용자가 전달한 퍼블릭 키로 암호화된 데이터를 복호화한다.
    - CA(Certificate Authorities)는 SSL 인증서를 발급해주는 기관이다.

## SSL certificate의 종류
    - Single-domain: 하나의 도메인에만 적용되며, 서브 도메인에도 적용되지 않는다. 해당 도메인의 모든 페이지는 해당 인증서가 적용된다.
    - Wildcard: 하나의 도메인과 그 서브 도메인에도 전부 적용된다.
    - Multi-domain: 여러 개의 서로 무관한 도메인에 적용 가능하다.

## SSL certificate validation level
    - Domain Validation: 가장 낮은 수준의 검증이며, 비용도 가장 적다. 해당 도메인의 control여부만 증명하면 된다. 이는 보통 DNS 레코드나 이메일을 통해 검증한다. 
    - Organization Validation: CA가 직접 인증서를 발급받는 주체와 접촉하여 검증한다. 인증서에는 해당 단체의 이름과 주소 등이 포함된다.
    - Extended Validation: SSL 인증서 발급 전, 해당 환경과 단체에 관한 폭넓은 검증이 수행된다. 단체가 정말 존재하며 법적 문제 없이 등록되어있느지 등을 조사하며 이에 대한 시간과 비용이 발생한다.

## 

