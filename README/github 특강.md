> ### 1. git이란?
>
> - 코드의 history를 관리하는 도구 개발된 과정과 역사를 볼 수 있고, 특정 시점으로 복구가 가능
>
> ### 2. 퀴즈 !
>
> - #### . git == Github 정답은 X !
>
> - #### git을 기반으로 한 서비스는 Github이 유일하다 정답은 X !
>
> ### 3. git 기본
>
> - add 커밋할 목록에 추가
> - commit 커밋 (히스토리의 한 단위) 만들기
> - push 현재까지의 역사 (commits) 가 기록되어 있는 곳에 새로 생성한 커밋들 반영하기
> - 터미널 창 실행 후, 미리 설정되어있을지 모를 계정 정보 삭제 (처음 설치시 생략 가능)
>
> ```
> $ git config --global --unset credential.helper
> $ git config --system --unset credential.helper
>
> ```
>
> - 나의 github 계정 이메일과 본인의 영문이름으로 계정 정보 등록
>
> ```
> $ git config --global user.email “내이메일@적어요”
> $ git config --global user.name “내이름 적어요”
>
> ```
>
> ### 4. git training
>
> - stage 1: basic routine
>
> ```
> $ git status 파일의 상태 확인
> $ git show HEAD 가장 마지막 커밋을 조회
> $ git log 저장소의 커밋 히스토리를 시간순으로 보여줌
>
> ```
>
> - stage 2: check differences
>
> ```
> $ git diff 파일의 변경사항을 보여줌
> puts "hello"
> -puts "hi"
> +puts "bye"
> $ git log -p 각 커밋의 diff 결과를 보여줌
> $ git log -p -숫자 가장 최근 숫자개의 커밋 diff를 보여줌
>
> ```
>
> - stage 3: bring the repository
>
> ```
> $ git clone 리포주소 로컬에 해당 리포의 파일들을 가져옴
> # clone을 사용하지 않고 Download ZIP을 사용하게 된다면 git init 부터 즉 처음부터 하나하나 입력해야함.
> # 그리고 open in Desktop은 되도록 사용하지말자 ! 사용하다 꼬이면 답없음 !
>
> ```
>
> 1. 이번에는 두 대의 컴퓨터를 이용하여 git 을 관리하는 실습을 진행 함 !
>
> - mkdir git_local / 집에서 사용하는 컴퓨터라고 가정
> - mkdir git_other / 학교 또는 회사에서 사용하는 컴퓨터라고 가정
>
> ```
> < other 환경 >
> 1. clone 으로 local 환경에서 작업한걸 불러오자
> $ git clone 리포주소
> 2. other에서 작업한 것을 commit 하자
> $ git add 파일 명.
> $ git commit -m "커밋내용"
> $ git push -u origin master
> < local 환경 >
> 3. 여기서는 other에서 작업한 내용을 불러오면 된다 !
> $ git pull
>
> ```
>
> 1. 실수로 git add . 를 해버려서 특정 add 파일을 취소하는 방법을 알아보겠음 !
>
> ```
> 1. 먼저 git add .한 상태
> $ git reset HEAD 파일명
>
> ```
>
> - stage 4: undo
>
> ```
> $ git commit --amend 가장 최근의 커밋 메세지를 수정
> $ git reset HEAD 파일명 가장 최근 커밋에서 해당 파일을 add 취소
>
> ```
>
> - stage 5: versioning
>
> ```
> $ git checkout HEAD~1 하나 직전 커밋으로 돌아감
> $ git checkout 커밋해시코드6자리 해당 커밋으로 돌아감
>
> ```
>
> - 에러 무시하고 강제 push 하는 방법 !
>
> ```
> $ git push -f origin master 
> 이건 협업할때 사용하지 말자 ! 에러를 무시하고 강제로 push 하는 거임 !
>
> ```
>
> ### 5. Fork 사용하기
>
> - 리포를 포크 눌른 상태로 가정한 후
>
> ```
> # 포크 후 내 리포에 생성된 리포
> $ git clone 리포주소
>
> ```
>
> - 브런치 추가하기
>
> ```
> $ git checkout -b "브런치명"
>
> ```
>
> - 브런치에 커밋하기
>
> ```
> $ git add "파일명"
> $ git commit -m "커밋내용"
> $ git push -u origin "브런치명"
>
> ```
>
> - pull request 수정하기
> - 브런치에서 Compare & pull request 누른 뒤 내용을 수정하고 create 버튼 누르기 !
> - 브런치 합치기
>
> ```
> 1. test 브런치를 만들고
> $ git checkout -b test
> 2. 파일을 하나 생성해주자 !
> $ touch test.txt
> 3. 이후 add 와 커밋을 한 뒤
> $ git add test.txt / $ git commit -m "another test branch"
> 4. develop 브런치로 이동하자
> $ git checkout devlop
> 5. 이후 브런치를 합치자
> $ git merge test
>
> ```

### 재미있는 javascript 라이브러리 사용하기

> 1. 우선 깃허브에 typed.js를 검색한 후 메인에 있는 <https://mattboldt.com/demos/typed-js/> 주소에 들어가 데모 코드를 download 하자 !
> 2. 이후 알집을 풀고 index.html 을 Atom으로 열어주자 !
>
> ```
> <h2 id="basic">Basic Demo</h2>
> <div class="type-wrap">
>  <div id="typed-strings">
>    <span>안녕하세요. 여기는 <strong>506호</strong>입니다.</span>
>    <p>블라블라 <em>소개소개</em> </p>
>    <p> 힘내세요 !</p>
>  </div>
>  <span id="typed" style="white-space:pre;"></span>
> </div>
> ```
>
> - demons.js 조작하기
>
> ```
> var typed = new Typed('#typed', {
>  stringsElement: '#typed-strings',
>  typeSpeed: 200,
>  backSpeed: 40,
>  startDelay: 1000,
>  loop: false,
>  loopCount: Infinity,
>  ...
> });
> // 이부분을 수정하면 typed-strings에 해당하는 div가 수정이 됨 !
> ```