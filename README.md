## 01. Git 이 무엇인가..?!   
  - **버전 관리를 도와주는 시스템**이다.
  - **Git의 동작 방식**
    - 커밋에서 발생하는 차이들만 저장하는 것이 아니라, 커밋된 파일 전체인 스냅샷을 저장한다.
    - 바뀌지 않은 파일은 이전 파일의 링크만 저장하기 때문에, 용량을 많이 잡아먹지 않고, 계산도 필요 없다.
  - **.git 파일 내부에 저장되어 있는 정보**
    - 원격저장소의 주소
    - 버전 관리한 데이터 등..


## 02. Git 상태/공간 뜯어보기

![git_4status](https://user-images.githubusercontent.com/59442344/110064253-154cc180-7db0-11eb-8eb8-78387c2dc354.jpg)

  - **Git/GitHub으로 구분되는 4가지 공간.**
    - **작업 공간(WorkSpace)**
    - **로컬저장소(.git) 스테이지(stage**)
    - **로컬저장소(.git) commit저장소**
    - **원격저장소(GitHub)**   
 
  - **Git으로 관리하는 파일의 4가지 상태**
    - **추적 안됨 (untracked)** / 로컬저장소에 올라간 적 없음 : WorkSpace에서 작업 중인 파일.
    - **추적 됨 (tracked)** / 로컬저장소에 올라간 적 있음
      - **스테이지됨 (staged)** : WorkSpace에서 Stage로 올라온 파일. (선택된 파일)
      - **수정없음 (unmodified)** : commit된 내용과 WorkSpace에 존재하는 내용에 차이가 없는 파일
      - **수정함 (modified)** : staged되지 않고, commit된 내용과 WorkSpace에 존재하는 내용에 차이가 존재하는 파일


## 03. Git file (System/Global/Local file) 
  - **System 설정 파일** : 전체 system 사용자에게 적용된다.
    - git config --system 명령어
  - **Global 설정 파일** : 한 사용자의 전체 git 저장소에 적용된다.
    - git config --global 명령어
  - **Local 설정 파일** : 하나의 저장소에만 적용된다.
    - git config --local 명령어


## 04. Git 협업
  - **Branch** : 여러 명의 협업자들이 줄기를 나누어 프로젝트를 작업할 수 있게 도와주는 기능
    - **여러 명**이 **작업의 갈래를 나누지 않은 상태**라면
      - **먼저 푸시**한 커밋은 **정상**적으로 올라간다
      - **나중에 푸시**한 커밋은 **'낡은 커밋에 푸시하지 말라'는 오류가 발생**한다.
    - **Branch**는 단순한 포인터이다.
      - **[master] pointer** : Git이 제공하는 기본 브랜치(포인터)
      - **[HEAD] pointer** : 브랜치 사이를 넘나들 수 있게 해주는 포인터
        - detached HEAD 상태 : master 포인터에서 HEAD 포인터가 분리된 상태
    - **Branch**를 만들 때에는 base를 잘 설정해야 한다. (어떤 시점에서 브랜치를 뻗어나갈 것인가?)
    - **[master] pointer**를 기준으로 branch를 생성한 후에, 협업한 내용들을 다시 **merge** 한다.
- **Merge** : 병렬로 뻗어나간 가지들간의 합집합을 구하는 기능이다.
- **Merge의 3가지 경우**
  - **Merge commit** : 여러 branch들을 합치는 과정에서 새로운 상태를 새롭게 저장하는 commit
    - 어떤 브랜치를 기준으로 병합할지를 선택하는 과정이 요구된다.
  - **Fast-Forward** : 여러 branch들을 합치는 과정에서 어떤 branch가 다른 branch를 포함하여 굳이 새로운 상태를 새롭게 저장할 필요가 없는 commit
  - **Conflict** : 여러 branch를 합치는 과정에서 중첩된 상태가 발견되어 충돌이 일어난 상황
    - Conflict가 발생하면 충돌이 난 부분을 확인하여, 어떤 것을 남길지를 수동으로 택하고 병합하는 과정이 요구된다.
- **Pull Request**
  - master branch에 merge해도 되는지에 대해서 협력자에게 허락을 요청하는 과정!
  - **base branch / compare branch**
    - **base branch** : 병합 결과물이 올라갈 기준이 되는 브랜치
    - **compare branch** : base branch와 비교대상이 되는 브랜치
  - **Compare & pull request** : 원격 저장소에 커밋을 수행한 경우, 협력자에게 pull request를 보낸다.
  - **new pull request** : 다른 branch로 pull request를 직접 보내거나, 직접 설정을 변경하고 싶은 경우 사용.
- **Tag** : 특정 커밋, 상태에 버전을 붙여주거나, 별칭을 붙여주는 역할을 한다.
  - branch와 마찬가지로 커밋을 가리키는 포인터이다.
  - push해주어야 원격저장소에서도 확인할 수 있다.


## 05. Git 용어   
  - **원격 저장소 (repository)** : GitHub에서 협업할 공간. (다른 개발자들과 같이 버전관리할 공간.)
  - **로컬 저장소** : 내 컴퓨터에서 Git으로 버전관리 중인 공간
    - 특정 폴더 내의 숨겨진 .git 폴더가 바로 로컬 저장소 이다.
    - CLI 환경에서는 git init 이라는 명령어를 통해서 .git 폴더 생성됨
    - GUI 환경에서는 +create 이라는 아이콘을 통해서 .git 폴더 생성됨 
    - .git 폴더에 원격저장소의 주소, 버전 관리 데이터 등의 필요한 정보를 저장.
  - **Git** : 버전 관리 시스템
  - **GitHub** : Git을 통해 관리하는 프로젝트를 올려두는 공간
  - **GUI** : Graphic User Interface, 마우스로 명령 입력
  - **CLI** : Command Line Interface, 커멘드 라인으로 명령어 입력
  - **Git Bash** : CLI 방식으로 Git을 이용하게 해주는 터미널 환경
  - **commit** : 버전을 갱신하는 것, 새로운 버전으로 생성된 파일
  - **log** : 모든 commit 확인
  - **checkout** : 원하는 지점의 버전으로 파일을 되돌릴 수 있다.
  - **push** : 로컬 저장소 -> 원격 저장소로 commit을 올리는 것.
  - **pull** : 원격 저장소 -> 로컬 저장소로 commit을 내려받는 것.
  - **branch** : 특정 버전 위치를 가리키는 포인터이다.
  - **master** : Git이 제공하는 기본적인 branch 이름, 보통 로컬저장소의 버전 상태를 가리키며, 새로운 commit을 master 위에 올린다.
  - **origin** : 원격 저장소의 닉네임이며, 다른 이름으로 변경 가능. 원격 저장소의 현재상태를 사리키는 꼬리표.
    - $git remote add **origin** " ... " : 원격 저장소의 닉네임을 origin으로 저장하라는 git 명령.
    - **git push origin master** : master의 모든 새로운 commit들을 origin위에 올리는 명령.
    - **origin / master** : 보통 원격저장소의 버전 상태를 가리킨다.
  - **head** : 커밋들을 자유롭게 가리킬수 있는 포인터이다. head 포인터를 통해서, branch를 넘나들 수 있다.

