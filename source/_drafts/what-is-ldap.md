---
title: freeIPA
tags:
- network
- LDAP
- authentication
---

## freeIPA
팀에서 사용하는 여러 서비스들의 계정을 통합 관리하기 위해, freeIPA라는 솔루션을 도입하였다. 기능은 강력한데 디자인적인 요소에 전혀 신경을 쓰지 않은 모습이 특히 마음에 든다. 
![](/images/freeipa_gui.png)

freeIPA는 여러 가지 기능을 제공하지만, 현재 내가 이해한 기능으로는 Host-based Access Control(HBAC)과 LDAP 기능의 제공이 있다. 이를 통해 우리 팀 구성원들은 여러 대의 서버의 계정을 통합하여 관리(HBAC)하고, GitLab/Jenkins와 같은 서비스도 동일한 인증 정보로 사용(LDAP)할 수 있다.

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