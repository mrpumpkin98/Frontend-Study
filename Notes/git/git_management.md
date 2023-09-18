# Git 관리 1탄

## ✅ Git-flow 전략

- **`master`** : 제품으로 출시될 수 있는 브랜치
- **`develop`** : 다음 출시 버전을 개발하는 브랜치
- **`feature`** : 기능을 개발하는 브랜치
- **`release`** : 이번 출시 버전을 준비하는 브랜치
- **`hotfix`** : 출시 버전에서 발생한 버그를 수정 하는 브랜치

![](https://velog.velcdn.com/images/sju4486/post/7c803f8c-ea7e-4b62-9e1d-d548d397e7a2/image.png)

### git-flow 단계

1. 처음에는 `master`와 `develop` 브랜치가 존재한다. `develop` 브랜치는 `master`에서부터 시작된 브랜치다.

2. `develop` 브랜치에서는 상시로 버그를 수정한 커밋들이 추가된다.

3. 새로운 기능 추가 작업이 있는 경우 `develop` 브랜치에서 `feature` 브랜치를 생성한다. `feature` 브랜치는 언제나 `develop` 브랜치에서부터 시작하게 된다.

4. 기능 추가 작업이 완료되었다면 `feature` 브랜치는 `develop` 브랜치로 merge 된다.

5. `develop`에 이번 버전에 포함되는 모든 기능이 merge 되었다면 QA를 위해 `develop` 브랜치에서부터 `release` 브랜치를 생성한다.

6. QA를 진행하면서 발생한 버그들은 `release` 브랜치에 수정된다.

7. QA를 무사히 통과했다면 `release` 브랜치를 `master`와 `develop` 브랜치로 merge 한다.

8. 마지막으로 출시된 `master` 브랜치에서 버전 태그를 추가한다.

</br>

## ✅ 기본적인 branch 명령어

</br>

- **branch 생성 및 생성된 branch로 전환**

```
git checkout -b <branch 이름>
```

- **현재 자신의 파일과 연결된 branch 목록**

```
git branch
```

- **branch전환**

```
git checkout <branch 이름>
```

- **branch 생성**

```
git branch <branch 이름>
```

- **branch 삭제**

```
git branch -d <branch 이름>
```

- **branch 강제 삭제**

```
git branch -D <branch 이름>
```

- **branch에 코드push**

```
git push origin <branch 이름>
```

- **merge하는 법**

```
git checkout <branch 이름>
git merge <branch 이름>
```

- **branch 끼리 비교**

```
git diff <branch 이름> <branch 이름
```

</br>

## ✅ 깃 내려받고 풀리퀘스트하는 순서

</br>

1️⃣ **현재 로컬 저장소에 다른 리모트 저장소를 추가하는 명령어**

```tsx
git remote add upstream 회사 레파지토리 주소
```

`작업 시`

1️⃣ **feature 브런치 생성**

```tsx
git checkout -b feature-issue01
```

2️⃣ **현재 브런치 확인**

```tsx
git branch
```

`작업종료 시`

1️⃣ **현재 작업 디렉토리의 모든 변경 사항을 git의 staging area에 추가**

```tsx
git add .
```

2️⃣ **커밋 컨벤션 적용**

```tsx
git commit -m “커밋 내용”
```

3️⃣ **origin으로 푸쉬**

```tsx
git push origin feature-issue01
```

4️⃣ **깃허브: fork했던 내 레파지토리로 들어가서 풀리퀘스트 요청하기**

![](https://velog.velcdn.com/images/sju4486/post/80964fba-ceb1-409a-bb43-560d885fc658/image.png)

`다시 작업시작 시`

1️⃣ **내려받을 브런치 확인**

```tsx
git checkout master (마스터로 되어있는지 꼭 확인)
```

2️⃣ **내려 받기**

```tsx
git pull upstream develop
```

</br>

## ✅ git 커밋 컨벤션

</br>

\*️⃣ **Commit Type**

- **`feat`** : 새로운 기능 추가
- **`fix`** : 버그 수정
- **`docs`** : 문서 수정
- **`style`** : 코드 포맷팅, 세미콜론 누락, 코드 변경이 없는 경우
- **`refactor`** : 코드 리펙토링
- **`test`** : 테스트 코드, 리펙토링 테스트 코드 추가
- **`chore`** : 빌드 업무 수정, 패키지 매니저 수정

\*️⃣ **Subject Rule**

1. 제목은 최대 50글자 넘지 않기
2. 마침표 및 특수기호 사용x
3. 첫 글자 대문자, 명령문 사용
4. 개조식 구문으로 작성(간결하고 요점적인 서술)

## 참고

- [우아한 기술블로그](https://techblog.woowahan.com/2553/)
- [코드짜는 문과녀](https://eunhee-programming.tistory.com/256)
