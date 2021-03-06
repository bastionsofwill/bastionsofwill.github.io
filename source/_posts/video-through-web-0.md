---
title: Adobe Flash와 ActiveX
tags:
  - web
  - history
date: 2021-10-05 19:48:36
---

## 웹 상에서의 사용자 경험에 대한 갈증 
웹을 통해 사용자에게 하이퍼텍스트 이상의 경험, 다시 말해 영상과 소리, 또는 게임 등의 상호작용이 가능한 컨텐츠를 전달하려면 어떻게 해야 할까? 클라이언트의 웹 브라우저는 HTTP 통신으로 정보를 주고받지만, 기존에 주고받던 데이터의 형태인 텍스트와 정적인 이미지에 비해 훨씬 많은 자원을 요구하는 이러한 컨텐츠를 웹을 통해 전달하고 경험하기 위해서는 특별한 고려가 필요하다. 이를 해결하기 위해 등장한 수많은 해답 중 하나인 RIA와 Browser Plugin 기술에 대해 알아보자.

## Rich Internet Application(RIA, RWA=Rich Web Appliction)
웹 상에서 사용자 경험을 향상시키기 위한 브라우저 확장 프로그램으로, 데스크탑 애플리케이션의 특징을 갖는 웹 애플리케이션이다. Adobe Flash의 전신인 Macromedia Flash MX로 만든 프로덕트를 설명하기 위한 개념으로 처음 소개되었으며, Java applet, 어도비 플래시, MS 실버라이트 등의 플러그인 기술로 개발한 웹 애플리케이션을 칭하는 개념으로 확장되었다. 
주로 브라우저의 멀티미디어/그래픽 성능을 보강하는 역할을 했지만, 브라우저, 운영체제 등 클라이언트의 환경에 따라 RIA 요소를 전부 따로 고려하여야 했기 때문에 크로스 브라우징을 지원할 때 심각한 장애 요소로 작용하여 현대의 웹에서는 퇴출되었다.

## NPAPI(Netscape Plugin API)와 ActiveX
NPAPI는 넷스케이프에서 개발한, 브라우저가 외부 애플리케이션(= RIA)을 브라우저에서 플러그인 형식으로 끌어다 쓰기 위한 API이다. 다시 말하면, 브라우저에서 동작하기 어려운 기능을 구현하기 위해 클라이언트 환경에 애플리케이션을 설치한 뒤, 이를 웹 페이지에서 접근하기 위해 사용하는 API이다.
이것이 대세가 되면서 플래시 등의 플러그인 기술들은 이를 기반으로 개발되고, MS는 이에 대응하기 위해 IE3에 NPAPI 지원 기능을 추가하면서도 한편으로는 윈도우 + IE 환경에서만 사용이 가능한 자체 플러그인 규격인 ActiveX를 만들었다.
이후 IE가 시장에서 지배적인 위치를 차지하면서 IE는 NPAPI 지원을 중단하였고, ActiveX는 웹 환경에서의 보다 다양한 경험 및 기능을 위한 표준이 되어버리나, 지나친 권한을 허용함으로서 사용자의 보안을 저해하고, 여러 플랫폼에서 호환이 되지 않는 등 여러 부작용을 가져온다.
이러한 심각한 문제점과 모바일 기반 환경의 폭발적인 성장, 파이어폭스/크롬 등 경쟁자의 등장 등이 맞물리면서 윈도우 및 IE의 독점적인 지위는 하락세를 걸었고, 크로스 브라우징 및 웹 표준에 대한 논의가 등장하면서 ActiveX(비슷한 문제를 가지고 있던 NPAPI까지도)는 마침내 퇴출된다.

## 어도비 플래시, 플래시 플레이어, 액션스크립트
- 어도비 플래시: RIA를 포함하는 다양한 프로덕트(animations, rich web applications, desktop applications, mobile apps, mobile games, and embedded web browser video players)를 개발하는 플랫폼(Java applets, MS Silverlight와 같은 레벨)
- 어도비 플래시 플레이어: 어도비 플래시에서 생산된 컨텐츠 파일(SWF 파일)을 실행하는 가상 머신
- 액션스크립트: 어도비 플래시에서의 사용(애플리케이션 개발)을 목적으로 만들어진 스크립트 언어 
