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
