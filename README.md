# 김진원

## 내용 정리(23.06.01)

## 공공 데이터의 활용
- 공공데이터 : 공공 기관이 만들어 내는 공적인 자료나 정보이다. 파일 데이터, 오픈 API, 시각화 등 다향한 방식으로 제공한다.
- 제공 사이트 : https://www.data.go.kr/
- 오픈API 인증키 발급 절차
1. 오픈API 검색
2. 오픈API 선정
3. 개발계정 신청
4. 승인받은 오픈API키 확인(마이페이지)
5. 승인받은 오픈API 확인
6. 오픈API 활용(R스크립트 Or Python)

---
## 내용 정리(23.05.25)

## 방사형 차트
- 레이더 차트나 거미줄 차트라고도 부르는데, 다중변수 데이터를 2차원 평면상에 시각화할 수 있는 몇 안되는 도구 중 하나로, fmsb패키지 설치가 필요하다.!
- ex)
- install.packages('fmsb')  
library(fmsb)  
score <- c(80,60,95,85,40) # 데이터 준비  
max.score <- rep(100,5) # 100을 5회 반복  
min.score <- rep(0,5) # 0 을 5회 반복  
ds <- rbind(max.score, min.score, score)  
ds <- data.frame(ds) # 매트릭스를 데이터프레임으로   
colnames(ds) <- c('국어', '영어', '수학', '물리', '음악')  
ds  
radarchart(ds) # 방사형 차트  
radarchart(ds, pcol='dark green', pfcol=rgb(0,1,0.5,0.5,0.5), plwd=3, cglcol='grey', cglty=1, cglwd=0.8, axistype=1,
seg=4, axislabcol='grey', caxislabels= seq(0,100,25)) # 옵션 지정  

## wordcloud 실습
- install.packages('wordcloud')  
library(wordcloud)  
word <- c('진원', '호용', '수민', '영준', '찬일', '도현')  
frequency <- c(851 ,222, 431, 234, 542, 111)  
wordcloud(word, frequency, colors='blue')  


---
## 내용 정리(23.05.18)

## 정렬
- ex)
- 1 <- c(1, 7, 6, 8, 4, 2, 3)  
v1 <- sort(v1) # 오름차순  
v1  
v2 <- sort(v1, decreasing = T) # 내림차순  
v2  
- ex)
- name <- c('김진원', '최호용', '최수민', '김영준', '최찬일', '김도현')  
sort(name) # 오름차순  
sort(name, decreasing = T) # 내림차순  
order(name)  
order(name, decreasing = T)  
sort(name, decreasing = T) # 내림차순  
idx <- order(name)  
name[idx]  
- sort() 함수 : 값의 크기에 따라 값을들 정렬하는 함수
- order() 함수 : 값의 크기에 따라 값들의 인덱스를 정렬하는 함수


## 매트릭스와 데이터프레임의 정렬
- 특정 열의 값들을 기준으로 행을 재배열하는 방법
- iris 데이터셋에서 꽃잎의 길이(Sepal.Length)를 기준으로 행을 재정렬하는 예
- ex)
- head(iris)  
order(iris$Sepal.Length)  
iris[order(iris$Sepal.Length),]  
iris[order(iris$Sepal.Length,decreasing = T),]  
iris.new <- iris[order(iris$Sepal.Length),] #정렬된 데이터를 저장    
head(iris.new)  

## 샘플링
- 샘플링 : 주어진 값들에서 임의의 개수만큼 값을 추출하는 작업
- 여러 번 값을 추출할때,
- 한 번 뽑은 값은 제외앟ㄴ 뒤 새로운 값을 추출하는 방식 -> 비복원 추출
- 뽑았던 값을 다시 포함시켜 새로운 값을 추출하는 방식 -> 복원 추출
- 샘플링이 필요할 때 : 데이터셋이 너무 커 분석에 시간이 많이 걸리는 경우, 일부의 데이터만 추출하여 대략의 결과를 미리 확인
- ex)
- x <- 1:100  
y <- sample(x, size=10, replace = FALSE) # 비복원 추출  
x <- 1:100  
y <- sample(x, size=10, replace = T) # 복원 추출  
- ex)
- idx <- sample(1:nrow(iris), size = 50, replace=F)  
iris.50 <- iris[idx,] # 50개의 행 추출  
dim(iris.50) # 행과 열의 개수 확인  
head(iris.50)  
- 임의 추출을 하되 재현가능한 결과가 필요한 경우 : sample()함수 실행 직전에 set.seed()함수 사용한다.

