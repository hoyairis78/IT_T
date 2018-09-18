# CORS��

Cross Origin Resource Sharing �� ���� CORS �� ���� �˾ƺ���.
CORS�� Cross site Http Request�� �����ϰ� ���ִ� ǥ�� �Ծ��̴�.


�ٸ� �����ο��� �������� ���ҽ��� �ʿ��� ��, ������ ���Ȼ��� ������ �ڽŰ� ������ ���������θ� HTTp request�� ������ ������ �س���. XMLHttpRequest�� ũ�ν��������� ��û�� �� �ְ� �ϴ� ���� CORS�̴�.

���� �Ҹ��ĸ� Ÿ �����ο��� �±�`<>`���� ������ ��, <script></script> �±׸� ������ Cross site http requeste�� ��������, ȣ��Ʈ��, ��Ʈ�� ���ƾ� ������ ����. �׷����� ajax�� ���ٺ��� �̰� ���Ҽ��� ���� �׶� CORS��û�̶�� ����� ����Ѵ�.

CORSsms 4���� �������� �̷���� �ְ� �� �� ������ �´� ����� �����ϸ� �ȴ�.


## Simple Request

- GET, HEAD, POST�� �ϳ�
- POST�� Content-Type�� �Ʒ� �� �� �ϳ�
	v application/x-www-form-urlencoded
	v multipart/form-data
	v text/plain
- Ŀ���� ����� �������� ����

������ 1�� ��û�ϰ� ������ 1�� ȸ���� ó�� �����

request����

```
GET /resources/public-data/ HTTP/1.1

Host: bar.other

User-Agent: Mozilla/5.0 (Macintosh; U; Intel Mac OS X 10.5; en-US; rv:1. 9.1b3pre) Gecko/20081130 Minefield/3.1b3pre

Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8

Accept-Language: en-us,en;q=0.5

Accept-Encoding: gzip,deflate

Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7

Connection: keep-alive

Referer: http://foo.example/examples/access-control/simpleXSInvocation.html

Origin: http://foo.example
```

response����

```

HTTP/1.1 200 OK

Date: Mon, 01 Dec 2008 00:23:53 GMT

Server: Apache/2.0.61 

Access-Control-Allow-Origin: *

Keep-Alive: timeout=2, max=100

Connection: Keep-Alive

Transfer-Encoding: chunked

Content-Type: application/xml

```

foo.example ����Ʈ���� bar.other�� ��û�� ������ �ǰ��ִµ� 
Access-Control-Allow-Origin: * ���� ǥ�õǾ� �ִ�. bar.other�� cross-stie��� ��� ���������κ��� ������ �����ϴٴ� ���̴�.


## Preflight Request


![](http://wiki.gurubee.net/download/attachments/28607117/cors_flow.png)

Simple Request�� �ƴ� �� �ش�. ���� ��û�� �� ��û���� �����µ� ó���� �����û�� ������ ������ ������ ����û�� ������.

�׷����� �����ڰ� ���� �������� �ʰ� `Access-Control-`����� �����ָ� options��û���� ���� ���� ��û�� GET,POST������ ���� �� ��û�� ������ �˾Ƽ� ó���Ѵ�.

�� �����û, ��������, ����û, ���������� �̷���.

request ����

```
OPTIONS /resources/post-here/ HTTP/1.1

Host: bar.other

User-Agent: Mozilla/5.0 (Macintosh; U; Intel Mac OS X 10.5; en-US; rv:1.9.1b3pre) Gecko/20081130 Minefield/3.1b3pre

Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8

Accept-Language: en-us,en;q=0.5

Accept-Encoding: gzip,deflate

Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7

Connection: keep-alive

Origin: http://foo.example

Access-Control-Request-Method: POST

Access-Control-Request-Headers: X-PINGOTHER
```

response ����

```

HTTP/1.1 200 OK

Date: Mon, 01 Dec 2008 01:15:39 GMT

Server: Apache/2.0.61 (Unix)

Access-Control-Allow-Origin: http://foo.example

Access-Control-Allow-Methods: POST, GET, OPTIONS

Access-Control-Allow-Headers: X-PINGOTHER

Access-Control-Max-Age: 1728000

Vary: Accept-Encoding, Origin

Content-Encoding: gzip

Content-Length: 0

Keep-Alive: timeout=2, max=100

Connection: Keep-Alive

Content-Type: text/plain
```

�����û�� `OPTIONS /resources/post-here/ HTTP/1.1` �� �������� `Access-Control-Request-Method: POST`�� ���� ����û������ POST�� ���.

����� ���� X-PINGOTHER��� Ŀ���� ����� �̷� ������ ������ �ִ�. `Access-Control-Request-Headers: X-PINGOTHER`

���������� �°� ����

```
Access-Control-Allow-Origin: http://foo.example

Access-Control-Allow-Methods: POST, GET, OPTIONS

Access-Control-Allow-Headers: X-PINGOTHER
```

�� �� Access-Control-Allow-�� �����Ѵ�. ���� ����û�� ������ ����ȴ�.


## Credential request

HTTP Cookie�� Authentication������ �ν��� �� �ְ� ���ִ� ��û�̴�.
��û�� `xhr.withCredentials =true`������ ������ �Ǵµ� Response Header�� �� `Access-Control_Allow-Credentials : true`�� ���ԵǾ�� �Ѵ�.

�׸��� ����� `Access-Control-Allow-Origin`���� *�� �ƹ��ų� �� �����̸� �ȵǰ� ������ �̸��� ��õǾ�� �Ѵ�.

���� `Credentials : true`�س��� `Access-Control-Allow-Origin : *`�س����� ��������.

false�� �س����� ��û�� �źεż� ���������� ����.

## Non Credential request

`withCredentails : false` �� ����Ʈ���̶� Credential��û�� ������ �� ���� ���� ��ø� ����� �Ѵ�.


---

���

- Ajax���� Same Origin Policy��� ��Ģ�� ����
- ���� �������� �������� �ִ� HTML�� ������ ������(Origin- ���ϵ�����,����port,������������)���Ը� Ajax ��û�� ���� �� ����
- CORS�� �� ������ �������������� �ٸ� �����ΰ� ����� �Ұ���
- ��ȸ ������� JSONP, IFRAME IO, CrossDomain Proxy ���� ��ȵ� (Get�� ��� �� �������, ����ȣ��ȵ� �� ��������)
- HTML5 ���� �ٸ� ������ �� ����� ������ ������ �߰��Ǿ��µ� �װ� CORS
- 4���� ����� �����Ƿ� ��󾲸� ��