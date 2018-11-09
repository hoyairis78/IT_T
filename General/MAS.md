# MSA란

MicroService Architecture 의 약자 
기존의 통합 관점의 단일 시스템(Monolitic)을 서비스 단위로 나누고 분리하는 개념의 아키텍처

# Context
You are developing a server-side enterprise application. 
It must support a variety of different clients including desktop browsers, mobile browsers and native mobile applications. 
The application might also expose an API for 3rd parties to consume. 
It might also integrate with other applications via either web services or a message broker. 
The application handles requests (HTTP requests and messages) by executing business logic; accessing a database; exchanging messages with other systems; 
and returning a HTML/JSON/XML response. 
There are logical components corresponding to different functional areas of the application.

# Problem
What’s the application’s deployment architecture?

  
  Forces
	* There is a team of developers working on the application
	* New team members must quickly become productive
	* The application must be easy to understand and modify
	* You want to practice continuous deployment of the application
	* You must run multiple copies of the application on multiple machines in order to satisfy scalability and availability requirements
	* You want to take advantage of emerging technologies (frameworks, programming languages, etc)

원본 : https://microservices.io/patterns/microservices.html


11번가 Spring Cloud 기반 MSA로의 전환 - 지난 1년간의 이야기

  https://readme.skplanet.com/?p=13933
