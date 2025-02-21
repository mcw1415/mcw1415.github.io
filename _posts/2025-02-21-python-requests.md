---
title: Python requests란?
date: 2025-02-21 16:30:00 +0900
categories: [Python]
tags: [python, requests, crawling, module, 파이썬, 크롤링, 모듈]     # TAG names should always be lowercase
use_math: true
mermaid: true
---

## **HTTP란?**

`requests` 모듈을 설명하기에 앞서, HTTP(HyperText Transfer Protocol)에 대한 약간의 이해가 필요하다. HTTP는 클라이언트(서버와 통신하는 모든 프로그램) 와 서버 간 데이터 전송을 가능하게 해주는 규칙이다.

> HTTP에서는 `GET`, `POST`, `PUT`, `DELETE`, `PATCH` 메소드를 지원한다.

## **requests란?**
  
`requests` 모듈은 **Python에서 HTTP 요청을 쉽게 보내주는 라이브러리**이다. 쉽게 말해 Python 코드로 서버에 요청을 보내고 응답받을 수 있다는 것이다. 보통 크롤링을 위해서 많이 사용된다.

### **requests Method**

> `pip install requests #패키지 매니저(pip)로 다운받으면 된다.`

`GET`, `POST`, `PUT`, `DELETE`, `PATCH` 메소드로 반환되는 형태는 `Object Type`이고, **응답 객체**라고 한다. 응답에 대한 HTTP 상태 코드, 본문, 메타데이터 등의 정보를 포함하고 있다.

1. **`GET` 요청**
	```python
	#데이터 조회
	url = "https://~~~~"
	response = requests.get(url)
	```
2. **`POST` 요청**
	```python
	#새 데이터 생성
	url = "https://~~~~/post"
	data = "title=Python requests란?&body=blabla" #key=value&key2=value2
	response = requests.post(url, data=data, headers={"Content-Type": "application/x-www-form-urlencoded"})
	```		
	> `"Content-Type": "application/x-www-form-urlencoded"`  
	:  **HTML 폼 데이터를 서버로 전송할 때 사용되는 기본 인코딩 방식**
	
3. **`PUT` 요청**
	```python
	#전체 데이터 수정 
	url = "https://~~~~/post/1"
	data = "title=Updated Python requests란?&body=Update blabla"
	response = requests.put(url, data=data, headers={"Content-Type": "application/x-www-form-urlencoded"})
	```
4. **`PATCH` 요청**
	```python
	#일부 데이터 수정 
	url = "https://~~~~/post/1"
	data = "title=Updated2 Python requests란?"
	response = requests.patch(url, data=data, headers={"Content-Type": "application/x-www-form-urlencoded"})
	```
5. **`DELETE` 요청**
	```python
	#1번 포스트 삭제
	url = "https://~~~~/post/1"
	response = requests.delete(url)
	```
	

### **응답 객체 속성**

| 속성                  | 설명                    | 추가 설명 |
|----------------------|------------------------|------------------------------|
| `response.status_code` | **HTTP 상태 코드**     | `200(OK)`, `404(Not Found)`, `500(Internal Server Error)` |
| `response.text`        | **응답 데이터 본문**   | HTML, JSON 등의 데이터 구조 |
| `response.headers`     | **응답 메타데이터**     | `{ 'Content-Type': 'application/json', 'Server': 'nginx' }` |
  
## **회고**
가볍게 넘긴 개념들에 대해서는 따로 포스트 업로드를 해야겠다.



