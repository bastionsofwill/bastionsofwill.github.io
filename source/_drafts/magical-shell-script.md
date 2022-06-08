---
title: 쉘 스크립트 기초
tags:
- unix
- shell
---

## 이게 대체 뭔 소리야
```bash
#!/bin/bash
set -eo pipefail
ID=$(dd if=/dev/random bs=8 count=1 2>/dev/null | od -An -tx1 | tr -d ' \t\n')
```
AWS Lambda를 공부하던 중에 샘플 코드에 위와 같은 내용이 있었다.
이를 이해하는 데 제법 오랜 시간이 걸렸으나 그 과정에서 알게 된 것이 많다.

하향식으로 접근하면, 위 코드(쉘 스크립트)는 3개 행으로 구성되어 있다.
- 1행: shebang
- 2행: `set` 명령어와 그 옵션
- 3행: `$`, `|` 명령어와 쉘 스크립트의 조합

이를 하나씩 뜯어서 살펴보자.

## Shebang
`#`과 `!`의 조합으로 시작되기 때문에 이러한 이름이 붙었다. 
따라서 '셔뱅'이라고 읽으며, *sha-bang*, *hash-bang*이라고도 한다. 프로그램으로서 실행되는 스크립트임을 알리기 위해 스크립트 시작점에 작성하는 문자열이며, 나머지 부분은 인터프리터 지시자로 해석된다.
```bash
#! /bin/bash
```
특정 경로에 존재하는 어떤 스크립트의 첫 행이 위와 같다면, Unix-like OS는 그 스크립트를 프로그램으로 인식하며, 지정한 인터프리터, 즉 `/bin/bash`를 실행하면서 해당 스크립트가 위치한 경로가 그 인수로 전달된다.

## set -eo pipefail
`set`은 로컬 환경변수의 조회 및 쉘 환경 설정 기능을 수행한다. 환경변수를 조회한다는 점에서 `env`명령어와 유사하지만, `env`명령어는 글로벌 환경변수의 조회만 가능하다는 점에서 그 차이가 있다.
- `-e`옵션: 오류 발생 시 프로세스 중단
- `-o pipefail`옵션: pipe 오류 코드 승계
즉, `set -eo pipefail` 명령을 실행하면, 이후 실행되는 pipe로 연결된 스크립트 중 하나만 non-zero exit code를 반환하여도 프로세스가 중단된다. 

## 기본 명령어
### |
파이프 명령어로, 파이프 왼쪽에 위치한 (출력)값을 오른쪽에 위치한 명령어의 입력으로 전달한다.
```bash
ls -al | grep "yml"
```
예를 들어, 위 스크립트는 `|` 왼쪽의 `ls -al`의 출력을 오른쪽 `grep "yml"`의 입력으로 전달한다. 
따라서, `ls-al`의 출력값은 cli로 출력되지 않고 `grep "yml"`의 입력로 전달되며, 결과적으로 현재 디렉토리에 존재하는 파일과 디렉토리의 리스트(`ls -al`의 출력) *중에서* `yml`이라는 문자열을 포함하는 행만 출력된다.

### $와 명령어 치환(Command Substitution)
쉘 스크립트에서 `$`는 변수를 가리키기 위해 사용된다. 예를 들어, `$VAR`또는 `${VAR}`과 같이 VAR라는 변수의 값에 접근할 수 있다.
```bash
$(cat file.txt)
```
하지만 위의 예시에서 `$`는 변수의 값에 접근하기 위해 사용된 것이 아니라, 명령어 치환을 위해 사용되었다. `$(command)`형태의 스크립트는 자기 자신을 subshell 환경에서 `command` 명령어를 실행한 표준 출력으로 대체한다.
(다만 예시는 `$(< file)`와 동치이며, `<`를 사용하는 것이 더 빠르다.)



### 출처
https://ko.wikipedia.org/wiki/%EC%85%94%EB%B1%85
https://zetawiki.com/wiki/%EB%A6%AC%EB%88%85%EC%8A%A4_set
https://zetawiki.com/wiki/%EB%A6%AC%EB%88%85%EC%8A%A4_set_-e
https://zetawiki.com/wiki/%EB%A6%AC%EB%88%85%EC%8A%A4_set_-euxo_pipefail
https://zetawiki.com/wiki/%EB%A6%AC%EB%88%85%EC%8A%A4_env,\_set_%EC%B0%A8%EC%9D%B4%EC%A0%90
https://www.gnu.org/software/bash/manual/html_node/Command-Substitution.html

