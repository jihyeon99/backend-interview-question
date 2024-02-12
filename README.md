## Table Of Contents

- [이 저장소를 잘 사용하기 위한 팁](#이-저장소를-잘-사용하기-위한-팁)
- [CS 관련 지식](#CS-관련-지식)
- [언어 관련](#언어-관련)
- [기타](#기타)
- [면접 꿀팁](#면접-꿀팁)


## 이 저장소를 잘 사용하기 위한 팁

문제를 보고 음성메모로 답을 해봅시다. 그리고 음성메모를 들으면서 자신이 알고있는 것이 잘 전달되는지 확인합시다.

문제에 대한 내용에 대한 답변은 상당히 간추린 내용이기 때문에, 누락되거나 불필요하다 판단하여 덜어낸 부분이 존재할 수 있습니다. 그리고 정답이라고 할만한 것이 존재하지 않는 문제도 존재하기 때문에 '이 사람은 이렇게 답변했겠구나' 정도로 받아들이시는 것을 권장합니다.

예제 답변 그대로 답변하면 좋겠지만, 최대한 짧고 간결하게 대답해야만 면접자 입장에서 좀 더 유리합니다. 궁금하면 면접관님께서 꼬리질문으로 깊이있게 물어보실 것입니다.

추가로 아래 내용에 보충을 하고싶다면, issue 혹은 PR로 기여를 해주세요. 저도 초보 개발자이기 때문에 틀리거나, 잘못된 내용이 있을 수 있습니다.

모의 면접을 도와줄 지인이 있다면 모의면접을 부탁해서 실제 면접처럼 수행하면 더욱 실전에서 도움이 될 것 같습니다.

이 주제들을 가지고 학습을 하는 것도 도움이 많이 될 것입니다.


## CS 관련 지식 :black_square_button: :white_check_mark: 

### 네트워크

<details>
  <summary>:black_square_button: 웹 통신의 큰 흐름: https://www&#46;google&#46;com/ 을 접속할 때 일어나는 일</summary>
  </br>
  <p>면접 단골 문제입니다. 면접관 입장에서는 한 질문으로 많은 답변을 들을 수 있기 때문에 대부분의 면접자리에서 나왔던 문제입니다. OSI 7계층과도 연관지어 설명하라는 질문을 받은적도 있습니다.</p>
  <p>브라우저가 URL에 적힌 값을 파싱해서 HTTP Request Message를 만들고, OS에 전송 요청을 합니다. 이 때, Domain으로 요청을 보낼 수 없기 때문에 DNS Lookup을 수행합니다.</p>
  <p>DNS 룩업 과정은 크롬의 경우 브라우저 → hosts 파일 → DNS Cache의 순서로 도메인에 매칭되는 ip를 찾습니다. 일반적으로 설명하는 DNS Lookup은 루트 도메인서버에서부터 서브도메인 서버순으로 찾게됩니다.</p>
  <p>이 요청은 프로토콜 스택이라는 OS에 내장된 네트워크 제어용 소프트웨어에 의해 패킷에 담기고 패킷에 제어정보를 덧붙여 LAN 어댑터에 전송하고, LAN 어댑터는 이를 전기신호로 변환시켜 송출합니다.</p>
  <p>패킷은 스위칭 허브 등을 경유하여 인터넷 접속용 라우터에서 ISP로 전달되고 인터넷으로 이동합니다.</br>
액세스 회선에 의해 통신사용 라우터로 운반되고 인터넷의 핵심부로 전달됩니다. 고속 라우터들 사이로 목적지까지 패킷이 흘러들어가게 됩니다.</p>
  <p>핵심부를 통과한 패킷은 목적지의 LAN에 도착하고, 방화벽이 패킷을 검사한 후 캐시 서버로 보내어 웹 서버에 갈 필요가 있는지 검사합니다.</p>
  <p>웹 서버에 도착한 패킷은 프로토콜 스택이 패킷을 추출하여 메시지를 복원하고 웹 서버 애플리케이션에 넘깁니다. 애플리케이션은 요청에 대한 응답 데이터를 작성하여 클라이언트로 회송하고, 이는 전달된 방식 그대로 전송됩니다.</p>
</details>

<details>
  <summary>:black_square_button: TCP와 UDP의 차이점에 대해서 설명해보세요.</summary>
  </br>
  <p>TCP는 연결 지향형 프로토콜이고 UDP는 데이터를 데이터그램단위로 전송하는 프로토콜입니다.</p>
  <p>TCP는 가상 회선을 만들어 신뢰성을 보장하도록(흐름 제어, 혼잡 제어, 오류 제어) 하는 프로토콜로 따로 신뢰성을 보장하기 위한 절차가 없는 UDP에 비해 속도가 느린편입니다.</p>
  <p>TCP는 그래서 파일전송과 같은 신뢰성이 중요한 서비스에 사용되고, UDP는 스트리밍, RTP와 같이 연속성이 더 중요한 서비스에 사용됩니다.</p>
  <p>+) 하지만 UDP도 신뢰성을 UDP자체에서 보장하지 않는 것 뿐이지, 개발자가 직접 신뢰성을 보장하도록 할 수 있습니다. 그래서 HTTP/3은 QUIC이라는 프로토콜을 기반으로 하는데, QUIC은 UDP를 기반으로 합니다. 즉, UDP 자체는 신뢰성을 보장하지 않지만, 추가적인 정의를 통해 신뢰성을 보장받을 수 있습니다.</p>
</details>

<details>
  <summary>:black_square_button: TCP 3, 4 way handshake에 대해서 설명해보세요.</summary>
  </br>
  <p>TCP가 가상회선을 만들고 제거하는 과정에 대해서 묻는 질문입니다. TCP를 공부하셨다면 이 정도는 알겠지 하고 묻는 문제고, 실제 면접자리에서는 보통 네트워크에 대해서 설명할 때, 직접 설명하는 편입니다.</p>
  <p>TCP 3way handshake는 가상회선을 수립하는 단계입니다. 클라이언트는 서버에 요청을 전송할 수 있는지, 서버는 클라이언트에게 응답을 전송할 수 있는지 확인하는 과정입니다. SYN, ACK 패킷을 주고받으며, 임의의 난수로 SYN 플래그를 전송하고, ACK 플래그에는 1을 더한값을 전송합니다. 정확한 순서는 SYN(n) -> ACK(n + 1), SYN(m) -> ACK(m + 1) 순으로 일어납니다.</p>
  <p>왜 임의의 난수를 지정하느냐는 꼬리질문이 나올 수 있습니다. 기존 요청과 구분하기 위해서 정도로 알고있고, 그 이상은 생각해본적이 없네요.</p>
  </br>
  <p>TCP 4way handshake는 TCP연결을 해제하는 단계로, 클라이언트는 서버에게 연결해제를 통지하고 서버가 이를 확인하고 클라이언트에게 이를 받았음을 전송해주고 최종적으로 연결이 해제됩니다. 단, 서버에서 소켓이 닫혔다고 통지해도 클라이언트 측에서는 일정시간 대기하는데, 혹시나 패킷이 나중에 도착할 수 있기 때문입니다.</p>
</details>

<details>
  <summary>:black_square_button: HTTP와 HTTPS의 차이점에 대해서 설명해보세요.</summary>
  </br>
  <p>HTTP는 따로 암호화 과정을 거치지 않기 때문에 중간에 패킷을 가로챌 수 있고, 수정할 수 있습니다. 따라서 보안이 취약해짐을 알 수 있습니다. 이를 보완하기 위해 나온 것이 HTTPS입니다. 중간에 암호화 계층을 거쳐서 패킷을 암호화합니다.</p>
</details>

<details>
  <summary>:black_square_button: HTTPS에 대해서 설명하고 SSL Handshake에 대해서 설명해보세요.</summary>
  </br>
  <p>HTTPS는 HTTP에 보안 계층을 추가한 것입니다. HTTPS는 제3자 인증, 공개키 암호화, 비밀키 암호화를 사용합니다.</p>
  <p>제3자 인증은 믿을 수 있는 인증기관에 등록된 인증서만 신뢰하는 것이고, 공개키 암호화는 비밀키를 공유하기 위해 사용합니다. 비밀키 암호화는 통신하는 데이터를 암호화하는데 사용합니다.</p>
  <p>클라이언트는 TCP 3way handshake를 수행한 이후 Client Hello를 전송합니다. 서버는 인증서를 보냅니다.(다른 정보들도 전송하나 검색을 통해 알 수 있는 부분입니다. 대개 그 정도까지는 요구하지 않습니다.)</p>
  <p>클라이언트는 받은 인증서를 신뢰하기 위해서 등록된 인증기관인지 확인합니다. 이 인증서는 인증기관의 개인키로 암호화되어있고, 공개키로 검증할 수 있습니다.(브라우저에 내장되어있음) 클라이언트는 사이트의 정보와, 서버의 공개키를 얻을 수 있습니다.</p>
  <p>서버의 공개키로 통신에 사용할 비밀키를 암호화해서 서버에 보냅니다. 서버는 이를 개인키로 확인하고 이후 통신은 공유된 비밀키로 암호화되어 통신합니다.</p>
  <p>제3자 인증: 인증서, 인증기관/공개키 암호화: 인증서, 비밀키 공유/비밀키 암호화: 통신과정</p>
  <p>왜 공개키 암호화와 비밀키 암호화를 복합적으로 사용했는지도 질문을 받았습니다.</p>
</details>

<details>
  <summary>:black_square_button: GET과 POST의 차이점에 대해서 설명해보세요.</summary>
  </br>
  <p>대개의 경우 아래의 HTTP 메서드 질문을 더 많이합니다. 하지만 둘의 차이만을 물을 수도 있습니다.</p>
  <p>GET요청은 서버에 존재하는 정보를 요청합니다. 이 때 반환되는 정보는 정보 자체가 아니라 정보의 표현입니다.(뒤의 내용은 REST와 연관이 있고, 굳이 답변하지 않으셔도 됩니다.) 일반적으로 Request Body는 입력하지 않는 것이 일반적이며, 레거시 시스템의 경우 요청을 받아들이지 않을 수 있습니다. 캐싱을 수행하기 때문에 캐싱되지 않는 요청은 GET 요청이 맞지 않을 수 있습니다.</p>
  <p>POST요청은 서버에 정보를 생성하는 것을 요청합니다. 예전 HTTP 통신은 POST 요청으로 데이터 삭제, 수정도 form요청으로 같이 수행했습니다. POST 요청은 서버의 상태를 변경시키기 때문에 멱등성이 유지되지 않습니다. 보통 Request Body에 요청하는 데이터를 담아 전송합니다.</p>
</details>

<details>
  <summary>:black_square_button: HTTP 메서드와 이것이 하는 역할에 대해서 설명해보세요.</summary>
  </br>
  <p>보통 REST API를 설계했다면 이해할 수 있을정도로 설명하면 되는 것 같습니다.</p>
  <p>OPTIONS, HEAD, TRACE의 존재에 대해서는 알아만 둡시다. 특히 TRACE는 몰라도 되는 것 같습니다. OPTIONS는 해당 uri에 대해 서버가 허용하는 메서드를 확인할 때 사용합니다. HEAD는 GET과 비슷하나 header만 가져옵니다.</p>
  <ul>
    <li>GET 요청은 서버에 존재하는 데이터를 요청하는 것입니다. CRUD로 따지면 R입니다.</li>
    <li>POST 요청은 서버에 데이터를 생성하는 것을 요청합니다. CRUD로 따지면 C입니다.</li>
    <li>PUT 요청은 서버에 존재하는 데이터를 수정하거나 존재하지 않으면 생성합니다. CRUD로 따지면 C,U입니다.</li>
    <li>DELETE 요청은 서버에 데이터를 제거할 것을 요청합니다. 존재하지 않아도 동일하게 동작합니다. CRUD로 따지면 D입니다.</li>
    <li>PATCH 요청은 서버에 존재하는 데이터를 일부 수정합니다. CRUD로 따지면 U입니다.</li>
  </ul>
  <p>더 나아가서 불필요한 메서드는 허용하지 않고 필요한 메서드만 허용하는 Whitelist 방식으로 관리합시다. 자세한 내용은 HTTP Method 취약점에 대해 검색합시다.</p>
</details>

<details>
  <summary>:black_square_button: RESTful이란 무엇이며, 이것에 대해서 아는대로 설명해보세요.(보충필요)</summary>
  </br>
  <p>REST는 굉장히 난해한 개념입니다. 하지만 REST가 무엇인지 대략의 감은 잡아둡시다. REST API를 설계했다면 충분히 물어볼만한 질문입니다.</p>
  <p>HTTP URI를 통해 자원을 표시하고 HTTP Method를 통해 자원에 대한 처리를 표현합니다. 사람이 읽을 수 있는 API라는 것이 특징입니다. HTTP를 사용하기 때문에 HTTP의 특성을 그대로 반영합니다. 또한 별도의 인프라 구축이 필요없습니다.</p>
  <p>단점으로는 명확한 표준이 존재하지 않는다는 점, RESTful을 완전히 만족하는 API를 만들기는 매우 까다롭다는 점(그런 REST API로 괜찮은가 참고)이 있습니다.</p>
  <p>HATEOAS라는 개념이 있는데, 동적인 API를 제공할 수 있게됩니다.(모든 관련된 동작을 URI를 통해 알려줍니다.) 즉, 클라이언트가 API의 변화에 일일이 대응하지 않아도 된다는 장점을 가져옵니다.</p>
</details>

<details>
  <summary>:black_square_button: CORS란 무엇이며 이것에 대해서 설명해보세요.</summary>
  </br>
  <p>CORS는 웹개발을 하다가 흔히 만날 수 있는 이슈입니다. 대개는 프론트엔드 개발시에 로컬에서 API 서버에 요청을 보낼 때 흔하게 발생합니다.</p>
  <p>서로 다른 도메인간에 자원을 공유하는 것을 뜻합니다. 대부분의 브라우저에서는 이를 기본적으로 차단하며, 서버측에서 헤더를 통해서 사용가능한 자원을 알려줍니다.</p>
  <p>preflight request는 실제 요청을 보내도 안전한지 판단하기 위해 사전에 보내는 요청입니다. OPTIONS 메서드로 요청하며 CORS를 허용하는지 확인합니다. CORS가 허용된 웹서버라면 사용 가능한 리소스를 헤더에 담아 응답합니다.</p>
</details>

<details>
  <summary>:black_square_button: OSI7계층과 그 존재 이유, TCP/IP 4계층에 대해 설명해보세요.</summary>
  </br>
  <p>OSI7계층은 네트워크 통신을 구성하는 요소들 7개의 계층으로 표준화 한 것입니다. 이렇게 표준화하는 것의 장점은 통신이 일어나는 과정을 단계별로 파악할 수 있어, 문제가 발생하면 해당 문제를 해결하기 용이해집니다.</p>
  <p>실제로 우리가 대부분 사용하는 네트워크는 TCP/IP 4계층입니다. 통신에 실제로 사용되는 계층이고 1,2 계층이 1계층, 5, 6, 7계층이 4계층으로 운영됩니다.</p>
</details>

<details>
  <summary>:black_square_button: 웹 서버 소프트웨어(Apache, Nginx)는 OSI 7계층 중 어디서 작동하는지 설명해보세요.</summary>
  </br>
  <p>Apache와 NGINX는 HTTP 웹 서버로, 이들이 동작하는 HTTP 프로토콜은 OSI 7 Layer 중 7계층인 애플리케이션 Layer 에 해당하는 프로토콜입니다. HTTP 프로토콜은 TCP/IP 프로토콜을 통해 동작합니다. TCP/IP 프로토콜은 OSI 7 Layer 중 4계층인 Transport Layer에서 동작합니다.  따라서 웹 서버 소프트웨어는 4계층의 TCP/IP 프로토콜과 7계층의 HTTP 프로토콜을 활용하여 동작합니다.</p>
</details>

<details>
  <summary>:black_square_button: 웹 서버 소프트웨어(Apache, Nginx)의 서버 간 라우팅 기능은 OSI 7계층 중 어디서 작동하는지 설명해보세요.</summary>
  </br>
  <p> 두 가지가 있습니다. Layer 4 (Transport Layer), 그리고 Layer 7 (Application Layer) 입니다. L4 에서는 TCP/UDP 포트 정보를 토대로 라우팅 기능이 제공됩니다. L7에서는 TCP/UDP 뿐만 아니라 HTTP의 URI 등을 토대로 라우팅 기능이 제공 됩니다. 
  L4 에서 라우팅 기능을 사용 한 예시를 들자면, Nginx 의 경우 여러 포트들을 하나의 upstream 블록으로 묶어서 로드 밸런싱, 즉 특정 경로로 전달되는 요청을 각 포트 별로 분산해서 전달하도록 설정 해 줄 수 있습니다.
  L7 에서 라우팅 기능을 사용 한 예시를 들자면, Apache, Nginx 각각에서 서브 도메인에 대해 라우팅 설정을 해 둘 수 있습니다. 브라우저에서 /test 와 같은 서브 도메인으로 HTTP 프로토콜을 통한 요청을 보낸다면, 웹서버 내 Config 파일에 설정 된 경로 정보를 토대로 요청에 대한 라우팅을 제공하여 스태틱 파일을 전달하거나 API 서버에 대해 리버스 프록시 역할을 해 줄 수 있습니다.</p>
</details>

### 운영체제

운영체제는 제가 공부가 부족해서 틀리거나 다른 내용이 있을 수 있습니다.  
검색을 통해서 학습하시고, 간단한 자신만의 답을 만들어보세요.  
보통 중요하다곤 하나 지엽적인 지식은 잘 안물어보기도 합니다.(비전공자의 경우 더더욱 물어보지 않을 가능성이 큽니다.)

<details>
  <summary>:black_square_button: 프로세스와 스레드의 차이를 설명해보세요.</summary>
  </br>
  <p>프로세스는 실행중인 프로그램을 의미합니다. 스레드는 실행 제어만 분리한 것을 의미합니다.</p>
  <p>프로세스는 운영체제로부터 자원을 할당받지만, 스레드는 프로세스로부터 자원을 할당받고, 프로세스의 코드/데이터/힙영역을 공유하기 때문에 좀 더 효율적으로 통신할 수 있습니다. 또한 컨텍스트 스위칭도 캐시 메모리를 비우지 않아도 되는 스레드쪽이 빠릅니다. 그리고, 스레드는 자원 공유로 인해 문제가 발생할 수 있으니 이를 염두에 둔 프로그래밍을 해야합니다.</p>
  <p>한 프로세스 안에 여러개의 스레드가 생성될 수 있습니다.</p>
</details>

<details>
  <summary>:black_square_button: 컨텍스트 스위칭에 대해 설명해보세요.</summary>
  </br>
  <p>컨텍스트 스위칭은 한 Task가 끝날 때까지 기다리는 것이 아니라 여러 작업을 번갈아가며 실행해서 동시에 처리될 수 있도록 하는 방법입니다.</p>
  <p>인터럽트가 발생하면 현재 프로세스의 상태를 PCB에 저장하고 새로운 프로세스의 상태를 레지스터에 저장하는 방식으로 동작합니다. 이 때, CPU는 아무런 일을 하지 않으므로 잦은 컨텍스트 스위칭은 성능저하를 일으킬 수 있습니다.</p>
  <p>스레드와 프로세스의 동작방식이 약간 상이한데, 스레드는 캐시메모리나 PCB에 저장해야하는 내용이 적고, 비워야 하는 내용도 적기때문에 상대적으로 더 빠른 컨텍스트 스위칭이 일어날 수 있습니다.</p>
</details>

<details>
  <summary>:black_square_button: 동기와 비동기의 차이(블로킹, 넌블로킹) / 장단점에 대해 설명해보세요.</summary>
  </br>
  <p>동기/비동기는 두 개 이상의 무엇인가가 시간을 맞춘다/안맞춘다로 구분할 수 있습니다.</p>
  <p>동기 방식은 메서드 리턴과 결과를 전달받는 시간이 일치하는 명령 실행 방식입니다. 또, 동기 방식은 한 함수가 끝나는 시간과 바로 다음의 함수가 시작하는 시간이 같습니다.</p>
  <p>비동기 방식은 여러 개의 처리가 함께 실행되는 방식으로, 동기 방식에 비해 단위시간 당 많은 작업을 처리할 수 있습니다. 단, CPU나 메모리를 많이 사용하는 작업을 비동기로 처리하게 되면 과부하가 걸릴 수 있습니다. 프로그램의 복잡도도 증가하게 됩니다.</p>
  <p>블로킹/논블로킹은 동기/비동기와는 다른 관점으로, 내가 직접 제어할 수 없는 대상(IO/멀티스레드)을 상대하는 방법에 대한 분류입니다.</p>
  <p>블로킹 방식은 대상의 작업이 끝날 때 까지 제어권을 대상이 가지고 있는 것을 의미합니다. 반면에 논블로킹은 대상의 작업 완료여부와 상관없이 새로운 작업을 수행합니다.</p>
  <p>동기 논블로킹은 계속해서 polling을 수행하기 때문에 컨텍스트 스위칭이 지속적으로 발생해 지연이 발생합니다.</p>
  <p>https://youtu.be/HKlUvCv9hvA 를 참고합시다.</p>
</details>

<details>
  <summary>:black_square_button: 멀티스레드 프로그래밍에 대해 설명해보세요.</summary>
  </br>
  <p>멀티스레드 프로그래밍은 하나의 프로세스에서 여러개의 스레드를 만들어 자원의 생성과 관리의 중복을 최소화하는 것을 멀티스레드 프로그래밍이라고 합니다.</p>
  <p>장점
    <ul>
      <li>멀티 프로세스에 비해 메모리 자원소모가 줄어듭니다.</li>
      <li>힙 영역을 통해서 스레드간 통신이 가능해서 프로세스간 통신보다 간단합니다.</li>
      <li>스레드의 컨텍스트 스위칭은 프로세스의 컨텍스트 스위칭보다 빠릅니다.</li>
    </ul>
  </p>
  <p>단점
    <ul>
      <li>힙 영역에 있는 자원을 사용할 때는 동기화를 해야합니다.</li>
      <li>동기화를 위해서 락을 과도하게 사용하면 성능이 저하될 수 있습니다.</li>
      <li>하나의 스레드가 비정상적으로 동작하면 다른 스레드도 종료될 수 있습니다.</li>
    </ul>
  </p>
</details>

<details>
  <summary>:black_square_button: Thread-safe 하다는 의미와 설계하는 법을 설명해보세요.</summary>
  </br>
  <p>두 개 이상의 스레드가 race condition에 들어가거나 같은 객체에 동시에 접근해도 연산결과의 정합성이 보장될 수 있게끔 메모리 가시성이 확보된 상태를 의미합니다.</p>
  <ul>
    <li>java.util.concurrent 패키지 하위의 클래스를 사용합니다.</li>
    <li>인스턴스 변수를 두지 않습니다.</li>
    <li>Singleton 패턴을 사용합니다.(이 때, 일반적으로 구현하는 Singleton Pattern은 Thread-safe 하지 않습니다.)[참고](https://github.com/ksundong/TIL/blob/master/DesignPattern/singleton-pattern.md)</li>
    <li>동기화(syncronized) 블럭에서 연산을 수행합니다.</li>
  </ul>
</details>

<details>
  <summary>:black_square_button: 프로세스 동기화에 대해 설명해보세요.</summary>
  </br>
  <p>알아야 하는 부분이 조금 많습니다. 면접때에는 적절히 짧게 끊어서 대답합시다. 너무 깊게 들어가면 말을 번복할 가능성도 있고, 잘 모른다는 인상을 주기 쉽습니다.</p>
  <p>다중 프로세스 환경에서 자원등에 한 프로세스만이 접근가능하도록 하는 것입니다.</p>
  <p>프로세스 동기화를 하지 않으면 데이터의 일관성이 깨지기 때문에 연산결과가 잘못 반환될 가능성이 존재하기 때문에 주의해야 합니다.</p>
  <p>Race Condition(경쟁 상태): 여러 프로세스나 스레드가 동기화 메커니즘 없이 자원에 접근하려는 상황을 가리킵니다. 공유된 자원에 대한 접근 순서에 따라 실행 결과가 달라질 수 있는 상황을 의미합니다.</p>
  <p>Critical Section(임계 구역): 여러 스레드가 동시에 접근해서는 안되는 공유자원에 접근하는 코드 블럭을 얘기합니다. 한 임계구역에 하나의 스레드 혹은 프로세스만 접근이 가능합니다. 임계 구역에 접근하는 것을 제어하기 위해 세마포어, 뮤텍스와 같은 매커니즘을 사용합니다.</p>
  <p>임계 구역 문제를 해결하기 위한 조건(모두 충족해야함)
    <ul>
      <li>상호 배제(Mutual Exclusion): 한 프로세스가 임계구역에서 동작중이면 다른 프로세스는 접근할 수 없다.</li>
      <li>진행(Progress): 임계구역에서 작업중인 프로세스가 없다면 입계구역으로 진입하려는 프로세스를 적절히 선택해서 진입할 수 있도록 합니다.</li>
      <li>유한 대기(Bounded Waiting): 한 프로세스가 임계영역으로 진입을 요청한 후 다른 프로세스는 진입이 유한한 횟수로 제한되어야 합니다. (기아상태 방지)</li>
    </ul>
  </p>
</details>

<details>
  <summary>:black_square_button: 교착상태와 기아상태의 해결방법에 대해 설명해보세요.</summary>
  </br>
  <p>교착상태(Deadlock)가 무엇인지 알고 있어야 합니다. 서로 다른 프로세스가 서로 점유하고 있는 자원의 반납을 대기하고 있는 상태를 의미합니다.</p>
  <p>발생조건
    <ul>
      <li>상호 배제: 한 번에 한 프로세스만 해당 자원을 사용할 수 있어야 합니다.</li>
      <li>점유 대기: 할당된 자원을 가진 상태에서 다른 자원을 기다립니다.</li>
      <li>비선점: 다른 프로세스가 자원의 사용을 끝낼 때 까지 자원을 뺏을 수 없습니다.</li>
      <li>순환대기: 각 프로세스가 순환적으로 다음 프로세스가 요구하는 자원을 가지고 있습니다.</li>
    </ul>
  </p>
  <p>해결방법
    <ul>
      <li>예방: 4가지 조건 중 하나라도 만족되지 않도록 합니다.</li>
      <li>회피: 알고리즘을 데드락이 발생하지 않도록 합니다.</li>
      <li>회복: 교착상태가 발생할 때, 해결합니다.</li>
      <li>무시: 회복과정의 성능저하가 심하다면 그냥 무시합니다.</li>
    </ul>
  </p>
  <p>기아상태(Starvation): 여러 프로세스가 부족한 자원을 점유하기 위해 경쟁할 때, 특정 프로세스가 영원히 자원 할당이 되지 않는 경우입니다.</p>
  <p>우선순위를 변경합니다.(우선순위를 수시로 변경하거나, 오래 기다린 프로세스의 우선순위를 높여주거나, Queue를 사용합니다.)</p>
</details>

<details>
  <summary>:black_square_button: 세마포어와 뮤텍스의 차이에 대해 설명해보세요.</summary>
  </br>
  <p>세마포어는 여러개의 프로세스가 접근 가능한 공유자원을 관리하는 방식이고, 뮤텍스가 될 수 있지만, 뮤텍스는 한 번에 한 개의 프로세스만 접근 가능하도록 관리하는 방식입니다. 따라서 뮤텍스는 세마포어가 될 수 없습니다.</p>
  <p>또, 세마포어는 다른 프로세스가 세마포어를 해제할 수 있지만, 뮤텍스는 락을 획득한 프로세스만 락을 반환할 수 있습니다.</p>
</details>

<details>
  <summary>:black_square_button: 가상 메모리에 대해 설명해보세요.</summary>
  </br>
  <p>가상 메모리는 프로세스가 실제 메모리의 크기와 상관없이 메모리를 이용할 수 있도록 지원하는 기술 입니다.</p>
  <p>가상 메모리는 실제 메모리(RAM, main memory, first storage)와 보조 기억 장치(auxiliary storage, secondary storage)의 Swap 영역으로 구성됩니다.</p>
  <p>OS 는 메모리 관리자(Memory Management Unit)를 통해 메모리를 관리하며 프로세스는 사용하는 메모리가 실제 메모리인지, Swap 영역인지 모릅니다.</p>
  </br>
  <p>Java 에서는 Swap 영역을 잡아주지 않은 경우 OOM 이 발생할 수 있습니다.</p>
  <p>Swap 영역은 실제 메모리가 아니기 때문에 지연시간이 많이 발생하며, 가급적이면 Swap 메모리를 사용하지 않도록 설계하는 것이 좋고, 만약 계속해서 사용하는 양이 증가한다면 메모리 누수를 의심해 볼 수 있습니다.</p>
</details>

<details>
  <summary>:black_square_button: 캐시의 지역성에 대해 설명해보세요.</summary>
  </br>
  <p>캐시가 무엇인지, 왜 캐시를 사용하는지를 알고 있어야 합니다. 관련한 좋은 글을 링크해둡니다. https://parksb.github.io/article/29.html</p>
  <p>시간 지역성과 공간 지역성으로 나눌 수 있으며, 시간 지역성은 최근에 접근한 데이터에 다시 접근하는 경향을 의미하고, 공간 지역성은 최근 접근한 데이터의 주변 공간에 다시 접근하는 경향을 의미합니다.</p>
</details>

<details>
  <summary>:black_square_button: 프로세스 관련 용어를 설명해보세요. (알아만 둡시다.)</summary>
  </br>
  <p>PCB: 프로세스 제어 블록, 프로세스에 대한 중요한 정보를 저장합니다.</p>
  <p>PC: 프로그램 카운터, 프로세스 실행을 위한 다음 명령의 주소를 표시합니다.</p>
  <p>캐시메모리: 자주 사용되는 데이터가 저장되는 공간으로 CPU의 레지스터와 메모리 사이에서 병목 현상을 완화하는 장치입니다.</p>
</details>

### 데이터베이스

<details>
  <summary>:black_square_button: 데이터베이스에서 인덱스를 사용하는 이유 및 장단점에 대해 설명해주세요.</summary>
  </br>
  <p>데이터베이스에서 인덱스를 사용하는 이유는 검색성능을 향상시키기 위함입니다.</p>
  <p>하지만 검색성능을 실질적으로 향상시키기 위해서는 해당 쿼리가 index를 사용하는지, 카디널리티, Selectivity 같은 요소들이 고려된 인덱스가 생성되어야 합니다.</p>
  <p>일반적인 경우의 장점으로는 빠른 검색 성능을 들 수 있습니다.</p>
  <p>일반적인 경우의 단점으로는 인덱스를 구성하는 비용 즉, 추가, 수정, 삭제 연산시에 인덱스를 형성하기 위한 추가적인 연산이 수행됩니다.</p>
  <p>따라서, 인덱스를 생성할 때에는 트레이드 오프 관계에 놓여있는 요소들을 종합적으로 고려하여 생성해야합니다.</p>
  <p>그렇다고 모든 곳에서 인덱스를 사용하면 오히려 악효과를 낼 수 있다.</p>
  <p>1. 인덱스를 생성하면 추가적인 저장공간이 필요하고 인덱스 관리를 위한 오버헤드가 발생 할 수 있다.</p>
  <p>2. 인덱스가 존재하는 경우, 데이터 삽입,수정,삭제시에도 인덱스가 함께 업데이트 된다. 다라서 인덱스 수가 많이잘수록 쓰기 성능이 감소 할 수 있다.</p>
  <p>3. 쿼리에 사용되지 않는 인덱스가 존재하면, 해당 인덱스는 시스템 리소스 공간을 불필요하게 차지하기 때문에 시스템 전체 성능에 부정적인 영향이 있을 수 있다.</p>
  <p>4. 인덱스를 관리하는것도 비용이 드는 작업이기 때문에 인덱스가 많아지면 관리하기 어려울 수 있다.</p>
  <p>등의 문제가 있기 때문에 인덱스를 생성전에 충분한 분석 및 검토가 필요하여 시스템을 균형있게 유지해야 한다.
  </p>

</details>

<details>
  <summary>:black_square_button: 트랜잭션에 대해서 설명해주세요.</summary>
  </br>
  <p>트랜잭션이란 데이터베이스의 상태를 변화시키는 하나의 논리적인 작업 단위라고 할 수 있으며, 트랜잭션에는 여러개의 연산이 수행될 수 있습니다.</p>
  <p>트랜잭션은 수행중에 한 작업이라도 실패하면 전부 실패하고, 모두 성공해야 성공이라고 할 수 있습니다.</p>
</details>

<details>
  <summary>:black_square_button: ACID에 대해서 설명해주세요.</summary>
  </br>
  <p>ACID는 트랜잭션이 안전하게 수행된다는 것을 보장하기 위한 성질입니다.</p>
  <p>
    <ul>
      <li>Atomicity(원자성): 트랜잭션의 연산은 모든 연산이 완벽히 수행되어야 하며, 한 연산이라도 실패하면 트랜잭션 내의 모든 연산은 실패해야 합니다.</li>
      <li>Consistency(일관성): 트랜잭션은 유효한 상태로만 변경될 수 있습니다.</li>
      <li>Isolation(고립성): 트랜잭션은 동시에 실행될 경우 다른 트랜잭션에 의해 영향을 받지 않고 독립적으로 실행되어야 합니다.</li>
      <li>Durability(내구성): 트랜잭션이 커밋된 이후에는 시스템 오류가 발생하더라도 커밋된 상태로 유지되는 것을 보장해야 합니다. (일반적으로 비휘발성 메모리에 데이터가 저장되는 것을 의미)</li>
    </ul>
  </p>
</details>

<details>
  <summary>:black_square_button: 트랜잭션 격리 수준(Transaction Isolation Levels)에 대해서 설명해주세요.</summary>
  </br>
  <p>트랜잭션 격리수준은 고립도와 성능의 트레이드 오프를 조절합니다.</p>
  <p>
    <ul>
      <li>READ UNCOMMITTED: 다른 트랜잭션에서 커밋되지 않은 내용도 참조할 수 있다.</li>
      <li>READ COMMITTED: 다른 트랜잭션에서 커밋된 내용만 참조할 수 있다.</li>
      <li>REPEATABLE READ: 트랜잭션에 진입하기 이전에 커밋된 내용만 참조할 수 있다.</li>
      <li>SERIALIZABLE: 트랜잭션에 진입하면 락을 걸어 다른 트랜잭션이 접근하지 못하게 한다.(성능 매우 떨어짐)</li>
    </ul>
  </p>
</details>

<details>
  <summary>:black_square_button: 정규화에 대해서 설명해주세요.</summary>
  </br>
  <p>정규화는 데이터의 중복방지, 무결성을 충족시키기 위해 데이터베이스를 설계하는 것을 의미합니다.</p>
  <p>이 이상을 물어보는 경우가 있었는데, 학습이 좀 더 필요한 것 같습니다.</p>
</details>

<details>
  <summary>:black_square_button: JOIN에 대해서 설명해주세요.</summary>
  </br>
  <p>단순히 SQL에서 JOIN 쿼리가 어떤식으로 동작하는지 알고 있어야 합니다.</p>
  <p>다이어그램으로 이해하는 편이 좋습니다.</p>
</details>

<details>
  <summary>:black_square_button: RDBMS vs NOSQL에 대해서 설명해주세요.</summary>
  </br>
  <p>RDBMS는 데이터베이스를 이루는 객체들의 릴레이션을 통해서 데이터를 저장하는 데이터베이스입니다. SQL을 사용해 데이터의 저장, 질의, 수정, 삭제를 할 수 있으며 데이터를 효율적으로 보관하는 것을 목적으로 하고 구조화가 굉장히 중요합니다.</p>
  <p>장점으로는 명확한 데이터 구조를 보장하고, 중복을 피할 수 있습니다.</p>
  <p>NOSQL은 RDBMS에 비해 자유로운 형태로 데이터를 저장합니다. 또한 수평확장을 할 수 있고 분산처리를 지원합니다. 다양한 형태의 NOSQL 데이터베이스가 있고, 대표적으로 key-value store, bigtable, dynamo, document db, graph db 등이 있습니다.</p>
  <p>둘은 대체될 수 있는 것이 아니고, 각각 필요한 시점에 적절히 선택해서 사용해야 합니다. 둘 다 같이쓰는 상호보완적인 존재가 될 수도 있습니다.</p>
</details>

<details>
  <summary>:black_square_button: Redis에 대해서 간단히 설명해주세요.</summary>
  </br>
  <p>Redis는 key-value store NOSQL DB입니다. 싱글스레드로 동작하며 자료구조를 지원합니다. 그리고 다양한 용도로 사용될 수 있도록 다양한 기능을 지원합니다. 데이터의 스냅샷 혹은 AOF 로그를 통해 복구가 가능해서 어느정도 영속성도 보장됩니다.</p>
  <p>스프링에서는 세션을 관리하거나, 캐싱을 하는데에 자주 사용되는 것으로 알고 있습니다.</p>
</details>

<details>
  <summary>:black_square_button: Redis와 Memcached의 차이에 대해서 설명해주세요.</summary>
  </br>
  <p>Redis는 싱글 스레드 기반으로 동작하고, Memcached는 멀티스레드를 지원해서 멀티 프로세싱이 가능합니다.</p>
  <p>Redis는 다양한 자료구조를 지원하고, Memcached는 문자열 형태로만 저장합니다.</p>
  <p>Redis는 여러 용도로 사용할 수 있도록 다양한 기능을 지원합니다.</p>
  <p>Redis는 스냅샷, AOF 로그를 통해서 데이터 복구가 가능합니다.</p>
</details>

<details>
  <summary>:black_square_button: Elastic Search에 대해서 간단히 설명해주세요.</summary>
  </br>
  <p>Elastic Search는 자바로 개발된 오픈소스 검색엔진 입니다. 보통 단독으로 사용하기보다는 ELK 스택이라고 부르는 Logstash, Kibana, Beats를 추가적으로 사용합니다.</p>
  <p>Inverted Index 구조로 데이터를 저장해서, 전문(Full-text) 검색시에 RDBMS에 비해 뛰어난 성능을 보장합니다.</p>
  <p>다양한 용도로 사용할 수 있습니다. (데이터 저장, 문서 검색, 위치 검색, 머신 러닝 기반 검색, 로그 분석, 보안 감사 분석 등)</p>
</details>

<details>
  <summary>:black_square_button: Elastic Search의 인덱스구조와 RDBMS의 인덱스 구조의 차이에 대해 설명해주세요.</summary>
  </br>
  <p>Elastic Search는 Inverted-Index 구조로 데이터를 저장합니다. 이는 책의 색인을 생각해보면 쉬운데, 특정 단어가 출현하는 doc을 저장하는 것입니다. 반면 RDBMS는 B-Tree와 그와 유사한 인덱스를 사용합니다. 데이터가 어디에 존재하는지 어떤 순서로 저장하는 지의 차이라고 생각합니다. RDBMS에도 다양한 인덱스 구조가 있으나 여기서 예로 든 것은 B-Tree 인덱스입니다.</p>
</details>

<details>
  <summary>:black_square_button: Elastic Search의 키워드 검색과 RDBMS의 LIKE 검색의 차이에 대해 설명해주세요.</summary>
  </br>
  <p>Elastic Search의 키워드 검색은 document를 저장할 때 수행하는 알고리즘과 동일한 알고리즘으로 키워드를 분리합니다. 그 중에서 랭킹알고리즘을 통해서 가장 유사한 순서대로 결과를 나타냅니다.</p>
  <p>RDBMS에서의 LIKE 검색은 와일드카드로 시작하지 않는 경우에만 인덱스를 사용하고 나머지 경우는 전체를 탐색하기 때문에 상대적으로 느립니다.</p>
</details>

<details>
  <summary>:black_square_button: MongoDB에 대해서 간단히 설명해주세요.</summary>
  </br>
  <p></p>
</details>

<details>
  <summary>:black_square_button: CAP 이론과, Eventual Consistency에 대해서 설명해주세요.</summary>
  </br>
  <p>CAP 이론은 분산 환경에서 모두를 만족하는 시스템은 없다는 이론입니다.</p>
  <p>
    <ul>
      <li>Consitenty(일관성): ACID의 일관성과는 약간 다릅니다. 모든 노드가 같은 시간에 같은 데이터를 보여줘야 한다는 것입니다.</li>
      <li>Availability(가용성): 모든 동작에 대한 응답이 리턴되어야 합니다.</li>
      <li>Partition Tolerance(분할 내성): 시스템 일부가 네트워크에서 연결이 끊기더라도 동작해야 합니다.</li>
    </ul>
  </p>
  <p>CAP는 해당 시스템이 이거다 하고 말하기 곤란한게 어떻게 클러스터링 하느냐에 따라 달라질 수 있습니다. 그렇기 때문에 어떤 전략을 취할 때 어떤 것을 선택했는가를 잘 알아야 합니다. (단순히 MySQL이 CA입니다. 보다는 어떤 이유로 CA인지 근거를 생각해보기) 그리고 어느정도 한계가 있는 이론이고 PACELC 이론이라고 또 있습니다.</p>
  <p>Eventual Consistency는 이 Consistency를 보장해주지 못하기 때문에 나온 개념으로, Consistency를 완전히 보장하지는 않지만, 결과적으로 언젠가는 Conssistency가 보장됨을 의미합니다.</p>
</details>

### 자료구조/알고리즘

보통의 자료구조/알고리즘적 지식은 코딩테스트로 검증합니다.  
하지만 아래의 개념을 적어도 이해는 한다고 생각하니, 혹시 모르는 부분이 있을 경우 학습을 권장합니다.

<details>
  <summary>:black_square_button: 시간 복잡도를 계산해주세요.</summary>
  </br>
  <p>코딩테스를 풀었다면 해당 코드에 대해서 시간복잡도를 물어볼 수 있습니다.</p>
  <p></p>
</details>

<details>
  <summary>:black_square_button: 배열과 링크드 리스트의 차이를 설명해주세요.</summary>
  </br>
  <p>배열은 메모리상에 순서대로 데이터를 저장합니다. 반면 링크드 리스트는 다음 데이터의 위치에 대한 포인터를 가지고 있는 구조입니다.</p>
  <p>배열은 데이터를 인덱스로 조회할 수 있기 때문에 인덱스 조회성능이 높고, 데이터가 메모리에 순서대로 저장되어 있기 때문에, 캐시의 지역성으로 인하여 비교적 빠르게 탐색을 수행할 수 있습니다.</p>
  <p>링크드 리스트는 중간에 데이터를 삽입하거나 삭제하는 것이 용이하다는 장점이 있습니다.</p>
</details>

<details>
<summary>:black_square_button: List와 Set의 차이에 대해서 설명해주세요.</summary>
</br>
<p>List는 <b>중복</b>된 데이터를 저장하고 순서를 유지하는 선형 자료구조이고, Set은 <b>중복</b>되지 않은 데이터를 저장할 수 있고, 일반적으로 순서를 유지하지 않는 선형 자료구조입니다.(Set은 집합입니다., TreeSet과 같이 순서를 유지하는 Set도 존재합니다.) </p>
</details>

<details>
  <summary>Hash Function, HashTable에 대해서 설명해주세요.</summary>
  </br>
  <p></p>
</details>

<details>
  <summary>:black_square_button: Stack, Queue에 대해서 설명해주세요.</summary>
  </br>
  <p><b>Stack</b></p>
  <p>스택은 선형 자료구조의 일종으로 마지막에 저장한 데이터를 가장 먼저 꺼내게 되는 LIFO(Last In First Out)방식의 자료구조 입니다. 스택의 사용 예시로는 웹 브라우저의 방문기록(뒤로가기), 실행 취소(undo) 등이 있습니다.</p>
  <p><b>Queue</b></p>
  <p>큐는 선형 자료구조의 일종으로 처음에 저장한 데이터를 가장 먼저 꺼내게 되는 FIFO(First In First Out)방식의 자료구조 입니다. 큐의 사용 예시로는 프린터의 인쇄 대기, 콜센터 고객 대기 시간 등이 있습니다.</p>
</details>

<details>
  <summary>:black_square_button: Heap, Priority Queue에 대해서 설명해주세요.</summary>
  </br>
  <p></p>
</details>

<details>
  <summary>:black_square_button: Tree, Binary Tree, BST, AVL Tree에 대해서 설명해주세요.</summary>
  </br>
  <p></p>
</details>

<details>
  <summary>:black_square_button: BST의 최악의 경우의 예와 시간복잡도에 대해서 설명해주세요.</summary>
  </br>
  <p>BST가 아닌 Self-Balanced Tree를 사용하는 이유에 대해서 생각해보았다면 쉽게 답할 수 있는 문제입니다.</p>
  <p>예를들어 1부터 10까지 순차적으로 BST에 저장했다면, BST의 형태는 리스트와 같아집니다. 이 경우를 최악의 경우라고 하며 시간복잡도는 O(n)이 됩니다.</p>
</details>

<details>
  <summary>:black_square_button: 피보나치 수열을 코드로 구현하는 방법에 대해서 설명해주세요.</summary>
  </br>
  <p>질문의 의도는 피보나치 수열을 코드로 구현할 수 있는가? 만약 재귀를 사용했다면 어떤 문제가 있는가? DP를 사용할 수 있는가로 이어집니다.</p>
  <p>피보나치 수열은 보통 재귀정도로 구현할 수 있지만, 중복된 연산이 계속해서 발생하게 됩니다. 이런 중복된 연산을 메모리 등에 저장해두고 해당 결과가 존재하지 않을 때만 연산을 수행하도록 하면 보다 빠른 동작을 구현할 수 있게됩니다.</p>
</details>

<details>
  <summary>:black_square_button: DFS, BFS에 대해서 설명해주세요.</summary>
  </br>
  <p></p>
</details>

<details>
  <summary>:black_square_button: 정렬, 탐색에 대해 설명해주세요.</summary>
  </br>
  <p></p>
</details>

### 암호학/보안(간단한 정도)

<details>
  <summary>:black_square_button: 비대칭키 암호화, 대칭키 암호화에 대해 간단히 설명해주세요.</summary>
  </br>
  <p>비대칭키 암호화란 공개키 암호화라고도 하며, 공개키는 외부에 공개되어있고, 비밀키는 내부적으로 가지고 있고 서로 각각의 키로 암호화하거나 해제할 수 있는 방식입니다. 이 방식은 대칭키를 공유하는 방식보다 비교적 안전하며, 대신 연산 성능이 떨어지는 편입니다.</p>
  <p>대칭키 암호화란 양측이 동일한 키를 가지고 있으며, 암호화와 해제에 동일한 키를 사용하는 방식입니다. 이 방식은 비밀키가 노출되는 문제가 있을 수 있으며, 연산성능은 덜 필요해 상대적으로 빠릅니다.</p>
</details>

<details>
  <summary>:black_square_button: 단방향 암호화에 대해서 간단히 설명해주세요.</summary>
  </br>
  <p>단방향 암호화는 복호화 불가능한 암호화라고 합니다. 대부분 해시 알고리즘을 이용해서 구현하며, 민감정보를 데이터베이스에 저장할 때, 해당 방식을 사용합니다.</p>
  <p>보통의 단방향 암호화는 빠른 성능을 보여, 무차별 대입 공격에 취약합니다. 따라서 이런 정보를 저장하기 위해 bcrypt와 같은 방식을 사용합니다.</p>
  <p>해시란 말에서 알 수 있듯이 충돌가능성이 있습니다. 이렇게 복호화 불가능한 암호화 방식이 위험하다는 것은 해시 충돌을 일으켰다는 말로 이해해도 됩니다.</p>
</details>

<details>
  <summary>:black_square_button: JWT에 대해서 간단히 설명해주세요.</summary>
  </br>
  <p>JWT란 토큰 인증 방식에서 쓰이는 것이라고 볼 수 있습니다. 다른 사용으론 데이터를 공유하는데도 사용할 수 있지만 일반적으론 토큰 인증 방식에서 사용됩니다.</p>
  <p>JWT는 헤더, 페이로드, 시그니쳐로 구분됩니다. 헤더는 토큰의 타입, 암호화 알고리즘을 담고 있고, 페이로드는 토큰의 정보를 담는 부분이며, 시그니처는 토큰의 정보가 신뢰할 수 있는것인지 판단할 수 있도록 합니다.</p>
  <p>JWT는 세션 기반 인증과 주로 대비됩니다. 세션기반 인증은 서버에서 세션 정보를 관리해야하는 비용이 들게됩니다. 또한 분산환경에서도 관리하기 어렵습니다. 하지만 JWT는 그 자체로 정보를 가지고 있기 때문에 세션의 단점을 보완할 수 있습니다.</p>
  <p>JWT와 다른 토큰 기반 인증 방식을 비교하는 질문이 나온적도 있습니다.</p>
</details>

<details>
  <summary>:black_square_button: OAuth에 대해서 간단히 설명해주세요.</summary>
  </br>
  <p>OAuth는 제3자 인증방식 입니다. 기본적으로 사용자는 서버를 신뢰할 수 없습니다. 그렇기 때문에, 민감정보를 작성하는 것을 꺼립니다. 서버측에서도 마찬가지 입니다. 사용자의 민감정보를 관리하는 것은 리소스가 필요합니다.</p>
  <p>그래서 OAuth를 사용해서 신뢰할 수 있는 서버에게 정보를 맡겨놓고 접근할 수 있는 권한을 주는 것이라고 이해하면 됩니다. 그러면 사용자 측에서는 민감정보를 굳이 입력하지 않고도 서비스를 사용할 수 있고, 서버측에서도 민감정보를 굳이 관리하지 않아도 되기 때문에 이점이라고 볼 수 있습니다.</p>
  <p>OAuth 아키텍처에 대해서 설명해주세요.</p>
</details>

<details>
  <summary>:black_square_button: JWT와 OAuth의 차이는 무엇이 있을까요?</summary>
  </br>
</details>

<details>
  <summary>:black_square_button: SQL Injection에 대해서 간단히 설명해주세요.</summary>
  </br>
  <p></p>
</details>

<details>
  <summary>:black_square_button: XSS에 대해서 간단히 설명해주세요.</summary>
  </br>
  <p></p>
</details>

<details>
  <summary>:black_square_button: CSRF에 대해서 간단히 설명해주세요.</summary>
  </br>
  <p></p>
</details>

### 컴파일러

<details>
  <summary>:black_square_button: 스크립트 언어와 컴파일 언어를 나열하고 차이점을 설명해주세요.</summary>
  </br>
  <p>스크립트 언어는 PHP, Javascript, Python이 대표적인 스크립트 언어입니다. 컴파일 언어는 C, C++, Swift, Go가 있습니다.</p>
  <p>Java는 조금 특수한 경우입니다. Java는 컴파일 시에 Java Byte Code로 컴파일 되며, 이는 JVM에서 인터프리터 방식으로 동작합니다. 하지만 JIT Compiler라는 기술과 Hotspot JVM이라는 기술의 합작으로 네이티브 언어와 유사한 수준의 퍼포먼스를 낼 수 있게 되었습니다.</p>
  <p>스크립트 언어와 컴파일 언어의 차이점은 스크립트 언어는 인터프리터라는 방식으로 한 라인 한 라인 기계어로 번역하며 실행하고, 우리가 컴파일 에러라고 부르는 문법 오류를 사전에 방지하지 못하기 때문에 주의해야 합니다. 바로바로 실행하기에는 좋기 때문에 해당 방식이 필요한 분야에 많이 사용됩니다. 컴파일 언어는 컴파일 과정을 거쳐 기계어 코드로 번역이 되기 때문에 사전에 검증을 할 수 있고, 최적화를 해줄 수 있습니다. 이것이 컴파일러가 가지는 장점입니다.</p>
</details>

## 언어 관련

### Java


<details>
  <summary>:black_square_button: JVM의 구조와 Java의 실행방식을 설명해주세요.</summary>
  </br>
  <p>자바 가상 머신의 약자를 따서 줄여 부르는 용어로 JVM의 역할은 자바 애플리케이션을 클래스 로더를 통해 읽어 자바 API와 함께 실행하는 것입니다. 메모리 관리(GC)을 수행하며 스택기반의 가상머신입니다.</p>
  <p>JVM의 구조는 Class Loader, Execution engine, Runtime Data Area, JNI, Native Method Library로 이루어져 있습니다.</p>
  <ul>
    <li>클래스 로더: JVM내로 클래스를 로드하고, 링크를 통해 배치하는 작업을 수행하는 모듈</li>
    <li>실행 엔진: 바이트 코드를 실행시키는 역할</li>
    <ul>
      <li>인터프리터: 바이트 코드를 한줄 씩 실행합니다.</li>
      <li>JIT 컴파일러: 인터피르터 효율을 높이기 위한 컴파일러로 인터프리터가 반복되는 코드를 발견하면 JIT 컴파일러가 반복되는 코드를 네이티브 코드로 바꿔줍니다. 그 다음부터 인터프리터는 네이티브 코드로 컴파일된 코드를 바로 사용합니다.</li>
      <li>GC(Garbage Collector): 가비지 컬렉터로 힙 영역에서 사용되지 않는 객체들을 제거하는 작업을 의미합니다.</li>
    </ul>
    <li>Runtime Data Areas: 프로그램 실행 중에 사용되는 다양한 영역입니다.</li>
    <ul>
      <li>PC Register: Thread가 시작될 때 생성되며 현재 수행 중인 JVM 명령의 주소를 갖고 있습니다.</li>
      <li>Stack Area: 지역 변수, 파라미터 등이 생성되는 영역. 실제 객체는 Heap에 할당되고 해당 레퍼런스만 Stack에 저장됩니다.</li>
      <li>Heap Area: 동적으로 생성된 오브젝트와 배열이 저장되는 곳으로 GC의 대상 영역입니다.</li>
      <li>Method Area: 클래스 멤버 변수, 메소드 정보, Type 정보, Constant Pool, static, final 변수 등이 생성됩니다. 상수 풀(Constant Pool)은 모든 Symbolic Reference를 포함하고 있습니다.</li>
    </ul>
    <li>JNI(Java Native Interface): 자바 애플리케이션에서 C, C++, 어셈블리어로 작성된 함수를 사용할 수 있는 방법을 제공해줍니다. Native 키워드를 사용하여 메서드를 호출합니다. 대표적인 메서드는 Thread의 currentThread()입니다.</li>
    <li>Native Method Library: C, C++로 작성된 라이브러리 입니다.</li>
  </ul>
  <p>Java의 실행방식
    <ul>
    <li>자바 컴파일러(javac)가 자바 소스코드(.java)를 읽어 자바 바이트코드(.class)로 변환시킵니다.</li>
    <li>Class Loader를 통해 class 파일들을 JVM으로 로딩합니다.</li>
    <li>로딩된 class파일들은 Execution engine을 통해 해석됩니다.</li>
    <li>해석된 바이트코드는 Runtime Data Areas 에 배치되어 실질적인 수행이 이루어집니다.</li>
    </ul>
  </p>
</details>

<details>
  <summary>:black_square_button: GC가 무엇인지, 필요한 이유는 무엇인지, 동작방식에 대해 설명해주세요.</summary>
  </br>
  <p>GC는 힙 영역에서 사용하지 않는 객체들을 제거하는 작업을 총칭합니다. 이 객체를 제거하는 작업이 필요한 이유는 자바는 개발자가 메모리를 직접 해제해줄 수 없는 언어이기 때문입니다. 따라서 객체를 사용하고 제거하는 기능이 필요하게 됩니다.</p>
  <p>GC의 동작방식은 가장 간단한 Serial GC 방식으로 설명합니다. 좀 더 진보된 GC는 G1 GC, ZGC가 있으며 여기선 다루지 않습니다.</p>
  <p>GC는 Minor GC, Major GC로 구분할 수 있습니다. Minor GC는 young 영역에서, Major GC는 old 영역에서 일어난다고 정의합니다. (Major GC, Full GC는 명확히 정의된 문서가 없습니다.) GC를 수행할 때는 GC를 수행하는 스레드 이외의 스레드는 모두 정지합니다. 이를 Stop-the-world라고 합니다.</p>
  <p>Minor GC는 Eden 영역이 가득 참에서 부터 시작됩니다. Eden 영역에서 참조가 남아있는 객체를 mark하고 survivor 영역으로 복사합니다. 그리고 Eden 영역을 비웁니다. Survivor 영역도 가득차면 같은 방식으로 다른 Survivor 영역에 복사하고 비웁니다. 이를 반복하다 보면 계속 해서 살아남는 객체는 old 영역으로 이동하게 됩니다.</p>
  <p>Major GC는 old 영역에서 일어납니다. 위와 반대로 삭제되어야 하는 객체를 mark합니다. 그리고 지웁(sweep)니다. 메모리는 단편화 된 상태이므로 이를 한 군데에 모아주는 것을 Compaction이라 하며 compact라고 합니다. 그래서 Mark-Sweep-Compact 알고리즘이라고 합니다.</p>
  <p>이것이 중요한 이유는 GC 수행시 시스템이 멈추기 때문에 의도치 않은 장애의 원인이 될 수 있습니다. 따라서 이를 위해 힙 영역을 조정하는 것을 GC 튜닝이라고 하고 JVM 메모리는 절대 마음대로 조정해선 안됩니다.</p>
</details>

<details>
  <summary>:black_square_button: 컬렉션 프레임워크에 대해서 설명해주세요.</summary>
  </br>
  <p>Java Collection은 널리 알려져 있는 자료구조를 바탕으로 객체, 데이터들을 효율적으로 관리 할 수 있는 자료구조들이 있는 라이브러리를 컬렉션 프레임워크라고 합니다.</p>
  <p>List, Set은 Collection 인터페이스을 상속받지만, Map 인터페이스는 구조상의 차이라 별도로 정의합니다.</p>
</details>

<details>
  <summary>:black_square_button: 제네릭에 대해서 설명해주세요.</summary>
  </br>
  <p>제네릭은 자바의 타입 안정성을 맡고 있습니다. 컴파일 과정에서 타입체크를 해주는 기능으로 객체의 타입을 컴파일 시에 체크하기 때문에 객체의 타입 안정성을 높이고 형변환의 번거로움을 줄여줍니다.</p>
</details>

<details>
  <summary>:black_square_button: 애노테이션에 대해서 설명해주세요.</summary>
  </br>
  <p>애노테이션은 인터페이스를 기반으로 한 문법으로 주석처럼 코드에 달아 클래스에 특별한 의미를 부여하거나 기능을 주입할 수 있습니다. built-in annotation은 상속받아서 메소드를 오버라이드 할 때 나타나는 @Override 애노테이션이 그 대표적인 예입니다.</p>
  <p>메타 애너테이션은 애노테이션을 선언할 때 사용하는 애노테이션입니다.</p>
  <ul>
    <li>@Retention: 애노테이션 유지 범위를 지정합니다. (소스, 클래스, 런타임)</li>
    <li>@Inherit: 애노테이션을 하위 클래스까지 전달여부를 지정합니다. 이 애노테이션이 있으면 하위 클래스까지 상속이 가능합니다.</li>
    <li>@Target: 해당 애노테이션을 어디에 사용할 지 결정합니다. (타입, 필드, 메서드, 파라미터, 생성자, 로컬변수, 애노테이션 타입)</li>
  </ul>
</details>

<details>
  <summary>:black_square_button: 오버라이딩과 오버로딩이 무엇이며 어떤 차이가 있을까요?</summary>
  </br>
  <p>의외로 굉장히 많은 답을 들을 수 있는 질문입니다.</p>
  <p>오버라이딩은 상위 클래스의 메소드를 재정의 하는 것을 의미합니다. 또, 런타임 다형성이기도 합니다.</p>
  <p>오버로딩은 같은 클래스 내에서 동일한 메소드 이름을 가지지만, 매개변수의 타입, 개수가 다르게 구현할 수 있는 것을 의미하며 컴파일 타임 다형성이기도 합니다. 따라서 오버라이딩 될 수 있습니다.</p>
  <p>추가로 `@Override`를 써야하는 이유를 꼭 생각해보세요. 이 애노테이션은 컴파일 타임에 오버라이딩에 대한 안정성을 부여해주기 때문에 반드시 써주는 것이 좋습니다.</p>
</details>

<details>
  <summary>:black_square_button: 인터페이스와 추상클래스의 차이점에 대해 설명해주세요.</summary>
  </br>
  <p>추상클래스는 객체의 추상적인 상위 개념으로 공통된 개념을 표현할 때 사용합니다. 단일 상속만 가능합니다. 추상클래스를 상속하는 집합간에는 연관관계가 있습니다.</p>
  <p>인터페이스는 구현 객체가 같은 동작을 한다는 것을 보장하기 위해 사용합니다. 다중 상속이 가능합니다. 인터페이스를 구현하는 집합간에는 관계가 없을 수 있습니다.</p>
</details>

<details>
  <summary>:black_square_button: 클래스는 무엇이고 객체는 무엇인가요?</summary>
  </br>
  <p>클래스는 객체를 정의하는 틀 또는 설계도와 같은 의미로 사용됩니다.</p>
  <p>객체는 식별 가능한 개체 또는 사물입니다. 객체는 구별 가능한 식별자, 특징적인 행동, 변경 가능한 상태를 가집니다. 인스턴스들을 통칭하는 용도로 사용합니다.</p>
</details>

<details>
  <summary>:black_square_button: 정적(static)이란 무엇인가요?</summary>
  </br>
  <p>static은 클래스 멤버라고 하며, 클래스 로더가 클래스를 로딩해서 메소드 메모리 영역에 적재할 때 클래스별로 관리됩니다.</p>
  <p>static 키워드를 통해 생성된 정적멤버들은 PermGen 또는 Metaspace에 저장되며 저장된 메모리는 모든 객체가 공유하며 하나의 멤버를 어디서든지 참조할 수 있는 장점이 있습니다.</p>
  <p>그러나, GC의 관리 영역 밖에 존재하기 때문에 프로그램 종료시까지 메모리가 할당된 채로 존재합니다. 너무 남발하게 되면 시스템 성능에 악영향을 줄 수 있습니다.</p>
</details>

<details>
  <summary>:black_square_button: 자바의 원시타입들은 무엇이 있으며 각각 몇 바이트를 차지하나요?</summary>
  </br>
  <p>실제 면접에서 들었던 질문입니다. 들었을 때 굉장히 당황했던 기억이 나네요.</p>
  <p>boolean(1), char(unsigned 2), byte(1), short(2), int(4), long(8), float(4), double(8)</p>
  <p>사실 JVM에 의존적이기 때문에 정확한 크기라기 보다는 대략적인 크기입니다.</p>
</details>

<details>
  <summary>:black_square_button: 접근 제어자의 종류와 이에 대해 설명해주세요.</summary>
  </br>
  <p>private, default, protected, public이 있습니다. private은 해당 클래스 내에서만 접근 가능하고, default는 해당 패키지, protected는 상속한 클래스, public은 전체 영역에서 접근 가능합니다.</p>
  <p>접근 제어자를 사용하는 이유는 외부에 보여주고 싶은 정보들을 선택적으로 제공하기 위함이고, 캡슐화와 통하는 면이 있습니다.</p>
</details>

<details>
  <summary>:black_square_button: 객체지향에 대해서 설명해주세요.</summary>
  </br>
  <p>객체지향을 정의하면, 의존성 관리입니다.</p>
  <p>객체지향으로 의존성을 관리함으로써 변경 영향을 최소화하고 독립적인 배포가 가능해지며 독립적인 개발이 가능해집니다. 따라서 객체지향에서 가장 중요한 것은 DIP(Dependency Inversion Principle)를 통한 고수준 정책(High Level Policy)와 저수준 구현 세부사항(Low Level Details)의 분리라고 할 수 있습니다.</p>
</details>

<details>
  <summary>:black_square_button: SOLID(객체지향 5대원칙)에 대해서 설명해주세요.</summary>
  </br>
  <p>SRP(단일책임원칙)은 한 클래스의 하나의 책임만 가져야 합니다.</p>
  <p>OCP(개방-폐쇄 원칙)은 확장에는 열려 있으나 변경에는 닫혀 있어야 하며, 다형성을 활용해야 합니다.</p>
  <p>LSP(리스코프 치환 원칙)은 프로그램의 객체는 프로그램의 정확성을 깨뜨리지 않으면서 하위 타입의 인스턴스로 바꿀 수 있어야하는 원칙으로 상위 타입을 상속해서 재정의 했을 때 프로그램이 깨지지 않아야 합니다.</p>
  <p>ISP(인터페이스 분리 원칙)은 클라이언트는 자신이 사용하지 않는 메서드에 의존 관계를 맺으면 안되는 원칙입니다. 특정 클라이언트를 위한 인터페이스 여러 개가 범용 인터페이스 하나보다 더 낫습니다. 즉, 비대한 인터페이스보단 더 작고 구체적인 인터페이스로 분리해야합니다.</p>
  <p>DIP(의존관계 역전 원칙)은 추상적인 것은 자신보다 구체적인 것에 의존하지 않고, 변화하기 쉬운 것에 의존해서는 안된다는 원칙입니다. 구체적으론 구현 클래스에 의존하지 말고, 인터페이스에 의존해야 하는 원칙입니다.</p>
</details>

<details>
  <summary>:black_square_button: 동일성(identity)와 동등성(equality)에 대해 설명해주세요. (equals(), ==)</summary>
  </br>
  <p>동일성은 객체의 주소를 비교하는 것이고, 동등성은 객체의 같음을 비교하는 것입니다.</p>
  <p>기본적으로 자바에서는 Object 클래스에 정의된 equals() 메소드가 동일성 비교를 합니다. 따라서, 개발자는 원한다면 equals() 메소드를 오버라이딩해서 동등성의 판단 기준을 정의해주면 됩니다.</p>
</details>

<details>
  <summary>:black_square_button: 원시타입과 참조타입의 차이에 대해 설명해주세요.</summary>
  </br>
  <p>원시타입은 Java에서 단 8개 밖에 존재하지 않는 타입입니다. 나머지는 모두 참조타입이라고 볼 수 있고, Object 클래스이거나 이를 상속하는 클래스들로 이루어져 있습니다.</p>
  <p>원시타입은 항상 값이 존재해야 합니다. 반면, Object 타입은 null 포인터를 가질 수 있습니다. 그리고 멤버변수가 초기화될 때, 원시타입은 기본값을 가지지만, 참조타입은 null 포인터를 가지는 차이도 있습니다.</p>
</details>

<details>
  <summary>:black_square_button: String, StringBuilder, StringBuffer 각각의 차이에 대해 설명해주세요.</summary>
  </br>
  <p>String은 불변입니다. StringBuilder와 StringBuffer는 이런 String의 특징때문에 사용하는 가변타입이라고 볼 수 있습니다.</p>
  <p>StringBuilder와 StringBuffer는 Thread-safe 여부의 차이가 있습니다. StringBuilder는 Thread-safe하지 않습니다. 따라서 Multi-Thread 환경에서 사용할 때는 StringBuffer를 사용합니다.</p>
</details>

<details>
  <summary>:black_square_button: Checked Exception과 Unchecked Exception에 대해 설명해주세요. 스프링 트랜잭션 추상화에서 rollback 대상은 무엇일까요?</summary>
  </br>
  <p>둘의 차이는 RuntimeException을 상속하는가의 여부에 따라 다릅니다. RuntimeException을 상속하면 UncheckedException이 됩니다. 스프링 트랜잭션 추상화에서 rollback 대상은 바로 UncheckedException입니다.</p>
  <p>이 둘을 잘 알기 위해서는 토비의 스프링을 보시는 것을 추천합니다.</p>
</details>

<details>
  <summary>:black_square_button: Java8에서 추가된 기능에 대해서 설명해주세요.</summary>
  </br>
  <p>자신이 사용한 경험을 말해주면 더 효과적일 것 같습니다.</p>
  <p>Java8에서는 Lambda식, Stream API, Optional, 날짜 시간 API, StringJoiner 등이 추가되었습니다.</p>
  <p>lambda는 함수형 프로그래밍을 지원하기 위한 기능이고, Stream API는 고차함수를 지원합니다. Optional은 Null-safety를 제공하며, Stream과 사용법이 유사합니다. 날짜 시간 API는 Joda-time등의 라이브러리에서 영향을 받아 괜찮은 API가 되었으며, StringJoiner는 문자열을 간단하게 구분자로 합칠 수 있는 기능을 제공합니다.</p>
</details>

<details>
  <summary>:black_square_button: try-with-resource에 대해서 설명해주세요.</summary>
  </br>
  <p>try-with-resources는 자바 버전7에 도입된 문법입니다.</p>
  <p>자바 7 버전 이전에서 하나 이상의 리소스(java.lang.AutoCloseable을 구현한 객체 혹은 java.io.Closeable를 구현한 객체)를 사용할 경우 개발자가 임의로 finally 문에서 ~~.close()를 사용하여 자원 해제를 시켜줘야 했습니다.</p>
  <p>만약 개발자가 사용한 자원을 finally 문에서 해제시켜주지 않고 누락시켰다면 자원이 해제되지 않은 채로 프로그램이 오작동하게 되고, finally 문에서 자원을 해제 시켜주더라도 자원 해제를 위한 중복 코드가 발생하기 때문에 소스 코드의 가독성을 해치는 단점이 있었습니다.</p>
  <p>이를 해결하기 위해 try() 안에 사용할 리소스 객체를 명시적으로 선언하여 사용하면, try 블록 안에서 로직이 정상적으로 완료되었는지, 갑작스럽게 완료되었는지 여부와 관계 없이 JVM에서 자동으로 자원을 반납해주는 기능을 하도록 도입하였습니다.</p>
  <p>추가로, 자바 9 버전에서는 try() 문 안에 명시적으로 객체 선언을 하기 보다는 try 문 바깥에서 객체 선언을 하고 생성된 인스턴스의 변수를 넣어줄 수 있도록 바뀌었습니다.</p>
  <p>
  Java 7 : try(BufferedReader br = new BufferedReader()) <br>
  Java 9 : try(br)
  </p>
</details>

<details>
  <summary>:black_square_button: 강한 결합과 느슨한 결합이 무엇인지 설명해주세요.</summary>
  </br>
  <p>결합도는 의존성의 정도를 나타내며 다른 모듈에 대해 얼마나 많은 정보를 알고 있는지에 대한 척도입니다.</p>
  <p>어떤 모듈이 다른 모듈에 너무 자세한 부분(구현 세부사항)까지 알고 있을 경우에 강한 결합도를 가진다고 합니다.</p>
  <p>어떤 모듈이 다른 모듈에 대해 필요한 정보(인터페이스로 추상화된 고수준 정책)만 알고 있다면 두 모듈은 낮은 결합도를 가진다고 합니다.</p>
  <p>객체지향 관점에서 결합도는 객체 또는 클래스가 협력에 필요한 적절한 수준의 관계만을 유지하고 있는지를 나타냅니다. 이러한 관점에서 강한 결합도는 반드시 지양해야 하며, 개발자는 적절한 결합도를 유지할 수 있도록 고민하고 설계해야 합니다.</p>
</details>

<details>
  <summary>:black_square_button: 직렬화와 역직렬화에 대해서 설명해주세요.</summary>
  </br>
  <p>직렬화란 자바 시스템 내부에서 사용되는 객체 또는 데이터를 외부의 자바 시스템에서도 사용할 수 있도록 바이트 형태로 데이터 변환하는 기술과 바이트로 변환된 데이터를 다시 변환하는 기술(역직렬화)을 아울러서 이야기 합니다.</p>
  <p>자바 직렬화는 JVM의 메모리에서만 상주되어있는 객체 데이터를 영속화(Persistence)가 필요할 때 사용됩니다. 시스템이 종료되더라도 없어지지 않는 장점을 가지며 영속화된 데이터이기 때문에 네트워크로 전송이 가능합니다.</p>
</details>

<details>
  <summary>:black_square_button: 자바의 동시성 이슈(공유자원 접근)에 대해 설명해주세요.</summary>
  </br>
  <p></p>
</details>

<details>
  <summary>:black_square_button: Mutable 객체와 Immutable 객체의 차이점에 대해 설명해주세요.</summary>
  </br>
  <p>Mutable 객체는 변경 가능 객체이고, Immutable 객체는 불변 객체라고 흔히들 말합니다.</p>
  <p>Mutable 객체는 도메인 개체(도메인 클래스 혹은 엔터티)로 사용됩니다. Mutable 객체의 변경 메서드는 Command method라고도 부르며, 리턴 타입을 void 로 정의합니다. 또한 void 리턴 타입의 어떠한 상태를 변경하는 메서드는 모두 Command method의 상징입니다.</p>
  <p>
  Immutable 객체는 불변객체이며 값 객체, 서비스 객체 등에 사용됩니다. Immutable 객체의 변경 메서드는 변경한 객체의 복사본을 반환해야 합니다.
  </p>
</details>

<details>
  <summary>:black_square_button: 자바에서 null을 안전하게 다루는 방법에 대해 설명해주세요.</summary>
  </br>
  <p>공개 메서드가 아닌 곳에는 assert를 사용하여 null을 방어할 수 있습니다. 또한 메서드의 인자를 받을 때 Objects.requireNonNull()을 사용하여 방어할 수 있습니다. 그리고 Optional을 사용해 리턴 타입에서 null을 반환하지 않도록 방어할 수 있습니다. 마지막으로 사전 조건과 사후 조건을 명확히 하여 계약에 의한 설계를 실천해야 합니다.</p>
</details>


<details>
  <summary>:black_square_button: JDK와 JRE의 차이점을 설명하세요.</summary>
  </br>
  JDK는 Java Development KIT의 약자로 개발하는데 사용되는 도구이며 JRE를 포함하고 있으며 <br/>
  JRE는 Java Runtime Environment의 약자로 자바로 만들어진 프로그램을 실행시키는데 필요한 도구가 <br/> 
  들어있는 차이가 있습니다.<br/>
  
  운영서버와 같은 곳에서는 개발에 필요한 도구가 아닌 프로그램을 실행시키는 도구만 필요하기 때문에<br/>
  개발도구가 들어있는 JDK아닌 JRE를 설치합니다.<br/>

  ----여기는 굳이 말씀 안하셔도 될듯합니다.----<br/>
  그러나 최근에 JDK가 많이 가벼워지고 하드웨어도 좋아지고 해서 운영서버에 설치하여도 큰 문제가 없고<br/>
  JDK에 로깅, 디버깅, 로그분석등 유용한 도구들도 있고 해서<br/>
  굳이 JRE설치하는것 보다 JDK를 설치 해서 개발및 실행환경을 통합적으로 관리하는 경우도 있다고 합니다.<br/>
  </details>


#### Spring

<details>
  <summary>:black_square_button: Spring DI/IoC는 어떻게 동작하나요?</summary>
  </br>
  <p>IoC(제어의 역전)은 프로그램의 제어 흐름을 직접 제어하는 것이 아니라 외부에서 관리하는 것으로 코드의 최종호출은 개발자가 제어하는 것이 아닌 프레임워크의 내부에서 결정된 대로 이루어집니다.</p>
  <p>DI(의존관계 주입)은 Spring 프레임워크에서 지원하는 IoC의 형태로 클래스 사이의 의존관계를 빈 설정 정보를 바탕으로 컨테이너가 자동으로 연결해줍니다.</p>
  <p>스프링에서는 스프링 컨테이너 ApplicationContext를 이용하여 설정 정보를 생성, 등록하고 필요한 객체를 생성자 혹은 setter를 통해 주입합니다.</p>
</details>

<details>
  <summary>:black_square_button: Spring Bean이란 무엇인가요?</summary>
  </br>
  <p>IoC 컨테이너 안에 들어있는 객체로 필요할 때 IoC컨테이너에서 가져와서 사용합니다. @Bean 을 사용하거나 xml설정을 통해 일반 객체를 Bean으로 등록할 수 있습니다.</p>
</details>

<details>
  <summary>:black_square_button: 스프링 Bean의 생성 과정을 설명해주세요.</summary>
  </br>
  <p>객체 생성 → 의존 설정 → 초기화 → 사용 → 소멸 과정의 생명주기를 가지고 있습니다. Bean은 스프링 컨테이너에 의해 생명주기를 관리하며 빈 초기화방법은 @PostConstruct 를 빈 소멸에서는 @PreDestroy 를 사용합니다.</p>
  <p>생성한 스프링 빈을 등록할 때는 ComponentScan을 이용하거나 @Configuration 의 @Bean 을 사용하여 빈 설정파일에 직접 빈을 등록할 수 있습니다.</p>
</details>

<details>
  <summary>:black_square_button: 스프링 Bean의 Scope에 대해서 설명해주세요.</summary>
  </br>
  <p>빈 스코프는 빈이 존재할 수 있는 범위를 뜻하며 싱글톤, 프로토타입, request, session, application 등이 있습니다.</p>
  <p>싱글톤은 기본 스코프로 스프링 컨테이너의 시작과 종료까지 유지되는 가장 넓은 범위의 스코프입니다.</p>
  <p>프로토타입은 빈의 생성과 의존관계 주입까지만 관여하고 더는 관리하지 않는 매우 짧은 범위의 스코프입니다.</p>
  <p>request는 웹 요청이 들어오고 나갈때까지 유지하는 스코프, session은 웹 세션이 생성, 종료할때까지, application은 웹 서블릿 컨텍스트와 같은 범위로 유지하는 스코프입니다.</p>
</details>

<details>
  <summary>:black_square_button: IoC 컨테이너의 역할은 무엇이 있을까요?</summary>
  </br>
  <p>애플리케이션 실행시점에 빈 오브젝트를 인스턴스화하고 DI 한 후에 최초로 애플리케이션을 기동할 빈 하나를 제공해준다</p>
</details>

<details>
  <summary>:black_square_button: DI 종류는 어떤것이 있고, 이들의 차이는 무엇인가요?</summary>
  </br>
  <p>DI는 세가지 방법이 있습니다. 생성자 삽입, Setter를 이용한 메소드 매개 변수 삽입, 필드 주입이 있습니다.</p>
  <p>생성자 주입은 생성자 호출시점에 딱 1번만 호출되는 것을 보장하며 불변, 필수 의존관계에 사용합니다.</p>
  <p>Setter주입은 선택, 변경 가능성이 있는 의존관계에 사용되며 스프링빈을 선택적으로 등록이 가능합니다.</p>
  <p>필드 주입은 `@Autowired` 를 사용하는데 외부에서 변경이 불가능하여 테스트 하기 힘듭니다. DI 프레임워크 없이는 작동하기 힘들며, 주로 애플리케이션과 관계없는 테스트코드나 `@Configuration` 같은 스프링 설정 목적으로 사용합니다. </p>
</details>

<details>
  <summary>:black_square_button: Autowiring 과정에 대해서 설명해주세요.</summary>
  </br>
  <p>컨테이너에서 타입(인터페이스 또는 오브젝트)을 이용해 의존 대상 객체를 검색하고 할당할 수 있는 빈 객체를 찾아 주입한다</p>
</details>

<details>
  <summary>:black_square_button: Spring Web MVC의 Dispatcher Servlet의 동작 원리에 대해서 간단히 설명해주세요.</summary>
  </br>
  <p></p>
</details>

<details>
  <summary>:black_square_button: 프론트 컨트롤러 패턴이란 무엇인가요?</summary>
  </br>
  <p>클라이언트의 다양한 요청마다 서블릿을 만들어서 사용한다고 하면 개발과 유지보수의 효율이 떨어질 수 밖에 없습니다. 프론트 컨트롤러 패턴을 사용함으로써 각 요청을 적절한 곳으로 위임해줌으로써 개발과 유지보수의 효율성이 증가하고 모든 요청에 대해 보안, 국제화, 라우팅 및 로그와 같은 일반적인 기능을 한 곳에서 캡슐화할 수 있습니다. Spring에서는 DispatcherServlet이 프론트 컨트롤러 패턴을 사용한 예이며, DispatcherServlet이 Bean으로 등록되어 package를 scan하고 @Controller, @RestController 애노테이션을 확인하여 어떠한 요청이 들어왔을 때 적절한 Handler Method에 위임해줍니다.</p>
</details>

<details>
  <summary>:black_square_button: Servlet Filter와 Spring Interceptor의 차이는 무엇인가요?</summary>
  </br>
  <p>Filter는 Servlet Filter로써 javax.servlet 스펙에 포함되는 클래스입니다.</p>
  <p>Interceptor는 Spring MVC 스펙에 포함되어 있는 클래스입니다.</p>
  <p>Filter는 Servlet에서 전후처리를 담당하며, Interceptor는 Spring에서 Handler를 실행하기 전후나, ViewResolver를 통해 컨트롤러에서 리턴한 View Name으로부터 렌더링을 담당할 View 오브젝트를 준비해 돌려준 후 실제 View를 렌더링한 후에 어떠한 처리를 담당합니다.</p>
  <p>Filter는 Web Application(Tomcat을 사용할 경우 web.xml)에 등록하며, Interceptor는 Spring의 Application Context에 등록합니다.</p>
  <p>Filter는 Method Signature에 있는 Argument인 HttpServletRequest 혹은 HttpServeltResponse를 ServletRequest, ServletResponse 등으로 교체할 때 사용하거나, 데이터 변환(다운로드 파일의 압축 및 데이터 암호화 등), XSL/T를 이용한 XML 문서 변경, 사용자 인증, 자원 접근에 대한 로깅 등에 사용합니다.</p>
  <p>Interceptor의 경우 AOP를 흉내내거나, Spring 애플리케이션에서 전역적으로 전후처리 로직에서 예외를 사용하도록 하거나, Handler Method에서 사용자의 권한을 체크해서 다른 동작을 시켜준다거나 할 때 사용합니다.</p>
  <p></p>
</details>

<details>
  <summary>:black_square_button: Spring에서 CORS 에러를 해결하기 위한 방법을 설명해주세요.</summary>
  </br>
  <p>Servlet Filter를 사용하여 커스텀한 Cors 설정하거나, WebMvcConfiguer를 구현한 Configuration 클래스를 만들어서 addCorsMappings()를 재정의할 수도 있고, 마지막으로 Spring Security에서 CorsConfigurationSource를 Bean으로 등록하고 config에 추가해줌으로써 해결할 수 있습니다.</p>
  <p>Controller 클래스에 @Crossorigin 어노테이션을 통해 해결할 수 있습니다.</p>
</details>

<details>
  <summary>:black_square_button: Bean/Component 어노테이션에 대해서 설명해주시고, 둘의 차이점에 대해 설명해주세요.</summary>
  </br>
  <p>두 어노테이션 모두 IoC 컨테이너에 Bean을 등록하기 위해 사용합니다</p>
  <p>@Component : 개발자가 작성한 class를 기반으로 실행시점에 인스턴스 객체를 1회(싱글톤) 생성합니다</p>
  <p>@Controller, @Service, @Repository 는 모두 @Component 이며 실행시점에 자동으로 의존성을 주입합니다</p>
  <p>@Bean : 개발자가 작성한 method를 기반으로 메서드에서 반환하는 객체를 인스턴스 객체로 1회(싱글톤) 생성합니다</p>
</details>

<details>
  <summary>:black_square_button: POJO란 무엇인가요? Spring Framework에서 POJO는 무엇이 될 수 있을까요?</summary>
  </br>
  <p>POJO는 프레임워크 인터페이스, 클래스를 구현하거나 확장하지 않은 단순한 클래스로 Java에서 제공하는 API 외에 종속되지 않습니다. 특정 환경에 종속되지 않아 코드가 간결하고 테스트 자동화에 유리합니다. 스프링에서는 도메인과 비즈니스 로직을 수행하는 대상이 POJO대상이 될 수 있습니다.</p>
</details>

<details>
  <summary>:black_square_button: Spring Web MVC에서 요청 마다 Thread가 생성되어 Controller를 통해 요청을 수행할텐데, 어떻게 1개의 Controller만 생성될 수 있을까요?</summary>
  </br>
  <p>@Controller 어노테이션을 타고 들어가보면 @Component라는 어노테이션이 붙어 있습니다. 따라서 컨트롤러는 IoC컨테이너에 등록되어 Spring bean으로 관리됩니다. Spring의 빈 생성 전략의 기본은 싱글턴입니다. IoC컨테이너에 Controller Bean은 싱글턴 전략에 의해 1개만 존재하고 Application이 Init 되는 시점에 초기화됩니다. 그리고 실제 사용되는 시점에 의존성 주입을 통해서 사용됩니다. 요청시마다 새로 Bean을 생성해서 사용하는 것이 아닌 이미 생성되어있는 Bean을 가져다 쓰게됨으로써 여러개의 Thread에서 Contoller를 사용해도 1개의 동일한 컨트롤러인 것입니다. 만약 요청이 올때마다 새로운 컨트롤러가 생기길 바란다면 Bean scope를 Singleton 이 아닌, request 등으로 설정하면 요청이 들어올 때 혹은 지정한 전략마다 새로운 컨트롤러 Bean이 생기도록 할 수 있습니다.</p>
</details>

<details>
  <summary>:black_square_button: Spring WEB MVC의 근간에는 Java Servlet 이 있는데요. Spring 은 Servlet을 어떻게 구성해서 이를 구현했을까요?</summary>
  </br>
  <p>Servlet은 Java로 웹페이지를 구성할 때 동적으로 웹페이지를 구성해주는 자바 클래스 입니다. Spring에서도 이 Servlet을 사용하고 있지만 특성이 조금 다릅니다. 기본적으로 Java의 Servlet은 하나의 Request에 대해서 하나의 Servlet을 생성합니다. 이 방법은 간단하고 직관적이지만 Servlet이 많이 생성되면 관리하기 힘들어지는 단점이 있습니다. 반면 Spring의 경우에는 DispatcherServlet이라는 FrontController 패턴을 사용해서 중앙에서 하나의 Servlet이 요청을 받아서 HandlerMapping을 통해 그에 맞는 컨트롤러로 분배하는 방식을 사용합니다. 이렇게 할 경우 하나의 객체에서 모든 요청을 먼저 처리하기 때문에 재사용성 및 유연한 매핑, 인터셉터의 사용, 관리의 용이성 등이 있겠습니다.</p>
</details>

<details>
  <summary>:black_square_button: Filter는 Servlet의 스펙이고, Interceptor는 Spring MVC의 스펙입니다. Spring Application에서 Filter와 Interceptor를 통해 예외를 처리할 경우 어떻게 해야 할까요?</summary>
  </br>
  <p>Filter는 DispatcherServlet 외부에 존재하기 때문에 예외가 발생했을 때 ErrorController에서 처리해야 합니다. 하지만 Interceptor는 DispatcherServlet 내부에 존재하기 때문에 @ControllerAdvice를 적용해서 처리할 수 있습니다.</p>
</details>

<details>
  <summary>:black_square_button: Spring Application을 구동할 때 메서드를 실행시키는 방법에 대해 설명해주세요.</summary>
  </br>
  <p>CommandLineRunner, ApplicationRunner를 구현한 클래스를 만들어서 실행시키는 2가지 방법이 있습니다. 또한 Spring의 ApplicationEvent를 사용한 방법, @Postconstruct를 사용한 방법, InitializingBean 인터페이스를 구현하는 방법, @Bean의 initMethod를 사용한 방법이 있습니다.</p>
</details>

<details>
  <summary>:black_square_button: 의존성과 설정값을 생성자 인자로 주입해야 하는 이유에 대해 설명해주세요.</summary>
  </br>
  <p>모든 의존성을 생성자를 통해 주입하면, 인스턴스 생성 시 즉시 어떠한 동작을 실행할 수 있습니다. 또한 추가적인 설정은 필요하지 않으며, 뜻하지 않게 의존성과 설정값을 빠뜨리는 일이 발생하지 않고 테스트에도 용이합니다.</p>
</details>

#### JPA

<details>
  <summary>:black_square_button: JPA 영속성 컨텍스트의 이점(5가지)을 설명해주세요.</summary>
  </br>
  <p>영속성 컨텍스트는 엔티티를 영구 저장하는 환경을 의미합니다.</p>
  <p>영속성 컨텍스트를 쓰는 이유는 1차 캐시, 동일성 보장, 쓰기 지연, 변경감지(Dirty checking), 지연로딩이 있습니다.</p>
  <ul>
    <li>1차 캐시: 조회가 가능하며 1차 캐시에 없으면 DB에서 조회하여 1차 캐시에 올려 놓습니다.</li>
    <li>동일성 보장: 동일성 비교가 가능합니다.(==)</li>
    <li>쓰기 지연: 트랜잭션을 지원하는 쓰기 지연이 가능하며 트랜잭션 커밋하기 전까지 SQL을 바로 보내지 않고 모아서 보낼 수 있습니다.</li>
    <li>변경 감지(Dirty checking): 스냅샷을 1차 캐시에 들어온 데이터를 찍습니다. commit 되는 시점에 Entity와 스냅샷과 비교하여 update SQL을 생성합니다.</li>
    <li>지연 로딩: 엔티티에서 해당 엔티티를 불러올 때 그 때 SQL을 날려 해당 데이터를 가져옵니다.</li>
  </ul>
</details>

<details>
  <summary>:black_square_button: JPA Propagation 전파단계를 설명해주세요.</summary>
  </br>
  <p>대기업면접에서 나왔던 질문으로 트랜잭션 고립단계와 같이 질문할 가능성이 있습니다.</p>
  <p>JPA Propagation은 트랜잭션 동작 도중 다른 트랜잭션을 호출(실행)하는 상황에 선택할 수 있는 옵션입니다.</p>
  <p>@Transactional의 propagation 속성을 통해 피호출 트랜잭션의 입장에서는 호출한 쪽의 트랜잭션을 그대로 사용할 수도 있고, 새롭게 트랜잭션을 생성할 수도 있습니다.</p>
  <p>REQUIRED(디폴트): 부모 트랜잭션 내에서 실행하며 부모 트랜잭션이 없을 경우 새로운 트랜잭션을 생성합니다.</p>
  <p>이 외에도 종류가 REQUIRES_NEW, SUPPORTS, MANDATORY, NOT_SUPPORT, NEVER, NESTED 가 있지만 신입이 실제로 다뤄본 경험이 적기 때문에 REQUIRED(디폴트)값만 답변했습니다.</p>
</details>

<details>
  <summary>:black_square_button: JPA를 쓴다면 그 이유에 대해서 설명해주세요.</summary>
  </br>
  <p>사실 면접관이 의도한 바를 파악하는게 중요합니다. 각기 다른 조건에서 같은 질문을 들었을 때 대답을 다르게 했던 기억이 납니다.</p>
  <p>제가 JPA를 사용하는 이유는 객체지향 프레임워크이기 때문입니다. JPA를 사용하면 비즈니스 로직이 RDBMS에 의존하는 것이 아니라, 자바 코드로 표현될 수 있기 때문입니다. 그로 인해서 생산성이 높아진다고 볼 수 있습니다.(이는 JPA에 익숙하다는 것을 전제로 합니다.)</p>
  <p>또, JPA는 JPQL로 SQL을 추상화하기 때문에 RDBMS Vendor에 관계없이 동일한 쿼리를 작성해서 같은 동작을 기대할 수 있다는 장점도 가지고 있습니다. 이는 database dialect를 지원하기 때문에 가지는 장점입니다.</p>
</details>

<details>
  <summary>:black_square_button: N + 1 문제는 무엇이고 이것이 발생하는 이유와 이를 해결하는 방법을 설명해주세요.</summary>
  </br>
  <p>JPA와 관련된 단골문제입니다. 꼭 학습해둡시다.</p>
  <p>N + 1 쿼리 문제는 즉시 로딩과 지연 로딩 전략 각각의 상황에서 발생할 수 있습니다. 하위 엔티티들이 존재하는 경우 한 쿼리에서 모두 가져오는 것이 아닌, 필요한 곳에서 각각 쿼리가 발생하는 경우를 이릅니다.</p>
  <p>즉시 로딩에서 발생하는 이유는 JPQL을 사용하는 경우 전체 조회를 했을 때, 영속성 컨텍스트가 아닌 데이터베이스에서 직접 데이터를 조회한 다음 즉시로딩 전략이 동작하기 때문입니다.<br>
  지연 로딩에서 발생하는 이유는 지연로딩 전략을 사용한 하위 엔티티를 로드할 때, JPA에서 프록시 엔티티를 unproxy 할 때 해당 엔티티를 조회하기 위한 추가적인 쿼리가 실행되어 발생합니다.</p>
  <p>해결 방법으로는 Fetch Join이라고 불리는 JPQL의 join fetch를 사용하는 방법이 있으며, 또 다른 방법으로는 <code>@EntityGraph</code>를 사용하는 방법, <code>@Fetch(FetchMode.SUBSELECT)</code>를 사용하는 방법, <code>@BatchSize</code>를 사용해 조절하거나 전역적인 batch-size를 설정하는 방법이 있습니다.</p>
  <p>각 해결방안에 대한 유의점은 작성하지 않습니다.</p>
</details>

### nodeJS


<details>
  <summary>:black_square_button: nodeJS는 싱글 스레드인가 멀티 스레드인가?</summary>
  </br>
  <b>nodeJS의 주 실행 흐름은 싱글 스레드 기반의 이벤트 루프 모델입니다.</b><br/>
  <p>I/O 작업을 자신의 메인 스레드(이벤트 루프를 도는 싱글스레드)가 아닌 다른 스레드(libuv에서 관리하는 thread pool에 존재)에 위임함으로써 싱글 스레드로 non blocking I/O를 지원합니다.<br>
  
  <p>(참고: event-driven모델을 사용하는 서버는 대체로 event loop를 활용하여 동작합니다. 예시로 redis(multiplexing),spring webflux(Reactor) 등이 있습니다.)<br>
</details>


<details>
  <summary>:black_square_button: 참조복사(얕은복사) vs 값복사(깊은복사)</summary>

  1) 얕은 복사(Shallow copy)는 참조 타입 데이터가 저장한 '메모리 주소 값'을 복사한 것을 의미한다. <br/>
  
  ```
  /* 얕은 복사시 주의!!! */ 
let origin = ["a", "b"];
let copy = origin;

copy.push("c");

console.log(origin); //["a", "b", "c" ]; // 원본까지 바뀌어버림
console.log(copy); //["a", "b", "c"];
  ```
  따라서 원본까지 바뀌는것에 주의해야 한다. <br/>

  2) 반대로 깊은 복사(Deep copy)는 새로운 메모리 공간을 확보해 완전히 복사하는 것을 의미한다.<br/>

</details>

### Python

<details>
  <summary>:black_square_button: List와 Tuple의 차이에 대해 설명해주세요.</summary>
  </br>
  <p>List와 Tuple의 가장 큰 차이점은 값을 변경할 수 있는가의 여부입니다.<br>
  1. List는 값을 수정할 수 있지만, Tuple은 값을 변경할 수 없습니다.</br>
  2. List는 []로 작성, Tuple은 ()를 이용하여 작성합니다.</p>
</details>

<details>
  <summary>:black_square_button: 파이썬 코루틴에 대해 아는대로 설명해주세요.</summary>
  </br>
  <p></p>
</details>

<details>
  <summary>:black_square_button: 파이썬 데코레이터에 대해 아는대로 설명해주세요.</summary>
  </br>
  <p>
      어떤 함수가 있을 때 해당 함수를 직접 수정하지 않고 함수에 기능을 추가하고자 할 때 데코레이터를 사용합니다.
      즉, 함수의 전처리나 후처리에 대한 필요가 있을 때 보통 사용합니다.
      이를 통해서 반복을 줄이고 메소드나 함수 책임을 확장시킬 수 있습니다.
  </p>
</details>

<details>
  <summary>:black_square_button: GIL에 대해 설명해주세요.</summary>
  </br>
  <p></p>
</details>

<details>
  <summary>:black_square_button: MRO에 대해 설명해주세요.</summary>
  </br>
  <p></p>
</details>

<details>
  <summary>:black_square_button: Magic Method에 대해 설명해주세요.</summary>
  </br>
  <p></p>
</details>

<details>
  <summary>:black_square_button: __new__와 __init__의 차이에 대해 설명해주세요.</summary>
  </br>
  <p></p>
</details>

<details>
  <summary>:black_square_button: __repr__와 __str__의 차이에 대해 설명해주세요.</summary>
  </br>
  <p></p>
</details>

<details>
  <summary>:black_square_button: r string과 u string에 대해 설명해주세요.</summary>
  </br>
  <p></p>
</details>

<details>
  <summary>:black_square_button: Call by Assignment에 대해 설명해주세요.</summary>
  </br>
  <p></p>
</details>

<details>
  <summary>:black_square_button: 파이썬에서의 접근제어지시자에 대해 아는대로 설명해주세요.</summary>
  </br>
  <p></p>
</details>

<details>
  <summary>:black_square_button: global과 nonlocal 키워드의 차이에 대해 설명해주세요.</summary>
  </br>
  <p></p>
</details>
 
<details>
  <summary>:black_square_button: classmethod와 staticmethod의 차이에 대해 설명해주세요.</summary>
  </br>
  <p></p>
</details>
 
## 기타

### 트러블 슈팅

<details>
  <summary>:black_square_button: 대용량 트래픽에서 장애가 발생하면 어떻게 대응할 것인가요?</summary>
  </br>
  <p>캐쉬에서 트래픽이 감당이 안되거나 오류가 나면 DB에서 조회하게끔 서킷브레이커를 걸어서 다른 방법으로 우회하도록 제공할 것입니다.</p>
</details>

### 디자인 패턴

<details>
  <summary>:black_square_button: 싱글톤 패턴에 대해서 설명해주세요.(생각보다 어려움)</summary>
  </br>
  <p>전역 변수를 사용하지 않고 객체를 하나만 생성하도록 하며, 생성된 객체를 어디에서든지 참조할 수 있도록 하는 패턴입니다.</p>
  <p>하나의 인스턴스만을 생성하며 getInstance메서드로 모든 클라이언트에게 동일한 인스턴스를 반환합니다.</p>
  <p>private 생성자를 가지는 특징을 가지며, 생성된 싱글톤 오브젝트는 저장할 수 있는 자신과 같은 타입의 스태틱 필드를 정의합니다.</p>
  <p>싱글톤 패턴의 문제점은 다음과 같습니다.</p>
  <ul>
    <li>의존 관계상 클라이언트가 구체 클래스에 의존합니다.</li>
    <li>private 생성자 때문에 테스트가 어렵습니다.</li>
    <li>객체 인스턴스를 하나만 생성해서 공유하는 방식 때문에 싱글톤 객체를 stateful하게 설계 했을 경우 큰 장애 발생요인이 됩니다.</li>
  </ul>
  <p>싱글톤의 단점을 해결하기 위해 무상태(stateless)로 설계해야 합니다.</p>
  <ul>
    <li>특정 클라이언트에 의존적인 필드가 있으면 안됩니다.</li>
    <li>특정 클라이언트가 값을 변경할 수 있는 필드가 있으면 안됩니다.</li>
    <li>가급적 읽기 전용으로 만들고, 필드 대신에 자바에서 공유되지 않는 지역변수, 파라미터, ThreadLocal 등을 사용합니다.</li>
  </ul>
</details>

<details>
  <summary>:black_square_button: 가교 패턴(브릿지 패턴)에 대해서 설명해주세요.</summary>
  </br>
  <p>가교 패턴은 추상부와 구현부를 분리하는 디자인 패턴입니다. 해당 패턴에서 기능은 인터페이스를 통해 정의 및 이용되고 해당 인터페이스를 따르는 클래스를 통해 구현됩니다. 해당 패턴을 통해서 사용자는 추상부와 구현부를 독립적으로 수정 및 확장할 수 있습니다. 가교 패턴은 객체지향 설계의 SOLID 원칙 중 단일 책임 원칙(SRP)과 개방 폐쇄 원칙(OCP)에 부합한 패턴입니다.</p>
</details>

<details>
  <summary>:black_square_button: 전략 패턴에 대해서 설명해주세요.</summary>
  </br>
  <p>전략 패턴은 알고리즘을 객체 단위로 캡슐화하는 디자인 패턴입니다. 해당 패턴에서 알고리즘은 인터페이스를 통해 정의 및 이용되고 해당 인터페이스를 따르는 클래스를 통해 구현됩니다. 해당 패턴을 통해서 사용자는 알고리즘을 필요에 따라 바꿔서 사용할 수 있게 됩니다. 전략 패턴은 객체지향 설계의 SOLID 원칙 중 개방 폐쇄 원칙(OCP)에 부합한 패턴입니다.</p>
  <p>전략 패턴은 가교 패턴과 구조가 비슷하지만 목적에 차이가 있습니다. 가교 패턴이 추상과 구현의 분리를 통한 독립적 개발의 용이성에 중점을 둔다면 전략 패턴은 알고리즘의 캡슐화를 통한 알고리즘 변경의 유연성에 중점을 둡니다.</p>
</details>

<details>
  <summary>:black_square_button: 빌더 패턴에 대해서 설명해주세요.</summary>
  </br>
  <p></p>
</details>

<details>
  <summary>:black_square_button: 팩토리 메서드 패턴에 대해서 설명해주세요.</summary>
  </br>
  <p></p>
</details>

<details>
  <summary>:black_square_button: 퍼사드 패턴에 대한 예를 들어주세요.</summary>
  </br>
  <p>바운디드 컨텍스트로 구분된 각각의 독립적인 애플리케이션을 UI 서버를 통해 파사드 역할을 담당하도록 두고 각 바운디드 컨텍스트에서 UI 서버와 통신하기 위해 HTTP, Protobuf, Thrift와 같은 방식을 이용할 수 있습니다.</p>
</details>

### 테스트

<details>
  <summary>:black_square_button: 테스트 코드에 대해서 어떻게 생각하고, 작성하나요?</summary>
  </br>
  <p></p>
</details>

<details>
  <summary>:black_square_button: TDD를 알고 있나요? TDD에 대해서 어떻게 생각하나요?</summary>
  </br>
  <p></p>
</details>

<details>
  <summary>:black_square_button: 테스트 커버리지에 대해서 어떻게 생각하나요?</summary>
  </br>
  <p>라인 커버리지, 브랜치 커버리지를 높은 수치로 달성하는 것은 바람직하지 않다고 생각합니다. 핵심 비즈니스 로직의 패스 커버리지를 갖는 것이 라인 커버리지, 브랜치 커버리지를 높은 수치로 유지하는 것보다 낫다고 생각합니다. 또한 무의미한 테스트 코드를 작성함으로써 유지보수 비용을 발생시키거나 읽기 좋은 코드를 테스트 커버리지를 채우기 위해 수정하는 등의 일은 반드시 피해야 한다고 생각합니다.</p>
</details>

### 인프라/클라우드

<details>
  <summary>:black_square_button: AWS 인프라를 구축해보았다면 설명해주세요.</summary>
  </br>
  <p></p>
</details>

<details>
  <summary>:black_square_button: 로드 밸런서에 대해서 설명해주세요.</summary>
  </br>
  <p></p>
</details>

<details>
  <summary>:black_square_button: 리버스 프록시에 대해서 설명해주세요.</summary>
  </br>
  <p></p>
</details>

<details>
  <summary>:black_square_button: Fault-tolerant(무정지) 시스템으로 가기 위해 필요한 방법에 대한 생각을 말해주세요. </summary>
  </br>
  <p>다운 타임이 발생하지 않도록 두 대 이상의 서버를 서비스해야 하고 비용 절감을 위해 배포할 때에만 새롭게 서비스를 띄우고, 배포가 완료된 후에는 기존 서버는 셧다운 시키면 됩니다.</p>
  <p>무정지 배포 방법 Rolling </br>
  로드 밸런서에서 서버를 빼고, 배포하고 다시 넣는 작업이 각 서버마다 이루어지도록 합니다. </br>
  Rolling 배포의 단점은 배포할 서버가 너무 많다면, n대 단위로 배포하기도 하는데 배포가 모두 끝나기 전까지 클라이언트 중 누구는 이전 서비스를 제공 받고 누구는 신규 서비스를 제공 받게 되는 문제가 발생합니다. 또한 1대에 배포하는 것보다 최소 2배 이상 느립니다.
  </p>
  <p>무정지 배포 방법 Canary </br>
  소수의 유저(혹은 사내)만 사용하는 환경(Canary 환경)에 신규 버전을 배포하고 문제가 없다고 판단됐을 때 다른 모든 서버에 배포합니다.
  </p>
  <p>무정지 배포 방법 Blue/Green </br>
  실제로 서비스 중인 환경(Blue)과 새롭게 배포할 환경(Green)을 세트로 준비해서 배포하는 형식입니다. </br>
  새롭게 배포할 환경에만 배포하면 되기 때문에 배포 속도가 매우 빠르며, 언제나 Green 환경이 실행 중이기 때문에 만약 잘못된 버전으로 배포 했을 경우 신속하게 롤백이 가능합니다. </br>
  Blue/Green 배포의 단점은 Green 환경이 항상 실행 중이어야 하기 때문에 비용이 많이 발생합니다.
  </p>
</details>

### 컨테이너

제가 아직 도커, 쿠버네티스에 익숙하지 않아 공부가 좀 더 필요합니다.  
관련해서 질문을 받아본적은 없으나, 일반적인 질문을 담아보았습니다.

<details>
  <summary>:black_square_button: Docker란 무엇이고 컨테이너 가상화를 왜 사용할까요?</summary>
  </br>
  <p></p>
</details>

<details>
  <summary>:black_square_button: 컨테이너 환경에서의 디버깅은 어떤식으로 하며 상대적으로 어려운 점은 무엇인가요?</summary>
  </br>
  <p></p>
</details>

### DevOps

DevOps는 어쩌면 신입에겐 물어보지 않을 수도 있습니다. 하지만 DevOps가 무엇인지 정도는 알아두는게 좋을 것 같습니다.

<details>
  <summary>:black_square_button: CI/CD가 무엇인가요? 왜 CI/CD가 장점이 될까요?</summary>
  </br>
  <p>보통 이 질문을 하는 동시에 어떤 CI/CD를 써봤는지 질문을 할 것입니다. 그때 썼던 CI/CD툴을 설명하고, 그 툴의 장단점을 설명하면 좋습니다.</p>
  <p>코드 버전 관리를 하는 VCS 시스템에 push가 되면 테스트와 빌드가 수행되어 안정적인 배포파일을 만드는 과정을 CI(지속적 통합, continuous integration)이라고 하며, 이 빌드 결과를 자동으로 운영 서버에 배포까지 되는 과정을 CD(지속적 배포, continuous delivery or continuous deployment)라고 합니다.</p>
  <p>푸시가 될 때마다 코드를 병합하고, 테스트 코드와 빌드를 수행하면서 자동으로 코드가 통합되어 더는 수동으로 코드를 통합할 필요가 없어져 개발에만 신경을 쓸 수 있습니다.</p>
  <p>이 CI / CD의 중요한 것은 테스트 자동화입니다. 프로젝트의 완전한 상태임을 보장하기 위해 테스트 코드가 구현되어 있어야 합니다.</p>
</details>

<details>
  <summary>:black_square_button: DevOps가 무엇인지 설명해주세요.</summary>
  </br>
  <p>DevOps는 애플리케이션과 서비스를 빠른 속도로 제공할 수 있도록 조직의 역량을 향상시키는 문화와 방식이며 자동화, 측정, 공유를 수행하고 이 모든 것들을 축적해나가는 것입니다.</p>
  <p>DevOps를 수행하면, 기존의 개발 및 인프라 관리 프로세스를 사용하는 조직보다 제품을 더 빠르게 혁신하고 개선할 수 있습니다. 이를 통해서 고객 친화적이고, 시장에 효과적으로 대응할 수 있는 유연성을 얻을 수 있습니다.</p>
</details>





### 커뮤니케이션

정답이 없는 질문입니다. 면접관마다 의도하는 답이 다 다를테니 자신만의 방법을 한 번 쯤 생각해보고 답변에 막힘이 없도록 준비합시다.


<details>
  <summary>:black_square_button: 코드리뷰중 갈등이 있을 경우, 이를 어떻게 해결할 것인가요?</summary>
  </br>
  <p></p>
</details>

<details>
  <summary>:black_square_button: 어떤 기술이나 방법론이 좋아보일 때, 이를 어떻게 설득할 것인가요?</summary>
  </br>
  <p></p>
</details>

<details>
  <summary>:black_square_button: 일정이 예상보다 지연될 것 같습니다. 어떻게 해결하실 것인가요?</summary>
  </br>
  <p></p>
</details>

<details>
  <summary>:black_square_button: 팀원과의 갈등이 있었나요? 있었다면 어떻게 대처했나요?</summary>
  </br>
  <p></p>
</details>

### 기타
<details>
  <summary>:black_square_button: 좋은 소스란, 좋은 코드, Clean Code란 어떤것인가요?</summary>
</details>
<details>
  <summary>:black_square_button: 코딩테스트의 해당 언어를 선택한 이유는 무엇인가요?</summary>
  </br>
  <p>Java(Spring), Javascript(Node), 파이썬등 여러가지 언어가 있었는데 왜 해당 언어로 코딩 테스트를 했는지</p>
  <p>해당 언어가 익숙해서 인지, 코딩 테스트 풀기 편해서인지, 우리 회사가 사용하는 언어여서 인지</p>
  <p>(*질문 작성자 주)을 물어보더라구요..회사에서 이 지원자의 기술 선호도, 프로그래밍 지식의 폭, 언어에 대한 이해, 업무 적합성 등을 알고 싶어서 물어 본거 아닐까 합니다.</p>
</details>

### 개인의 역량

<details>
  <summary>:black_square_button: 본인이 수행한 프로젝트 중 상용화 가능한 프로젝트가 있나요?</summary>
  </br>
  <p></p>
</details>

<details>
  <summary>:black_square_button: 기술을 습득할 때 어떤 식으로 습득하나요?</summary>
  </br>
  <p></p>
</details>

### 최신기술에 관심이 있는지

최신기술에 관심이 있는지 정도를 확인하고자 함입니다. 너무 정확하게 말하지 않아도 관심이 있다는 인상정도를 줄 수 있다면 좋겠습니다.  
그 회사의 기술 스택을 찾아보고 관심을 가져봤다 정도의 느낌을 줄 수 있어야합니다.  
사용까지 해보면 더더욱 좋을 것 같습니다.

<details>
  <summary>:black_square_button: protobuf에 대해서 알고계신가요? 이것은 왜 사용할까요?</summary>
  </br>
  <p>JSON이 가진 문제점을 보완하기 위한 하기위한 직렬화 방법</p>
  <p>JSON은 문자열 형식이기 때문에 바이트를 많이 사용한다. 하지만 프로토버프는 속성값을 숫자로 대체해서 바이트 스트림으로 만들기 때문에 훨씬 용량을 적게 소모한다.</p>
  <p>장점으로는 데이터 크기가 작아 데이터 통신이 빠르다. 또한 파싱을 할 필요가 없다.</p>
  <p>단점으로는 사람이 읽기 어렵고, 학습비용이 조금 있다.(proto의 문법을 알아야 한다.)</p>
</details>

<details>
  <summary>:black_square_button: gRPC는 무엇이며, RPC는 무엇인가요? 왜 쓸까요?</summary>
  </br>
  <p>gRPC는 HTML/JSON 방식의 비효율성을 개선하기 위해 나온 것입니다.</p>
  <p>RPC는 원격에 있는 프로시져(함수)를 로컬에 있는 것처럼 호출할 수 있도록 해주는 기술로 학습비용이 있기에 잘 사용되지 않았습니다.</p>
  <p>최근의 아키텍쳐 트렌드는 MSA를 기반으로 한 분산시스템으로 구성됩니다. MSA는 결국 각 서비스의 API를 호출하는 식으로 네트워크 통신을 하게 되는데, HTML/JSON보다는 gRPC/protobuf가 더 빠른 속도를 보이게 됩니다. 그로인해 서비스의 응답속도도 빨라질 수 있게됩니다.</p>
</details>

<details>
  <summary>:black_square_button: 쿠버네티스가 무엇인가요? 왜 쿠버네티스를 쓸까요?</summary>
  </br>
  <p></p>
</details>

### 웹서버의 동작과정

## 면접 꿀팁

회사의 기술스택에 관심을 가져보세요. 학습능력이 좋음을 어떤식으로 보여줄 수 있을까요?

본인이 수행한 프로젝트를 유의미한 트래픽이 나올정도로 해본 경험을 높게 평가하는 회사가 많습니다.

두괄식으로 답변하도록 합시다. (사실 힘듭니다. 그렇게 될 수 있게끔 연습 또 연습!)

프로젝트를 수행할 때, 내가 이 기술을 단순히 좋아보여서 사용한 것이 아니라, 많은 고민을 했음을 보여주도록 하세요. 가장 간단한 질문으로는 '왜 그 기술을 사용했나요?', '그 기술 말고 다른 기술은 왜 사용하지 않았나요?', '대체할만한 기술이 있나요?' 등이 있습니다.

[면접 꿀팁 영상!](https://youtu.be/4XNJFAPnZrY)

