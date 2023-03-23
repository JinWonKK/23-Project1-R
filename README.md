# 김진원

## 내용 정리(23.03.09)



---

## 내용 정리(23.03.16)

## Readme.md 작성요령 (파일이름은 대문자)
1. 이름 : h1  
2. 강의 날자 : h2  
3. 학습 내용(필수) : h2이하 사이즈 자유 사용
4. 작성 코드(선택)  
5. 최근 내용이 위에 오도록 작성  
6. 날자 별 구분이 잘 가도록 작성  

## R언어의 특징
1. R은 python과는 다르게 데이터 분석에만 특화되어 있다.  
2. 다양한 패키지 제공 - 데이터 분석에 사용되는 함수들을 종류별로 묶어 패키지 형태로 제공한다. (쉽게 시각화를 할 수 있다.)  
3. 미적이고 기능적인 통계 그래프를 제공한다.  
4. 편리한 프로그래밍 환경 - R프로그래밍을 위한 통합 개발 환경으로 R스튜디오가 제공되어 모든 작업을 R스튜디오 내에서 처리할 수 있다.  
5. 무료사용 - 오픈소스 소프트웨어이다.

## R을 배우는 이유
1. 4차 산업혁명의 중심은 '데이터'이다.  
2. 시대의 흐름은 데이터를 잘 다룰 줄 아는 기업과 개인이 경쟁에서 우위를 점할 수 있음을 의미한다.  
3. 컴퓨팅 사고와 데이터 활용 능력은 전공을 불문하고 어떤 분야로 진출하든 점점 더 중요한 스펙이된다.
4. 배우기 쉬우면서도 강력한 데이터 처리 및 데이터 분석 능력을 제공한다.  

## Chocolatey 
마이크로소프트에서 개발한 패키지 관리자의 Window판이다.

## RStudio의 화면 구성
1. 소스 영역 - [File] - [New File] - [R Sript]에서 생성할 수 있다.
2. 콘솔 영역 - 소스창에서 작성한 R명령문을 실행시켰을 때 명령문의 실행 과정 및 결과가 표시되는 영역이다.
3. 환경 영역 - R명령문이 실행되는 동안 만들어지는 각종 변수나 자료구조의 내용을 보여주는 영역이다.
4. 파일 영역 - 윈도우의 파일 탐색기와 동일한 역할을 한다.

## RStudio 실습
1. A <- 51:80 는 A배열에 51부터 80까지의 정수를 하나 씩 넣는 코드
2. print(A) 는 A를 출력하는 코드

## 패키지의 개념
1. 이러한 함수들을 기능별로 묶어놓은 일종의 '꾸러미'인데
어떤 작업을 하느냐에 따라 필요한 패키지도 달라진다.
---

## 내용 정리(23.03.09)

## 일요일까지 Readme파일에 오늘 학습한 것을 정리해서 커밋하기.
## 월요일에 확인하시고, 다음주 목요일에 리뷰를 해주신다!!

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

---