## 조합
- 조합 : 주어진 데이터값 중에서 몇 개씩 짝을 지어 추출하는 작업으로, combn()함수를 사용한다.
- ex)
- combn(1:5, 3)  
x <- c('red', 'green', 'blue', 'black', 'white')  
com <- combn(x,2)  
for(i in 1:ncol(com)){  
  cat(com[,i], '\n')  
}  

## 집계
- 데이터의 그룹에 대해서 합계나 평균을 계산하는 작업
- aggregate()함수 사용한다.!
- ex)
- agg <-aggregate(iris[,-5], by=list(iris$Species), FUN = sd)  
agg  

## 나무지도
- 데이터 분석 과정에서 중요한 기술 중 하나, 데이터 시각화
- 데이터가 저장하고 있는 정보나 의미를 보다 쉽게 파악할 수 있음
- 시각화 결과로부터 중요한 영감을 얻기도 한다!
- 사각 타일의 형태로 표현, 데이터의 정보를 타일의 크기와 색깔로 나타내며, treemap패키지 설치 후 사용한다.!




---
## 내용 정리(23.05.11)

## 두 변수의 상관관계
- 다중변수 데이터는 변수들의 대별 분석보다 변수 간의 관계를 찾는 것이 더 중요하다.
- ex) prossure 데이터셋을 이용한 예제
- head(pressure) # 데이터 확인  
plot(pressure$temperature, pressure$pressure, main ='온도와 기압', xlab ='온도', ylab ='기압')  

## 두 변수가 상관관계가 있다고 말하는 경우
1. x축 변수 값이 증가하면 y축 변수 값이 비례해서 증가하는 경우
2. x축 변수 값이 증가하면 y축 변수 값이 비례해서 감소하는 경우

## 상관계수
- 상관관계를 수치로 나타낸 -1에서 1 사이의 값
- 상관계수가 0인 경우 : 두 변수 X, Y사이에 상관성을 찾기 어렵다.
- 상관계수가 -인 경우 X, Y가 반비례, 음의 상관관계에 있다.
- 상관계수가 +인 경우 X, Y가 반비례, 양의 상관관계에 있다.
- ex)
- head(cars) # 데이터 확인  
plot(cars$speed, cars$dist, main='자동차 속도와 제동거리', xlab='속도', ylab='제동거리') # 산점도 작성  
cor(cars$speed, cars$dist) # 상관계수를 구하는 함수!  

## 다중변수 사이의 상관관계
- 변수가 3개 이상인 데이터는 변수를 2개씩 짝지어서 상관관계를 분석할 수 있다.
- ex)
- st = data.frame(state.x77)  
head(st)  
plot(st)  
cor(st)  
- 상관계수를 구하는 cor()함수에 2개의 변수가 아닌 3개 이상의 벼눗 데이터를 입력하면 다중 산점도와 비슷한 형태의 결과가 나타난다.!

## 데이터 전처리
- 확고한 데이터를 정제하고 가공하여 분석에 적합한 형태로 만드는 과정
- 현실에서는 잘 정리된 데이터셋을 바로 얻는 경우가 많지 않다.
- 데이터 전처리는 전체 분석 과정에서 오랜 시간을 차지한다.

