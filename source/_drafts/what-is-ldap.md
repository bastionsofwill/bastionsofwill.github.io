---
title: what-is-ldap
tags:
- network
- 
---

## LDAP이란?
- Lightweight Directory Access Protocol
- 네트워크 상 디렉토리 서비스 표준 X.500의 일부인 DAP의 경량화 버전

## 네트워크 상 디렉토리란?
네트워크 상 디렉토리는 사용자에게 네트워크 어디에 무엇이 위치하는지를 알려준다. 
DNS도 이런 디렉토리 시스템으로 볼 수 있으며, 도메인 네임을 기준으로 특정 네트워크 주소라는 데이터에 접근하도록 해준다.
하지만, 만약 사용자가 도메인 네임을 모르더라도 사용자는 LDAP을 통해 네트워크 상의 자원을 검색할 수 있다. 

## LDAP의 용도
LDAP은 주로 인증의 축(Central place)를 제공하는데 사용된다. 이는 사용자명과 패스워드를 저장하여, 다른 애플리케이션이나 서비스에서 플러그인 형태로 사용자를 검증하는데 사용될 수 있다는 뜻이다. LDAP SSO는 LDAP 데이터베이스 접근을 제어하는 데에도 사용될 수 있다.

## LDAP 디렉토리의 계층(Level)
LDAP 설정(configuration)은 아래 계층들로 구성된 트리 형태이다.
- root 디렉토리
- Countries
- Organizations
- Organizational units(Divisions, Departments, etc.)
- Individuals(사람, 파일, 공유 자원 등)



### 출처
https://searchmobilecomputing.techtarget.com/definition/LDAP