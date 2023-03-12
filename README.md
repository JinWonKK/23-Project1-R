# 김진원
# 일요일까지 Readme파일에 오늘 학습한 것을 정리해서 커밋하기.
# 월요일에 확인하시고, 다음주 목요일에 리뷰를 해주신다!!

# 내용 정리(23.03.09)

## Git 사용자 설정
Global 사용자 정보 설정 - 시스템 전체에서 사용하며, $ git config --global user.name "이름", $ git config --global user.email "이메일"을 각각 cmd창에 입력한다.  
Local 사용자 정보 설정 - $ git config user.name"이름", $ git config user.email "이메일"을 각각 cmd창에 입력한다.  
등록되어있는 사용자 정보를 확인하는 명령어는 $ git config user.name, $ git config user.email를 입력한다.

## 프로젝트 폴더 Git으로 초기화
VSCode에서는 'source control'아이콘에서 Initialize Repository버튼을 클릭 -> 폴더에 .git이라는 숨긴 폴더가 생성된다.

## vscode commit 및 Push방법
Git으로 초기화된 폴더에 파일이 생성되거나, 파일의 내용이 변경되면 Git이 추적을 시작하고, 파일에 변동이 생기면 Source control에 숫자가 표시되고 메시지를 남기며 commit할 수 있다.  
변경된 내용 중 일부 파일만 commit후 push하는 경우 케밥 메뉴를 클릭하고 Push를 선택한다.  
변경된 내용 모두 commit후 push하는 경우 commit버튼이 Publish Branch로 바뀌며 이 버튼을 클릭한다.  
이와 다르게 Romote에 repository가 없으면 새로 만들어 Push해야하며 현재 작업 폴더와 같은 이름으로 원격에 저장소를 만들고 Private인지 Public인지 선택해 주면 된다.  

## GitHub와의 연동
브라우저로 GitHub에 로그인(Chrome을 추천한다.) -> 스테이터스 바의 구름 아이콘을 클릭하거나 처음 Push를 하려하면 GitHub에 로그인 하려 한다는 팝업창이 나타난다. -> Allow클릭 후 연동을 완료한다.

## 프로그래밍이란? 
CPU에 저장된 명령어를 사용자가 사용하기 쉽도록 코드를 보내서 매칭시키는 것? 단순 명령어셋, 복잡 명령어셋이 있다. 주로 복잡 명령어셋을 사용하며 단점으로는 발열이 심하다. 최근에는 단순 명령어셋을 사용한 애플사의 M1칩이 나왔다.  
Programing언어 랭킹을 검색해볼 필요가 있다. 

## R언어 - 데이터 관리에 특화되어 있다.

## Pro Git을 다운받아서 읽어보며 공부하면 Git을 이해하는데 크게 도움이 된다.