## 결측값의 처리
- 결측값은 데이터 수집, 저장 과정에서 값을 얻지 못하는 경우 발생한다.(NA로 표현)
- 결측값이 섞여 있는 데이터셋은 분석할 때 문제를 일으킨다.
- 결측값은 2가지 방법으로 처리한다.
1. 결측값을 제거하거나 제외한 후 분석
2. 결측값을 추정하여 적당한 값으로 치환한 후 분석
- ex)
- z <- c(1,2,3,NA,5,NA,8) # 결측값이 포함된 벡터 z  
sum(z) # 정상 계산이 되지 않음  
is.na(z) # NA 여부 확인  
sum(is.na(z)) # NA의 개수 확인  
sum(z, na.rm=TRUE) # NA값 빼고 계산!  
- ex)
- z1 <- c(1,2,3,NA, 5, NA, 8) # 결측값이 포함된 벡터 1  
z2 <- c(5,8,1,NA,3,NA,7) # 결측값이 포함된 벡터 2  
z1[is.na(z1)] <- 0 # NA를 0으로 치환  
z1  
z3 <- as.vector(na.omit(z2)) # NA를 제거하고 새로운 벡터 생성  
z3  
- ex) for문을 활용하여 결측값 찾기
- x <- iris  
x[1,2]<- NA; x[1,3] <- NA  
x[2,3]<- NA; x[3,4] <- NA  
head(x)  
for(i in 1:ncol(x))  
{  
  this.na <- is.na(x[,i])  
  cat(colnames(x)[i], '\t', sum(this.na), '\n')  
}  

---
## 내용 정리(23.05.04)

## 복수 선그래프
- ex)  
- month <- 1:12  
late <- c(5,7,6,5,4,3,2,1,2,3,12,13)  
late2 <- c(4,6,5,7,8,10,2,8,4,12,3,10)  
plot(month, late, main='지각생 통계', type ='l', lty = 1, col='red', lwd = 1, xlab='Month', ylab ='Late cnt')  
lines(month, late2, type='b', col='blue')  

## 상자그림
- 사분위수를 시각화하여 그래프 형태로 나타낸 것
- 하나의 그래프로 데이터의 분포 등 다양한 정보 전달하여 단일변수 수치형 자료를 파악하는 데 자주 사용한다.!
- ex)
- dist <- cars[,2]  
boxplot(dist, main='자동차 제동거리')  

## 그룹이 있는 데이터의 상자그림
- ex)
- boxplot(Petal.Length~Species, data=iris, main='품종별 꽃잎의 길이', col=c('green','yellow','red'))  

## 산점도
- 다중변수 데이터에서 두 변수에 포함된 값들을 2차원 그래프상에 점으로 표현하여 분포를 관찰할 수 있도록 하는 도구!
- ex)
- wt <- mtcars$wt  
mpg <- mtcars$mpg  
plot(wt, mpg, main='중량 연비 그래프', xlab='중량', ylab='연비', col='red', pch=19)  
- vars <- c('mpg', 'disp', 'drat', 'wt')  
target <- mtcars[,vars]  
head(target)  
plot(target, main ='Multi plots')  

## 그룹 정보가 있는 2개 변수의 산점도
- ex)
- iris.2 <- iris[,3:4]  
levels(iris$Species)  
group <- as.numeric(iris$Species)  
color <- c('red', 'green', 'blue')  
plot(iris.2, main = 'iris plot', pch=c(group), col=color[group])  
legend(x='bottomright', legend=levels(iris$Species), col=c('red','green','blue'), pch=(c(1:3)))  

## 데이터 분석의 절차
1. 문제 정의 / 계획
2. 데이터 수집
3. 데이터 정제/전처리
4. 데이터 탐색
5. 데이터 분석
6. 결과 보고

---
## 내용 정리(23.04.27)

## 시험 관련은 체점이 완료되는 주에 문제풀이 및 확인!!

## 막대그래프
- 데이터가 포함하고 있는 정보를 이해하기 쉽게 표현하는 과정을 데이터 시각화 라고 한다.
- 막대그래프는 그룹별로 집계된 데이터를 표현하는 도구이기 때문에 막대그래프를 작성하기 위해서는 먼저 그룹별로 데이터를 집계하는 작업이 필요하다.
- ex)
- favorite <- c('Winter', 'Summer', 'Sprring', 'Summer', 'Summer', 'fail', 'fail', 'Summer', 'Spring', 'Summer', 'Summer')  
table(favorite)  
ds <- table(favorite)  
barplot(ds, main = 'Favorite Season', col = c('skyblue', 'azure2', 'gold', 'gray'), xlab='계절', ylab='빈도 수', horiz=TRUE)  
- las값에 따른 출력 방향 0 ~ 3

