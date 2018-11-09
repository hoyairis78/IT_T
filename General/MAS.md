# MSA��

MicroService Architecture �� ���� 
������ ���� ������ ���� �ý���(Monolitic)�� ���� ������ ������ �и��ϴ� ������ ��Ű��ó

# Context
You are developing a server-side enterprise application. 
It must support a variety of different clients including desktop browsers, mobile browsers and native mobile applications. 
The application might also expose an API for 3rd parties to consume. 
It might also integrate with other applications via either web services or a message broker. 
The application handles requests (HTTP requests and messages) by executing business logic; accessing a database; exchanging messages with other systems; 
and returning a HTML/JSON/XML response. 
There are logical components corresponding to different functional areas of the application.

# Problem
What��s the application��s deployment architecture?

  
  Forces
	* There is a team of developers working on the application
	* New team members must quickly become productive
	* The application must be easy to understand and modify
	* You want to practice continuous deployment of the application
	* You must run multiple copies of the application on multiple machines in order to satisfy scalability and availability requirements
	* You want to take advantage of emerging technologies (frameworks, programming languages, etc)

���� : https://microservices.io/patterns/microservices.html


11���� Spring Cloud ��� MSA���� ��ȯ - ���� 1�Ⱓ�� �̾߱�

  https://readme.skplanet.com/?p=13933
