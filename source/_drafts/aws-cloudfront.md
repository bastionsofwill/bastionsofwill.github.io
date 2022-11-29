---
title: aws_cloudfront
tags:
    - AWS
    - network
---
# AWS CloudFront
## 개요
CloudFront는 AWS에서 제공하는 CDN 서비스로, AWS를 사용한 웹 서비스를 구성할 때 매우 빈번하게 사용하는 서비스이다.
CDN이라는 서비스의 성질로 보면 매우 당연하지만, Region과 AZ에 종속되지 않는다는 점이 AWS를 통해 네트워크를 공부하는 내 입장에서 다른 AWS 서비스들과는 굉장히 이질적이라고 느껴졌다. 

AWS에서는 CF가 동작하는 기반을 Edge Location 또는 POP(Point of Presence)라고 부르며, 각 edge location에 사용자 지정 정책으로 origin으로부터 Caching을 수행하고, cache hit이 발생하면 대신 응답해주는 역할을 한다.
![[Cloudfront-Map_9.24_2x.2eeac6e52bf404816c6d0aac3edbeb7b6b87fdaa.png]]

## 구성 요소
- Distribution
	- Origin
		- Domain
		- Protocol(Custom Origin Only)
		- Path
		- Name
		- Custom header
		- Origin shield
		- Connection attempts
		- Connection timeout
		- Origin Access(Amazon S3 Origin Only)
	- Cache behavior
		- 각 distribution마다 Default cache behavior가 존재하며, path pattern에 따라 다른 cache behavior를 지정하여 사용한다.
		- origin이 여러 개일 경우, 어떤 요청을 어떤 origin으로 보낼지도 지정이 가능하다.
		- signed url 사용 가능
	
- Origin Access Control 

- Policy
	- Cache policy
		- cache key를 관리하는 정책
		- cache key란, 
	- Origin request policy
	- Response headers policy

### 출처
https://aws.amazon.com/cloudfront/features/?whats-new-cloudfront.sort-by=item.additionalFields.postDateTime&whats-new-cloudfront.sort-order=desc#Global_Edge_Network