## 중첩 그룹의 막대그래프
- ex)
- age.A <- c(13709, 10974, 7979, 5000, 4250)  
age.B <- c(17540, 29701, 36209, 33947, 24487)  
age.C <- c(991, 2195, 5366, 12980, 19007)  
ds2 <- rbind(age.A, age.B, age.C)  
colnames(ds2) <- c('1970', '1980', '1990', '2000', '2010')  
ds2  
barplot(ds2, main ='인구 추정', col=rainbow(3), beside=TRUE, legend.text = c('0~14세', '15~64세', '65세 이상'))  

## 컬러종류 모를때!
- colors()

## 히스토그램
- 외관상 막대그래프와 비슷한 그래프로, 그룹이 명시적으로 존재하지 않는 수치형 자료의 분포를 시각화할 때 사용한다.
- R에서는 hist()함수를 이용하여 히스토그램을 작성한다.
- ex)
- head(cars)  
dist <- cars[,2]  
dist  
hist(dist, main='Histogram for 제동거리', xlab='제동거리', ylab='빈도 수', border='blue', col='green', las=2, breaks=5)  

## 히스토그램과 막대그래프 차이
- 외관상 유사하지만 일반적으로 막대 사이에 간격이 있으면 막대그래프, 간격이 없이 막대들이 붙어 있으면 히스토그램이라고 구분할 수 있다. 
- 막대그래프에서는 막대의 면적이 의미가 없지만 히스토그램에서는 막대의 면적이 의미가 있다.

## 화면 분할 및 다중 그래프
- ex)
- par(mfrow=c(2,2), mar=c(3,3,4,2))  
hist(iris$Sepal.Length, main = 'sepal.Length', col='orange')  
barplot(table(mtcars$cy1), main='mtcars', col=c('red','green','blue'))  
barplot(table(mtcars$gear), main='mtcars',col=rainbow(3),horiz=TRUE)  
pie(table(mtcars$gear),main='mtcars',col=topo.colors(3),radius=2)  
- export를 통해 Image와 pdf를 생성할 수 있다.

## 선 그래프
- ex)
- month <- 1:12  
late <- c(5,7,6,5,4,3,2,1,2,3,12,13)  
plot(month, late, main='지각생 통계', type ='l', lty = 1, lwd = 1, xlab='Month', ylab ='Late cnt')

---
## 내용 정리(23.04.13)

## 파일 입출력에서 알아야 할 내용
1. setwd('폴더 주소') # 작업 폴더 지정
2. getwd() ## 현재 주소 출력
3. print('hello) # 화면으로 출력
4. sink('result.txt', append=1) # 파일로 출력 시작
5. sink( ) # 파일로 출력 정지
6. sink('result.txt', append=T) # True로 할시 이어서 입력해주고 append=F로 할 시 초기화를 하고 입력한다.

## 조건문 if-else문
조건문 : 조건에 따라 실행할 명령문  
if( 조건 )  
 참일 경우 실행되는 명령문  
else  
 거짓일 경우 실행되는 명령문  

## ifelse문
ifelse(a>b, a, b)  
ifelse(조건, 참, 거짓)  

## 반복문 for문
for(반복 변수 in 반복 범위)  
{  
    반복할 명령문(틀)  
}  
예시 코드  
for(i in 1:5){  
    print('*')  
}  

## apply() 계열 함수
apply(iris[,1:4], 1, mean) # 행 방향으로 함수 적용  
apply(iris[,1:4], 2, mean) # 열 방향으로 함수 적용  

## 사용자 정의 함수
mymax <- function(x,y) {  
 num.max <- x  
 if(y>x){  
    num.max <- y    
 }  
 return(num.max)  
}  

---

## 내용 정리(23.04.06)

## 행과 열의 이름붙이기
1. rownames() : 행의 이름을 붙이거나 행의 이름을 출력할 때 이용한다. 
2. colnames() : 열의 이름을 붙이거나 열의 이름을 출력할 때 이용한다. ex) colnames(score) <- c('김', '진', '원')
3. 한글도 가능하다.
4. 배열이름[행, 열]을 입력하여 특정 값을 찾을 수 있다. ex) score['jinwon', 'math']
5. 배열이름[행,]을 입력하면 특정 행의 값만 찾을 수 있다.
6. 배열이름[,열]을 입력하면 특정 열의 값만 찾을 수 있다.

