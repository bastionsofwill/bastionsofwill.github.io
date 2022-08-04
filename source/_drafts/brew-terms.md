---
title: brew-terms
tags:
- macOS
- homebrew
---
## Homebrew 푸념
macOS에서 널리 사용되는 패키지 매니저인 Homebrew(리눅스에서도 리눅스용 Homebrew를 사용할 수 있긴 하다.)는 리눅스에서 주로 사용되는 패키지 매니저인 apt, yum과 유사한 방식으로 cli 명령어를 통해 패키지를 설치/조회/삭제할 수 있다.

문제는 다른 패키지 매니저와는 전혀 다른 용어를 사용한다는 점이다.
Homebrew라는 이름처럼 패키지 설치 및 관리 프로세스 관련 개념들을 주류를 유통하는 과정에 빗대어 사용하는데, 관련 용어에 대한 사전 지식이 있다면 모를까 그렇지 않다면 사용하는데 불리하게 작용하는 것 같다.
게다가 주류 관련 지식이 있으면 이해가 편할까 싶어서 조사해본 결과, 패키지 매니저가 사용하는 기술적인 개념을 잘 매칭시키지도 못하는 것 같아서 불만이 있다.

## Homebrew 용어
개인적으로는 진입 장벽이라고 생각되어 별로였다. 
애초에 오픈소스 프로젝트에서 개념을 어떻게 정의하는지는 프로젝트를 유지하는 사람들 마음이지만, 어떻게 이런 마니악한 센스로 macOS라는 큰 시장에서 지배적인 위치에 자리잡게 되었는지... 모를 노릇이다. 

케그는 탄산(carbonated) 음료를 보관하기 위해 높은 압력을 버티는 통이고, 캐스크는 '술통'이라고 말하면 보편적으로 떠올리는 큰 통(그라가스 Q)이다. 

- cask: Homebrew package definition that installs macOS native applications
- keg: installation destination directory of a given formula version e.g. /usr/local/Cellar/foo/0.1
- rack: directory containing one or more versioned kegs e.g. /usr/local/Cellar/foo
- keg-only: a formula is keg-only if it is not symlinked into Homebrew’s prefix (e.g. /usr/local)
- cellar: directory containing one or more named racks e.g. /usr/local/Cellar
- directory containing one or more named casks e.g. /usr/local/Caskroom
- tap: directory (and usually Git repository) of formulae, casks and/or external commands
- pre-built keg poured into the cellar/rack instead of building from upstream sources

탭은 수도꼭지로, 맥주가 나오는 지점을 말한다.
포뮬라는 맥주랑은 비교적 거리가 먼 용어
보틀
셀러(cellar)

### 출처
https://docs.brew.sh/Formula-Cookbook#homebrew-terminology
https://www.sevenbro7hers.com/faq/whats-the-difference-between-cask-and-keg-beer/
