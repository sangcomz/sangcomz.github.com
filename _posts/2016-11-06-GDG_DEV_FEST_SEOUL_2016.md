---
layout: post
title:  "GDG DEV FEST SEOUL 2016를 다녀와서.."
categories: Conference
---

“늅투촋" : “뉴비(초보)부터 초고수까지"라는 주제의 GDG 행사에 다녀왔다.  
나는 3가지 세션을 들었다. WorkShop도 듣고 싶었지만 경쟁이 치열해서 듣지 못했다.  
내가 들었던 3가지 세션은...  

* 완전 기초부터 다뤄보는 Machine Learning / TensorFlow 101
* 안드로이드 개발에 유용한 도구들
* 오픈 소스를 통해 개발 근육 강화하기


## 완전 기초부터 다뤄보는 Machine Learning / TensorFlow 101

|발표자|일시|
|---|---|
|권순선님 |2016-11-05 (토요일) |

많은 개발자들이 그렇겠지만, Machine Learning은 흥미롭게 생각하는 주제중에 하나다.   
전 회사에 머신러닝을 하시던 개발자님께(영민님) 간단하게 배웠었다.  
그때 배웠던것들이 초반 발표에서 나와서 "음.."하면서 듣고 있었다.   
하지만 수식이 나오기 시작하면서...."아..어..으..므.."  
세션에선 spervised Learning에 대해서 알려주셨는데, 그 안에서도 많은 방법이 있는데,   
그 중에서 Linear Regression에 대해서 알려주셨다.
간단하게 
1 = 1
2 = 2
3 = 3
5 = ?
컴퓨터가 이걸 맞추게 하는게 Machine Learning이다.
이 이후에 Cost Function에 대해서 나왔다. 
예측과 실제 값의 차이의 평균값인데 줄일수록 좋다. 이 값을 줄여나가야한다!!
결론 : TensorFlow를 이용해서 체험해보고 싶다.

## 안드로이드 개발에 유용한 도구들

|발표자|일시|
|---|---|
|안세원님 |2016-11-05 (토요일) |

### 도구 및 Tip

* Stetho
* LeakCanary
* HierarchyViewer
* Debugger Tip


#### Stetho : 종합선물세트

* 페이스북이 만든 선물세트
* 크롬 브라우저의 inspect UI를 이용해 각종 정보 조회
  * 네트워크 로깅
    * 헤더값 보려고 proxy 깔고 설정을 피할 수 있다.
    * json 눈 파싱을 피할 수 있다.
  * Sqlite DB SQL 실행 및 조회, 수정
    * 쿼리 날리려고...다른 도구를 열 필요가 없다.
    * 데이터 조작하려고 디버거 걸어두고 sql 불편하게 날리지 말자!
  * SharedPreference 조회/수정
    * 값 조회/조작 가능
  * 커스텀 동작 수행할 수 있는 dump plugin
    * 커스텀 정보 조회 / 수정 작업을 콘솔창에서 수행하자. 
  * UI
    * 편하게 볼 수 있다.
     

#### LeakCanary

* Sqaure 릭 탐지 도구
* GC 이후에 참조가 사라지지 않을 경우 메모리릭으로 판단함
  * GC가 안된 경우 메모리 릭  
  * FishBun에 적용됐지만 안사용했는데 사용해봐야겠다.
* 메모리 릭 탐지 결과는 notification으로 알려줌

#### HirarchyViewer

* SDK가 제공하는 뷰 선능 / 속성 조회 도구
* 렌더링 성능에 영향을 미치는 노드 정보 제공, 각 노드의 렌더링 결과 제공
* 실행
  * Device monitor window/ Open Perspective/ HirarchyViewer
  * 에뮬레이터나 루팅된 기기에서만 사용 가능
  * 4.0초과 에선 `export ANDROID_HVPROTO=ddm`
  * 안스 2.2에 Layout inspector
    * 아직은 레이아웃 스냅샷 기능밖에 없음

#### Debuugger Tip

* Evaluate expression(Alt + F8)
  * 실행 중단 지점에서 다양한 조작이 가능

* Conditional Breakpoint
  * 특정 조건을 만족할 경우에만 실행을 중단
  
* Breakpoint > Log message
  * 한두번 확인하고 말 용도의 로그메시지
  * Suspend 옵션은 꺼두자
    
## 오픈 소스를 통해 개발 근육 강화하기

|발표자|일시|
|---|---|
|서주영님 |2016-11-05 (토요일) |

오픈소스를 하면 많은것을 배울 수 있다. 커뮤니케이션 능력, 개발 능력, 영어...등   
하지만 나는 오픈소스를 좋아한다고 하면서 너무 나의 프로젝트에만 열심을 냈다.    
다른 개발자들과 소통하고, 영어 공부도 할겸..(?) 다른 오픈소스에도 기여해야겠다.   
결론적으로 구글에! 읭?

추천해주신것
* [개발자와 영어 : 박민우님](http://www.slideshare.net/tebica/developer-english-why-and-how)
* [머신러닝 강의 : 모두를 위한 머신러닝/딥러닝 강의](https://hunkim.github.io/ml/)