## 데이터프레임
매트릭스와 마찬가지로 2차원 형태이다.

실습)  
> city <- c("seoul", 'tokyo', 'washington')  
> rank <- c(1,2,3)  
> city.info <- data.frame(city, rank)  
> city.info  

## iris
150그루의 붓꽃에 대해 4개 분야의 측정 데이터와 품종 정보를 결합하여 만든 데이터 셋이다.  
실습)  
> iris[, c(1:2)] # 1~2열의 모든 데이터
> iris[1:5, c(1,3)] # 1~5행의 데이터 중 1, 3열의 데이터  
> dim[iris] # 행과 열의 개수 보이기
> colnames(iris) # 열 이름 보이기, names() 함수와 동일  
> nrow(iris) # 행의 개수 보이기  
> head(iris) # 데이터셋의 앞부분 일부 보기  
> tail(iris) # 데이터셋의 뒷부분 일부 보기  
> str(iris) # 데이터셋 요약 정보 보기  
> iris[,5] # 품종 데이터 보기  
> table(iris[,"Species"]) # 품종의 종류별 행의 개수 세기  
> colSums(iris[, -5]) # 열별 합계 S대문자!  
> colMeans(iris[, -5]) # 열별 평균  

## 행과 열의 방향 변환하기
ex) z <- matrix(1:20, nrow=4, ncol=5)  

## 조건에 맞는 행과 열의 값 추출하기
subset() 함수 매개변수  
ex)   
> IR.1 <- subset(iris, Species=='setosa')  
> IR.1  
> IR.2 <- subset(iris, Sepal.Length>5.0 & Sepal.Width>4.0)  
> IR.2  

## 매트릭스와 데이터프레임에 함수 적용
매트릭스와 데이터프레임에 산술연산 적용하기  
실습)  
> a <- matrix(1:20, 4, 5)  
> b <- matrix(21:40, 4, 5)  
> a  
> b  
> 2*a  # 매트릭스 a에 저장된 값들에 2를 곱하기  
> a+b  
> a <- a*3  
> b <- b-5  

## 매트릭스와 데이터프레임의 자료구조 확인과 변환
실습)  
> class(iris) # iris데이터셋의 자료구조 확인  
> class(state.x77) # state.x77 데이터셋의 자료구조 확인  
> is.matrix(iris) # 데이터셋이 매트릭스인지 확인하는 함수  
> is.data.frame(iris) # 데이터셋이 데이터프레임인지 확인하는 함수  
매트릭스를 데이터프레임으로 변환  
실습)  
> is.matrix(state.x77)  
> st <- data.frame(state.x77)  
> head(st)  
> class(st)  
데이터프레임을 매트릭스로 변환  
> is.data.frame(iris[,1:4])  
> iris.m <- as.matrix(iris[,1:4])  
> head(iris.m)  
> class(iris.m)  

## 데이터의 입력과 출력은 어떻게 하는 것일까
실습)  
> age <- c(20, 21, 22, 23, 24, 25) # 데이터 입력   
> age  
> young <- min(age) # 가장 작은 값 정보 추출  
> old <- max(age) # 가장 큰 값 정보 추출  
> cat('가장 젊은 사람의 나이는 ', young, '이고, ', '가장 나이든 사람의 나이는', old, '입니다. \n') # 처리 결과 출력  

## 데이터를 출력해주는 함수
1. print() 
2. cat()

## 파일을 이용해 데이터를 읽고 쓰는 방법
1. getwd() - 현재 작업 폴더 알아내기
2. setwd('변경할 파일 주소') - 작업 폴더 변경하기 
3. air <- read.csv('파일 이름') # 파일 읽기

---

## 내용 정리(23.03.30)

