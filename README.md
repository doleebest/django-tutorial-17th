# 1주차 미션: Django 튜토리얼

## 스터디 자료
[1주차 : Django와 개발 환경 설정](https://motley-way-58c.notion.site/Django-67e5994dfebd429d882d4b2b0e58e6a0)

## 미션
- [Writing your first Django app](https://docs.djangoproject.com/ko/3.2/intro/tutorial01/)의 Part 1~4 따라합니다.
- 코딩의 단위를 기능별로 나누어 Commit 메세지를 작성합니다.
- 새롭게 알게 된 것을 정리합니다.

## 목표
- Django 의 MTV 패턴을 이해합니다.

## 기한
- 2023년 3월 25일 토요일  

## 오류 해결
 - development server at http://127.0.0.1:8000/admin 이 주소값을 가진 페이지를 열게 하려면 python manage.py runserver를 해주어야 함
 - q.was_published_recently() 가 실행이 안됨 -> 새로운 터미널을 열어서 cd ./mysite 한 후 python manage.py shell을 다시 실행 해서 오류 해결
 - cd ../ : 현재 파일에서 빠져나와서 이전 파일로 나가는 명령어


## [part 1]
0) 깨달은 점
  다음부터는 part별로 commit 및 내용 정리를 해야겠다..
   +) feedback ; 파트별 커밋보다는 작업 단위 별로 커밋하는게 더 좋을 것 같아요~~! 특히 협업 시에는 커밋 메시지 컨벤션을 정하면 더더 좋답니다! 아래 링크 참고해주세요😇

https://overcome-the-limits.tistory.com/entry/%ED%98%91%EC%97%85-%ED%98%91%EC%97%85%EC%9D%84-%EC%9C%84%ED%95%9C-%EA%B8%B0%EB%B3%B8%EC%A0%81%EC%9D%B8-git-%EC%BB%A4%EB%B0%8B%EC%BB%A8%EB%B2%A4%EC%85%98-%EC%84%A4%EC%A0%95%ED%95%98%EA%B8%B0

+) feedback2 ; 클래스 간에는 두 줄 엔터, 함수와는 한 줄 엔터 띄우는게 원칙이에요!
파이참이 제공하는 Reformat the file 기능을 적극 활용해서 줄바꿈 해주면 가독성이 더 좋아질 것 같네용

+) 인덴트가 깔끔하게 정리되어있었음 좋겠어요..! 쓰는 언어가 파이썬인만큼 인덴트에 민감해야 한다고 생각합니다!

... 전반적인 feedback은 코드 정렬(들여쓰기)이나 다른 협업하는 팀원들이 보기에 좋게 만드는 것과 관련이 있었다.
좀 더 꼼꼼하게 살펴보며 코드를 작성해야겠다.



1) Django는 파이썬 기반이다.

2) 오류 해결한 것
   q.was_published_recently() 가 실행이 안됨 : 새로운 터미널을 열어서 cd ./mysite 한 후 python manage.py shell을 다시 실행 해서 오류 해결
   cd ../ : 현재 파일에서 빠져나와서 이전 파일로 나가는 명령어

3) HTTP
 : 컴퓨터들끼리 HTML파일을 주고받을 수 있도록 하는 소통방식 또는 약속(protocol)이다.
  클라이언트는 서버에게 request를, 서버는 response를 클라이언트에게 보낸다.

4) 가상환경에서 작업들을 수행한다.

5) No module named django : 장고 라이브러리가 설치가 안되어있음
   따라서 가상환경 구동(myenv), 장고 라이브러리 구축 해야함 
  
6) mysite라는 프로젝트 생성 (중요 : url&setting)
manage.py: Django 프로젝트와 다양한 방법으로 상호작용 하는 커맨드라인의 유틸리티 입니다. manage.py 에 대한 자세한 정보는 django-admin and manage.py 에서 확인할 수 있습니다.  
mysite/ 디렉토리 내부에는 프로젝트를 위한 실제 Python 패키지들이 저장됩니다. 이 디렉토리 내의 이름을 이용하여, (mysite.urls 와 같은 식으로) 프로젝트의 어디서나 Python 패키지들을 임포트할 수 있습니다.  
mysite/__init__.py: Python으로 하여금 이 디렉토리를 패키지처럼 다루라고 알려주는 용도의 단순한 빈 파일입니다. Python 초심자라면, Python 공식 홈페이지의 패키지를 읽어보세요.  
mysite/settings.py: 현재 Django 프로젝트의 환경 및 구성을 저장합니다. Django settings에서 환경 설정이 어떻게 동작하는지 확인할 수 있습니다.  
mysite/urls.py: 현재 Django project 의 URL 선언을 저장합니다. Django 로 작성된 사이트의 《목차》 라고 할 수 있습니다. URL dispatcher 에서 URL 에 대한 자세한 내용을 읽어보세요.  
mysite/asgi.py: An entry-point for ASGI-compatible web servers to serve your project. See ASGI를 사용하여 배포하는 방법 for more details.  
mysite/wsgi.py: 현재 프로젝트를 서비스하기 위한 WSGI 호환 웹 서버의 진입점입니다. WSGI를 사용하여 배포하는 방법를 읽어보세요.    

