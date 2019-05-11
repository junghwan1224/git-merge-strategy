## Merge 전략

- merge
  - ff merge
    - branch에서 push한 내용 그대로 merge
  - no-ff merge [v]
    - merge commit을 생성하면서 merge

> 기본적으로 merge를 하게 되면, 변경 사항을 확인해서 자동으로 ff 또는 no-ff를 해주지만, 우리는 no-ff를 기본적으로 진행!

```
$ git merge --no-ff [BRANCH_NAME]
```

- rebase

  - feature branch에서 develop branch을 rebase
    - commit 히스토리를 정리하기 위해
    - develop branch에서의 변경사항을 feature branch별로 적용하여 테스트 해보기 위해

  $ git rebase develop

## Branch 전략

- git flow
- hub flow
- lab flow

### J-flow

- master (릴리즈 버전만)
  - master `merge` 시 `commit` 메세지 Tag에 version을 표시
- develop (전체 테스트 진행)
  - 테스트 완료시 master로 `merge`
- feature (작업단위 별로 branch 생성)
  - 예 : feature/vcs-140-login
  - 각 테스트는 feature에서 진행!
- hotfix (우선순위 1위)
  - 상용화 버전에서 에러가 발생한 문제를 빠르게 해결하기 위한 branch

> 각자 feature 에서 개발한 내용을 테스트 하기 위해 develop branch를 rebase하고 테스트 통과시 merge

## 정리

1. `develop branch`에서 `feature branch` 생성
2. `feature branch`로 checkout 후 작업 진행
3. 작업이 완료되면 `develop branch`를 rebase
4. `feature branch`에서 변경사항 적용 후 테스트
5. `feature branch` 푸쉬 후 pull request
6. pull request 확인 후 `develop branch`에 merge
7. merge 후 develop pull



#### 명령어로 자세히 정리해보자면

- git checkout -b feature/{feature_name} 브랜치를 만든다.
- push하기전에!!! 작업내용 모두 커밋완료 후!
- feature브랜치에서 git rebase develop
- 위에서 중요한 점!!! develop이 최신인가!! 오리진에 있는걸 Pull받아서 로컬브랜치를 최신으로 업데이트 후 feature 브랜치에 rebase
  요약: develop브랜치에서 git pull받자!
- git checkout develop
- git merge --no-ff feature/{feature_name}
- git push (이것도 develop 브랜치에서)