## 저장된 값을 보여주고 지우는 함수
1. ls() - 저장된 변수는 보여줌
2. rm(변수명) - 지우는 함수
3. rm(list = ls()) - ls를 모두 지워줌.

## 1차원 자료와 2차원 자료
1. 1차원 자료 - 전 세계 국가의 GNP나 연도별 수출액과 같이 단일 주제에 대한 값들을 모아 놓은 것
2. 2차원 자료 - 4학년 학생의 전 과목 성적이나 도시의 월별 실업률과 같이 특수 주제에 대한 값을들 모아놓은 자료
3. 1차원 자료 - vector, list, factor
4. 2차원 자료 - matrix, data frame

## 범주형 자료와 수치형 자료
1. 범주형 자료 - 분류의 의미를 갖는 값들로 구성된 자료로, 보통 문자로 표현되고 산술 연산을 적용할 수 없음.
2. 수치형 자료 - 값들이 크기를 가지며 산술연산이 가능함.

## R은 인덱스값이 1부터 시작한다.

## 벡터와 벡터의 연산
길이가 같아야 하고, 값의 종류가 같아야 한다.

## 벡터에 적용 가능한 함수들
1. sum() - 값들의 합
2. mean() - 값들의 평균
3. max(), min() - 최대값, 최소값
4. sort() - 정렬
5. length() - 길이

## 벡터의 논리 연산자
1. A < B B가 A보다 크면 True
2. A == B 둘이 같으면 True
3. A != B 둘이 다르면 True
4. A >= 5 5보다 크거나 같으면 True

## 리스트
1. 자료형이 다른 값들을 한 곳에 저장하고 다를 수 있도록 해주는 수단

## 매트릭스와 데이터 프레임은 2차원 자료를 저장하기 위한 대표적인 자료구조
매트릭스는 2차원 테이블 형태의 자료구조.

---

## 내용 정리(23.03.23)

## 패키지의 개념
로딩 : 패키지는 R에서 불러와 사용한다.

## 패키지 설치와 사용
1. 패키지 설치하기 : R스튜디오에서 패키지를 설치하기 전에 인터넷이 연결되어 있는지 먼저 확인한다.
2. 명령문으로 설치하기 : R에서 install.packages()함수를 이용하면 알아서 설치된다. 
3. 패키지 로드하기 : install.packages('ggplot2')
4. 함수 사용하기 : 날짜 보기 : sys.time()
5. 도움말 사용 방법 : 소스창에서 함수 앞에 ?sort를 입력하고 실행한다.

## 챗봇을 좀 활용해보자!!!

## 변수의 개념
1. 내용물을 구분하기 위해 이름을 붙이고 저장한다.
2. 변수 만들기 : a <- 10 a에 10을 넣는다.
3. 변수 내용 확인하기 : 변수명을 입력한다. print(변수명) 
4. 변수의 값은 변경이 가능하다.

## 변수명의 작명 규칙
1. 첫 글자는 영문자나 마침표로 시작하는데, 일반적으로 영문자로 시작한다.
2. 두 번째 글자부터는 영문자, 숫자, 마침표를 사용 ㅎ가능하다.
3. 변수명에서 대문자와 소문자는 별개의 문자로 취급한다.
4. 변수명 중간에 빈 칸을 넣을 수 없다.

## 변수에 저장될 수 있는 값의 종류
1. 숫자형
2. 문자형
3. 논리형
4. 특수 값 : NULL(정의되어 있지 않음을 의미), NA(결측값), NaN(수학적으로 정의가 불가능한 값), Inf(양의 무한대), -Inf(음의 무한대)

## 벡터의 개념
1. R에서 제공하는 여러 개의 값을 한꺼번에 저장하는 기능이다. 
2. 일반적인 프로그래밍 용어로는 1차원 배열이라고도 한다.  
3. 벡터는 매우 중요하다!!

## 함수의 매개변수
1. 프로그래밍에서 함수의 입력값을 받는 변수를 매개변수라 한다.
2. 함수의 정의에 맞추어 매개변수를 입력하면 정의된 결과값을 얻을 수 있다.

## 함수는 다 외우진 못해도 필요할 때 찾아서 쓸 수 있으면 좋다!!

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