7) client가 web server에 요청 -> web server(nginx, apache)가 요청을 merge -> wsgi(web server와 장고 프레임웍을 연결)    
-> request(client가 요청한 주소)가 url 파일에서 잘게 나누어짐(=파싱) ->view.py 데베작업 -> template(디자인 작업) -> 사용자가 response 받음   
-> wsgi -> client가 화면을 볼 수 있음    

8) mysite 레포지토리에서 server를 run해야 함 (2번에 오류 해결 방법과 연관)  

9) 프로젝트 vs 앱 : 앱은 기능들 / 앱(웹 app)을 한 곳에 묶어 놓은 것이 프로젝트  

10) URLconf 개념 : 장고에서 URL과 일치하는 뷰를 찾기 위한 패턴들의 집합  

11) parsing : 구문분석 / 문장이 이라고 있는 구성 성분을 분해하고 분해된 성분의 위계 관계를 분석하여 구조를 결정  

12) include() : 다른 URLconf를 참조할 수 있도록 도와줌  
     최상위 URLconf에서  
     url를 파싱해서 polls를 잡아내고 polls url로 연결시켜줌.   
     url.py polls 에서는 view 파일로 연결시켜줌  
     view 내부 index 함수에서는 "hello world"라는 response를 client에게 전달  
     (url.py 와 view.py (polls 내) 그리고 url.py(mysite 내) 파일은 모두 연결된것!)  


[part2]  

13) 다른 데이터베이스를 사용해보고 싶다면 setting.py 파일의 
database를 변경해주면 됨.  

14) python manage.py migrate : 데이터베이스 테이블을 생성하는 명령어  

15) 모델 만들기 : Question - 질문, 발행일 필드 / Choice - 선택지, 표 필드   

16)  .Foreignkey(참조하려는 필드, ~) : '참조하려는 필드'를 참조하는 외래키    

* 17) Choice 클래스에 있는 하나의 question에 여러개의 choice를 갖는 구조이기 때문에 일대다 관계 (?)    

18) 앱을 현재의 프로젝트에 포함시키기 위해서는 앱의 구성 클래스에 대한 참고를 INSTALLED_APPS 에 추가해야한다. ->  이 부분에서 제대로 추가(복붙)를 안해서 runserver가 실행되지 않는 오류가 났었다.. OMG  

 즉, polls.py에 있는 config 앱을 model.py에 등록을 하겠다는 의미  

 

19) makemigration : migration이라는 장소에 모델들을 데이터베이스 내에 테이블을 생성할 수 있도록  

설계도를 만드는 작업을 하는 것 -> migration 내에 파일이 생성됨    0001_initial.py에 필드 생성  

 

20) API 가지고 놀기 : API란 개발자가 필요로 하는 데이터를 뽑을 수 있도록 만들어 놓은 함수 또는 서버에게 데이터를 뽑아낼 수 있도록 만들어놓은 함수  

 

21) Question.object.all() : 현재 Question 내 모든 명령어를 가져와라  

 

22) __str__() : <Question: Question object (1)>은 이 객체를 표현하는 데 별로 도움이 되지 않는다. (polls/models.py 파일의) Question 모델을 수정하여, __str__() 메소드를 Question과 Choice에 추가해본다. cmd에서 편하게 볼 수도 있고 사이트에서 객체의 표현 방식을 바꿀 수도 있다.  

 

23) admin : 장고에서 제공하는 아주 편한 기능! 관리자가 관리할 수 있는 페이지. 거의 모든 웹 어플리케이션에 존재  

admin 화면에서 새로운 질문 등록 등 새로운 데이터 등록 가능  

 

[part3]  

24) view : 앱의 로직 담당. 데이터 저장, 파일 다운로드 등을 처리하는 용도 쓰임.  

25) 다음과 같은 페이지를 view에 코드 작성하여 생성  
  
질문 《색인》 페이지 – 최근의 질문들을 표시합니다.
질문 《세부》 페이지 – 질문 내용과, 투표할 수 있는 서식을 표시합니다.
질문 《결과》 페이지 – 특정 질문에 대한 결과를 표시합니다
투표 기능 – 특정 질문에 대해 특정 선택을 할 수 있는 투표 기능을 제공합니다.  

  26) </polls/34/>를 요청 -> mysite.urls 파이썬 모듈을 불러옴 -> urlpatterns 라는 변수를 찾고 순서대로 패턴을 따라감  
-> polls/ 를 찾음 -> 일치하는 텍스트 /polls 를 버리고 남은 텍스트인 34/를 polls.urls URLconf로 전달 ->detail() 뷰 함수 호출  


27) 404 에러 일으키기 : 뷰가 요청된 질문의 id가 없을 경우 발생시키는 에러, 즉 객체가 존재하지 않을때  

 

[part4]  

제네릭 뷰는 URL에서 전달 된 매개 변수에 따라 데이터베이스에서 데이터를 가져 오는 것과 템플릿을 로드하고 렌더링 된 템플릿을 리턴하는 기본 웹 개발의 일반적인 경우를 나타냅니다.   

제너릭 뷰는 일반적인 패턴을 추상화하여 앱을 작성하기 위해 Python 코드를 작성하지 않아도됩니다  

: URLconf를 변환 -> 불필요한 오래된보기 중 일부를 삭제 -> Django의 제너릭 뷰를 기반으로 새로운 뷰를 도입하십시오.  

 
