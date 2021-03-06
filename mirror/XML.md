## Contents

    

1. 개요 
2. Well-formed 문서와 유효 XML문서 
3. XML 파서의 종류 
4. XML 로 된 이상한 거 엄청 많던데? 
5. 기타 

[[edit](http://rigvedawiki.net/r1/wiki.php/XML?action=edit&section=1)]

## 1. 개요 ¶

eXtensible Markup Language의 약어. W3C에서 여러 특수 목적의 마크업 언어를 만드는 용도에서 권장되는 다목적 마크업
언어이다. 첨언하자면 마크업 언어는 태그 등을 이용하여 데이터의 구조를 기술하는 언어의 한 가지이다. 가장 친숙하고 흔하게 접할 수 있는
마크업 언어로 [HTML](HTML.md)이 있다.

  

1996년 제안된 언어로, 기존의 HTML과 달리 웹상에서 구조화된 문서를 전송가능하도록 설계되었다. 이게 무슨 뜻이냐면 예를 들어
HTML에서 **CPU 2.83GHz**라는 데이터를 표기할 때 어디부터가 데이터 명이고 어디부터가 실제 데이터인지 표시할 수 있는 마땅한
방법이 없다.

  

이런 문제를 해결하기 위해 XML을 이용하면 어디부터 어디까지가 데이터 이름이고 어디부터 어디까지가 실제 데이터이며 어디부터 어디까지가
데이터 단위인지도 표현이 가능하다. 즉, 데이터에 의미를 부여하는
[메타데이터](%EB%A9%94%ED%83%80%EB%8D%B0%EC%9D%B4%ED%84%B0.md)를 기술할 수 있다. XML은
바로 이러한 목적으로 탄생했다. 위의 예를 XML로 바꾸면 데이터 명은 CPU가 되고 데이터 값은 2.83이 된다.

  

원래 동일한 목적을 가진 Standard Generalized Markup Language(SGML) 라는 것이 인터넷 등장보다 빠른
1980년대에 등장했으며, 이것의 Profile(부분집합)에 인터넷 환경과 새롭게 변화해온 컴퓨팅 환경에 맞게 확장을 더한 것이 바로 XML
이다. XML은 바로 SGML의 파생형이라고 할 수 있으며, [HTML](HTML.md)은 완전한 파생형은 아니지만 SGML의 영향을
강하게 받았다고 최초 제안자인 Tim Berners-Lee가 밝힌 적이 있다.

  

이런 XML의 특징은 수많은 종류의 데이터를 유연하고 자유롭게 기술하는 데 적용할 수 있어서 다양한 용도로 응용할 수 있으며, 인터넷으로
연결된 시스템끼리 쉽게 식별 가능한 데이터를 주고받을 수 있게 된다. 게임 모드 등을 시도해 봤다면 설정파일이 XML로 된 것을 본 경험이
있을 것이다.

  

[[edit](http://rigvedawiki.net/r1/wiki.php/XML?action=edit&section=2)]

## 2. Well-formed 문서와 유효 XML문서 ¶

  * Well-formed : XML의 기본 문법을 만족하는 수준으로 되어있는 문서. 모든 구문을 허용하기 때문에 XML처럼 보이기는 하지만 실제로 데이터 교환수단으로 바로 쓰기는 어렵다. 형식이 제각각이기 때문.
  * 유효(Valid) XML 문서 : XML 문서의 형식([DTD](DTD.md), XML Schema)를 만족하도록 작성된 XML 문서. 문서의 형식 정의는 XML 문서 자체에 포함되었을 수도, 다른 문서로 존재할 수도, 아니면 다른 컴퓨터에 존재할 수도 있다. 문서 형식 정의는 과거에는 [DTD](DTD.md)가 많이 사용되었지만, 2000년대 중후반 이후 XML Schema를 주로 사용한다..  

[[edit](http://rigvedawiki.net/r1/wiki.php/XML?action=edit&section=3)]

## 3. XML 파서의 종류 ¶

둘 다 모두 실제 구현체가 아닌 인터페이스 수준으로 느슨하게 정의되어 있다. 그래서 프로그래밍 언어/플랫폼 별로 실제 사용 방법이 조금씩
다를 수 있다. XML이 초기에 널리 퍼진 이유 중 하나는, 거의 웬만한 언어에서 기본으로 지원하는 구조화된 데이터를 읽는 기본 API 보다
훨씬 복잡한 형태의 구조화된 데이터를 읽고 쓰는데 매우 편리했기 때문이다. 지금은 웹 관련 한정으로 [JSON](JSON.md)이 더
많이 쓰이고 있다.

  

  * DOM : XML 문서가 전부 메모리로 올라가 객체 모델로 생성된다. W3C의 공식 표준이며, W3C가 표준화한 API들의 기반이다. 문서가 통째로 메모리에 올라가 조직화되기 때문에 문서 요소를 임의적으로 접근하고 사용하는데 적합하다. 그러나 이는 반대로 단점이 되기도 하는데, 논리 구조를 통으로 메모리에 올려놓고 연산하기 때문에 XML 데이터의 양이 크면 메모리 부족으로 인해 고생하게 된다.
  * SAX : XML 문서를 애플리케이션에서 사용하기 위한 API. DOM에 비해 저수준의 인터페이스를 가지고 있으며 처리해야 할 파일이 클 때 적합하다. XML의 구조에 따라 이벤트가 발생되며, 프로그래머는 이 이벤트를 처리하는 이벤트 핸들러를 작성하여 필요한 데이터를 추출할 수 있다. 그렇기 때문에 데이터 내용을 조직하는 기능은 DOM만 못하다. 아무래도 XML 문서를 통으로 메모리상에 논리 구조를 유지하면서 올리고 작업할 수 없기 때문. 그러나 이러한 이벤트 기반 처리 방식은 역시 읽어서 처리해야 하는 XML 데이터가 매우 클 때 장점으로 작용한다. 일단 어떻게든 다른 대용량 비휘발성 저장공간([데이터베이스](%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4.md), NoSQL 등)에 입력하는데 SAX를 쓰고, 데이터 조작은 해당 저장공간에서 하면 되기 때문이다.  

[[edit](http://rigvedawiki.net/r1/wiki.php/XML?action=edit&section=4)]

## 4. XML 로 된 이상한 거 엄청 많던데? ¶

XML은 어디까지나 구조를 가지면서
[메타데이터](%EB%A9%94%ED%83%80%EB%8D%B0%EC%9D%B4%ED%84%B0.md)를 기술할 수 있는 다목적 문서
형식 표준이다. 이를 원하는 용도에 맞게 [DTD](DTD.md), XML Schema를 작성하고 표준으로 제정하면 XML에 기반한
특수 목적용 마크업 언어가 된다. (무리가 있는 비유지만) XML과 XML을 사용하는 다른 마크업 언어는 마치 한국어와 한국어로 씌여진 시,
소설, 수필, 학술논문, 영화대본, 신문기사 등과 유사한 관계라고 할 수 있다.

  

누구나 알 수 있는 이러한 것의 대표적인 예로 초기의 [RSS](RSS.md)를 들 수 있다. 처음엔 이름이 RDF Site
Summary 였으나, 나중에 Rich Site Summary 로 변경되면서 XML 형식도 약간 변경이 되었는데, 이는 초기버젼이
Resource Description Framework(RDF)라는 XML 기반의 의미 정보를 엄격하게 기술하는 마크업 언어로 되어있었기
때문이다.

  

그 밖에 [자바](%EC%9E%90%EB%B0%94.md)로 웹 어플리케이션을 작성해 본 사람이면 web.xml 설정파일이 친숙할텐데,
이것도 Oracle(과거 Sun Microsystems)에서 XML Schema로 형식을 규정한 JSP/Servlet Web
Application 표준 설정 파일이다.

  

[[edit](http://rigvedawiki.net/r1/wiki.php/XML?action=edit&section=5)]

## 5. 기타 ¶

원래는 웹에서 사용할 목적으로 만들었는데, 웹환경이 아닌 일반 TCP/IP 네트웍 통신을 할 때에도 점점 사용빈도가 늘어나고 있는 추세이다.
디지털 기반의 네트워크 통신을 할 때 발신자와 수신자간에서는 서로 주고받는 데이터 패킷을 비트 단위로 정확하게 맞춰줘야 문제가 생기지
않는데, 이 비트단위 데이터 통신에 하도 불확실성이 많아서...<del>가장 큰 불확실성은 사람이 만든 버그</del> 또한 데이터 패킷단위
전송시 응용어플리케이션의 개발기반, 구동 환경에 따라 이런저런 잔처리가 많이 들어간다.`[1]`

  

그래서 요즘은 아예 XML로 데이터를 주고받는다. 이렇게 하면 최소한 패킷 사이즈가 안 맞아서 발생하는 버그는 줄일 수 있다. 그리고 이렇게
만든 프로그램은 XML로 데이터를 주고받기 때문에 웹확장성도 덤으로 갖게된다.

  

다른 컴퓨터 사이에 정보를 주고 받는 웹 서비스는 서버에 데이터를 요청하면 기본적으로 결과가 XML로 리턴이 된다. 구글맵
[API](API.md)의 경우도 XML로 데이터를 전달받을 수 있다. 아래 링크를 클릭하면 구경해볼 수 있다.

  
[구글맵 쿼리 테스트](http://maps.googleapis.com/maps/api/directions/xml?origin=Chicago
,IL&destination=Los+Angeles,CA&waypoints=Joplin,MO%7COklahoma+City,OK&sensor=f
alse)  

  

이러한 것이 아닌, 요청과 응답을 XML에 기반하여 제정된 표준으로 XML-RPC와 SOAP이라는 프로토콜이 존재한다. 처음에는 인터넷
상에서 사용할 것을 목적으로 만들었지만, 운용하는데 생각보다 까다롭고 부담이 많이 되기 때문에 지금은 기업 환경이 아니면 보기 힘들다. 기업
환경에서는 오버헤드를 감수하더라도 시스템간 정확하고 엄격한 데이터 교환이 이루어져야 하기 때문이다.

  

다만 [자바스크립트](%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8.md)에서는
여러 모로 취급이 불편하고, **실제 데이터 양에 비해서 [크고아름다운](%ED%81%AC%EA%B3%A0%20%EC%95%84%EB%A6%84%EB%8B%A4%EC%9A%B4.md) 덩치를
자랑하기 때문에**`[2]` [JSON](JSON.md)이라는 포맷을 따로 만들었을 정도. 단 이것은 웹 브라우저와 직결되는 환경
한정이다. 애초에
[자바스크립트](%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8.md) 사용 빈도
자체가 웹 브라우저 상에서 사용되는 경우가 가장 많으니까.

  

그러나 이러한 장점이 있는 대신, XML이나 JSON은 공통된 단점이 있으니, 기본적으로 둘 다 문자열에 기반한 것이고, 실 데이터에 비해
오버헤드가 많으며, 메모리 상에 들어있던 데이터를 XML이나 JSON으로 변환하여 전송하고, 다시 이렇게 전송받은 XML 이나 JSON
데이터를 메모리에 복원시키는 오버헤드가 크다.

  

어쩌다 한 번 이러한 방식으로 동작하는 프로그램을 운용하는 경우에는 별 문제가 없지만, 1초에도 수십 번 이상 이러한 요청을 받아서 처리하여
결과를 돌려주는 서비스를 운용할 때에는 꽤 문제가 되며, IBM 같은 곳에서는 이러한 변환 작업용 전용 가속 장비를 제작하여 기업용으로
판매할 정도이다. 어떻게든 이러한 문제점을 극복해 보고자 아예 Efficient XML Interchange(EXI)라고 하는 Binary
XML 까지 등장했다.

`\----`

  * `[1]` 예를 들어, 자바와 C++로 만든 프로그램이 통신한다고 할 때 양자간 기본 데이터 크기와 형식이 달라서 글자 그대로 패킷을 바이트 단위로 쪼개서 주고 받아야 한다.
  * `[2]` XML 선언 헤더, HTML 방식의 열고 닫는 태그 구조, 엔티티 이스케이핑(예를 들면 &를 &amp;로 적어야 한다든지) 등등이 덩치를 키우는 데 일조했다.

