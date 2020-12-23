# Review Git Settings

## single branch 로 clone한 후 새로운 브랜치를 추가하는 경우

git에서 브랜치가 너무 많아 특정 브랜치만 추적하도록 clone할 수 있다.

클론
```
git clone -b {본인_아이디} --single-branch https://github.com/{본인_아이디}/{저장소 아이디}
ex) git clone -b javajigi --single-branch
```

## 원격 저장소 브런치 제어
> 위와 같이 clone한 후 새로운 브랜치를 추가하고 싶은 경우가 있으면 다음과 같이 새로운 브랜치를 추가할 수 있다.

```
git remote set-branches --add origin [remote-branch]
git fetch origin [remote-branch]:[local-branch]
```
---

* 터미널에서 다음 명령을 입력해 브랜치를 생성한다.

```
git checkout -b 브랜치이름
ex) git checkout -b step1
```

* 본인 원격 저장소에 올리기

> 로컬에서 commit 명령을 실행하면 로컬 저장소에만 반영되고, 원격 github.com의 저장소에는 반영되지 않는다.

```
git push origin 브랜치이름
ex) git push origin step1
```

* merge를 완료했다는 통보를 받으면 브랜치 변경 및 작업 브랜치 삭제(option)한다.

> 강사에게 승인 후 merge를 완료했다는 통보를 받으면 해당 미션은 완료한 상태가 된다.
>
> 현재 미션을 완료했기 때문에 미션을 진행한 브랜치를 삭제하고 다음 미션을 위한 새로운 브랜치를 생성해야 한다.

```
git checkout 본인_아이디
git branch -D 삭제할_브랜치이름 // -D 강제삭제
ex) git checkout javajigi
ex) git branch -D step1
```

* 통합(merge)한 next-step 저장소와 동기화하기 위해 next-step 저장소 추가(최초 한번만)

> 계정 브랜치에서 다음 미션을 이어서 진행하기 위해 브랜치를 생성하려고 한다.
>
> 그런데 로컬 PC의 현재 상태는 최신 코드가 아니기 때문에 미션을 이어서 진행할 수 없다. 따라서 **next-step에 통합(merge)된 코드와 동기화하는 작업을 진행**해야 한다.

```
git remote add {저장소_별칭} base_저장소_url
ex) git remote add upstream https://github.com/next-step/java-racingcar.git
// 위와 같이 next-step 저장소를 추가한 후 전체 remote 저장소 목록을 본다.
git remote -v
```

* next-step 저장소에서 자기 브랜치 가져오기(또는 갱신하기)

> 앞 단계의 `remote add` 명령은 로컬 PC에서 next-step 저장소에 접근할 수 있도록 이름을 부여한 것이다. 앞 단계의 예제는 upstream이라는 이름을 부여했다.
>
> 앞 단계에서 next-step 저장소에 이름을 부여했다면 이번 단계는 fetch 명령으로 동기화하고 싶은 next-step 저장소의 브랜치를 가져오기 해야 한다.

```
git fetch upstream {본인_아이디}
ex) git fetch upstream javajigi
```

* next-step 저장소 브랜치와 동기화하기

> 현재 상태는 next-step 저장소 브랜치를 가져오기는 했지만 아직까지 로컬 저장소에 최신 버전의 코드가 반영된 것은 아니다.
>
> rebase 명령을 실행해 next-step 저장소와 로컬 저장소의 브랜치를 동기화한다.

```
git rebase upstream/본인_아이디
ex) git rebase upstream/javajigi
```

* 새로운 미션을 진행하기 위한 브랜치 생성
> 지금까지 과정을 통해 새로운 작업을 시작하기 위한 준비 작업을 마쳤다.
>
> 다음 단계는 [코드리뷰 요청 1단계](./review-step1.md)의 4번 항목의 checkout 명령으로 새로운 브랜치를 생성한다.

```
git checkout -b 브랜치이름
ex) git checkout -b step2
```
