---
title: Dependabot
tags:
    - 
---
### 내 main 브랜치에 무슨 짓이야
Github 리포지토리에 Dependabot이라는 봇이 main 브랜치를 내가 생성한 적이 없는 브랜치와 머지하는 PR을 작성하였다. 
![](/images/dpdb_pr.png)
버전 번호를 새 값으로 갱신하는 행위를 bump라고 한다.[1][1] 즉, Dependabot은 내 리포지토리에 존재하는 코드의 의존성을 확인하여 PR을 생성해 준다. 루비, 파이썬, 자바스크립트Ruby, Python, JavaScript 등 넓은 범위의 언어를 지원하며, `.github/dependabot.yml` 파일을 통해 업데이트 스케줄, 최대 open된 PR의 개수 등을 설정할 수 있다.



### 출처
[1]: https://stackoverflow.com/questions/4181185/what-does-bump-version-stand-for
- https://stackoverflow.com/questions/4181185/what-does-bump-version-stand-for
- https://www.nearform.com/blog/automatic-dependency-bump/
