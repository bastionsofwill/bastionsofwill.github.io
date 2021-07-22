---
title: 이메일 발신자 인증
tags:
    - email
    - DNS
---
출처:
RFC 5782: DNS Blacklists and Whitelists
    - https://datatracker.ietf.org/doc/html/rfc5782

Wikipedia
    - https://en.wikipedia.org/wiki/Mail_Abuse_Prevention_System
    - https://en.wikipedia.org/wiki/Domain_Name_System-based_blackhole_list

KISA 불법스팸대응센터
    - http://spam.kisa.or.kr

SendGrid Document
    - https://docs.sendgrid.com/ui/account-and-settings/spf-records
    - https://docs.sendgrid.com/ui/account-and-settings/dkim-records

# DNSBL과 KISA-RBL
DNSBL(DNS-based blackhole list)은 DNS 쿼리를 통해 발송 IP 주소가 스팸 블랙리스트에 등재되어 있는지 확인할 수 있는 서비스이다. MAPS(Mail Abuse Preventation System)에서 만들고 관리하던 스팸 발송 이력이 있거나 수상한 IP의 리스트인 RBL(Real-time Blackhole List)에서 출발하였으며, DNS 기반의 DNSBL을 만들어 해당 도메인으로부터 발송되는 메일을 차단할 수 있도록 발전하였다. 이후 각자의 정책에 따라 여러 종류의 RBL이 만들어지면서 RBL과 DNSBL이라는 용어는 일반화되고 혼용되는 상황이다.
KISA-RBL은 KISA(한국인터넷진흥원)에서 무료로 관리/운영하는 실시간 스팸차단리스트이다. 국내외의 스팸 정보를 실시간으로 취합/분석하여 1시간마다 업데이트하며, 일 10만건 이하의 수신량이 발생하는 메일 서버에서 사용이 가능하다.

# SPF Records
SPF(Sender Policy Framework)는 이메일 발신 주소 변조를 방지하기 위한 표준으로, 메시지를 보낸 IP가 특정 도메인에서 이메일을 보낼 수 있는 권한을 가지고 있는지를 검증한다. 이를 위해 특정 TXT 레코드를 도메인의 DNS 레코드에 추가하여 어떤 IP가 해당 도메인으로 이메일을 보낼 수 있는 권리를 가지고 있는지를 표시한다.

# DKIM Records
http://www.dkim.org/
DKIM(DomainKeys Identified Mail)은 이메일 스푸핑을 방지하기 위한 인증 표준으로, 도메인 소유자의 DNS 레코드를 관리하는 권한을 기반으로 사용자를 인증한다. 메일을 발송 시, 발송 서버는 메시지에 private key로 서명하며, 도메인 소유자는 TXT 레코드의 변형인 DKIM 레코드를 발송 도메인의 DNS에 추가한다. 해당 TXT 레코드는 메일 발송 시 서명하는 private key를 검증할 수 있는 public key를 포함하고 있어 메일 수신자가 발신자를 검증하게 해준다.

만약 sender@example.com이라는 주소를 발신자로 메일을 보낸다고 가정한다면 아래와 같은 절차를 거치게 된다.
1. 이메일 발송 전에 발송 서버는 private key로 메시지에 서명한다.
2. 메시지가 전달되면, 수신 서버는 example.com 도메인의 DNS 레코드로부터 DKIM 레코드를 가져온다.
3. 수신 서버는 DKIM 레코드의 public key를 사용하여 메일의 서명을 검증한다.
4. 검증이 성공한다면 수신 서버는 해당 주소(return-path의 값)로부터 이메일이 전송되었으며, 변조되지 않았다고 판단한다.
5. 검증 실패 시, 해당 메시지는 이상이 있다고 분류된다.

DKIM 인증은 베스트 프랙티스이지만, 그 범위는 제한된다. 컨텐츠를 검증하지도, 메시지를 어떻게 처리할지에 대한 정보를 전달하지도 않으며 다만 이메일 전달에 있어 중요한 역할을 하는 발신자 인증에 도움을 줄 뿐이다.

# DMARC
https://dmarc.org/
DMARC(Domain-based Message Authentication, Reporting and Conformance)