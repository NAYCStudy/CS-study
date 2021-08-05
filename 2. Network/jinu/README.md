-----

 ### OSI 7계층  

 OSI 7계층을 생각나는대로 적어보자!  
 - 물리 - 데이터링크 - 네트워크 - 전송 - 세션 - 표현 - 응용   
 - 끝..   공부해보자   
 
 #### 1. OSI 7계층?  &  OSI 7 Layer vs TCP 4 Layer  
 <img src="./images/layer.png" width="40%">   
 
 - OSI 모델은 국제 표준화 기구에서 개발한 네트워크 계층 모델입니다.   
 - 서로 통신을 위해 송신자의 데이터는 L7(응용)계층에서 L1(물리)계층으로 내려가서 수신자의 L1(물리)계층을 통해 전달되며 다시 수신자의 L7(응용)계층까지 올라가서 데이터 전송이 완료됩니다.  
 - L7 -> L1 과정을 Multipexing  /  L1 -> L7 과정을 Demultiplexing  
 - Multiplexing : Data에 Header를 추가하는 과정   
 - Demultiplexing : 순수 Data만 추출하는 과정   
 - 각 계층끼리는 통신을 위한 프로토콜이 존재합니다.  
 
 <br>   
 
 <img src="./images/layer2.png" width="40%">   
 
 AH : Application Header   
 PH : Presentation Header   
 SH : Session Header   
 TH : Transport Header   
 NH : Network Header / NT : Network Tail   
 DH : Data Link Header / DT : Data Link Tail   
 
 <br>  
 
 #### 2. 각 계층  
 
 ##### 물리계층 (L1)   
  <img src="./images/l1.png" width="30%">   
  
 - 프로토콜 : RS-232  
 - 장비 : 허브, 리피터  
 - 역할 : 전달된 데이터를 전기적 신호(bit 단위)로 변환하여 통신  
 - 단위 : bit
 - 정의 : 실제 장치들을 연결하기 위해 필요한 전기적, 물리적 세부사항들을 정의하는 계층  

 <br>  
 
 ##### 데이터 링크 계층 (L2)   
 <img src="./images/l2.jpg" width="30%">     
 
 - 프로토콜 : HDLC, PPP, Frame Relay, ATM  
 - 장비 : 스위치, 브릿지  
 - 역할 : 오류 없는 데이터 전송을 위한 상위 계층에서 받은 패킷을 Frame으로 변환   
 - 단위 : Frame(프레임)  
 - 정의 : 노드 간 오류제어, 흐름제어, 회선제어 기능을 수행하는 계층  

 * Frame Relay : 하나의 물리적 회선에 여러 개의 논리 회선인 가상회선(Pemanent Vitual Circuit)을 만들어 마치 전용선처럼 사용하는 서비스, L2 WAN 프로토콜  
    => 비싼 망 구성 물리적 비용을 줄일 수 있다.  
 
 <br>    
 
 ##### 네트워크 계층(L3)   
  <img src="./images/l3.jpg" width="30%">     
  
 - 프로토콜 : IP, ARP, RARP, ICMP, IGMP    
 - 장비 : 라우터, 스위치(L3)   
 - 역할 : 패킷을 분석하여 네트워크를 통해 출발지에서 목적지까지의 최적 경로를 선택    
 - 단위 : Packet(패킷) <- 데이터가 나누어진 여러 조각   
 - 정의 : 전송계층이 요구하는 QoS를 위한 수단을 제공하는 계층, 라우팅, 패킷 포워딩 등을 수행   
 
 * ARP : 주소 결정 프로토콜 : IP -> MAC   
 * RARP : MAC -> IP    
 * ICMP : 인터넷 제어 메시지 프로토콜 : 오류 메시지를 전송받는데 사용되는 프로토콜   
 
 #### 공유기 vs 라우터?  
  -> 공유기 : 단일회선, 단일 IP 에서 하위 클라이언트 장비들이 인터넷 연결을 가능하게 해주는 장비입니다. NAT 장비로서 공인 IP를 사설 IP로 분배하여 각 PC, IoT 장비에 분배하는 역할을 수행합니다.      
      -> 즉, 가정에서 할당받는 1개의 IP를 통해 다양한 기기가 공유기를 통해 사설 IP 를 할당받아 네트워크에 연결되도록 합니다.  
 
  -> 라우터 : 서버와 클라이언트간 효율적으로 연결을 분배하고 다양한 패킷을 분산하여 보내고 받을 수 있는 장비입니다. 공인 IP를 보내고 받는 역할을 하며 목적지까지의 최적의 경로를 설정하는 역할을 수행합니다.  


 <br>
 
 ##### 전송 계층(L4)  
  <img src="./images/l4.jpg" width="30%">   
  
  - 프로토콜 : TCP, UDP, RTP  
  - 장비 : 게이트웨이, L4 스위치  
  - 역할 : 양 끝단의 사용자들이 신뢰성 있는 __데이터를__ 주고 받을 수 있게 해주는 역할, Port를 통해 패킷을 생성 & 전송합니다.   
  - 단위 : 세그먼트(Segment)    
  - 정의 : End-to-End 통신을 다루며 신뢰성 있는 패킷을 생성 및 전송하고 오류검출, 복구, 흐름제어 등에 사용되는 프로토콜  
  (TCP, UDP는 뒤에서 다루겠습니다.)  
  
 <br>
 
 ##### 세션 계층(L5)  
  <img src="./images/l5.jpg" width="30%">    
  
  - 프로토콜 : SSH, TLS, NetBIOS  
  - 역할 : Port 번호를 기반으로 연결하며 통신 장치간 상호작용에 대해 설정하고 동기화합니다, TCP/IP 세션을 생성/파기하는 역할을 합니다.(OS에서 수행)  
  - 세션이란 __데이터가 통신하기 위한 논리적인 연결을 뜻합니다.__   
  - 단위 : 메시지  
  - 정의 : 통신 세션을 구성하는 계층으로 Port 기반으로 연결하여 상호간 연결을 유지하게 하는 프로토콜  

 <br>
 
  ##### 표현 계층(L6)   
  - 프로토콜 : MPEG, JPG, PAP, SMB  
  - 역할 : 사용자(응용) 계층으로부터 받은 데이터를 하위 계층으로 보내기 전 통신에 적당한 형태로 변환하는 역할을 합니다. (EBCDIC -> ASCII , 확장자 구분을 통해 JPG, GIF, TXT 등 표현하는 역할 등)     
  - 반대로 세션에서 받은 객체 메시지는 응용 계층에 맞게 변환하는 역할도 수행합니다.   
  - 단위 : 메시지, 데이터  
  - 정의 : 코드 간 번역을 담당하여 데이터의 형식 차이를 다루는 부담을 덜어주며 인코딩, 암호화 등을 통해 적절한 변환을 수행하는 프로토콜   

 <br>

 ##### 응용 계층(L7)   
  - 프로토콜 : DHCP, DNS, FTP, HTTP, TELNET, SMTP   
  - 역할 : 응용 SW를 도와주는 계층  
  - 단위 : 메시지, 데이터   
  - 정의 : 응용 프로세스와 직접적으로 연결을 통해 응용 서비스를 수행하도록 돕는 프로토콜입니다.  

 * FTP : 파일 전송 프로토콜   
 * SMTP : 메일 전송 프로토콜   

-----


<br><br>  

### TCP/IP   

<br>  

 #### TCP/IP 란?   
  : 통신을 하기 위한 규칙 중 하나로써 일반적으로 메일, 컴퓨터간 파일 전송, 원격 로그인 등의 통신을 지원합니다.   
  : 데이터가 목적지에 잘 도착할 수 있도록 보장하는 통신 규약   
  
  <br>
  
 - TCP : 두 호스트가 교환하는 데이터와 승인 메시지 형식을 정의하여 신뢰성있는 정보 전달을 목표로 합니다.  
   -> TCP는 패킷에 일련 번호를 부여하여 데이터 손실을 최소화하고 순서를 재조합하여 클라이언트에게 전달할 수 있게 해줍니다. & 데이터가 손실된 경우 재전송을 요청   
   -> 따라서 신뢰성이 높은 프로토콜   
 
 - IP : 컴퓨터 간 데이터 전송을 위해 서로의 주소가 필요합니다. Internet Protocol은 4byte로 이루어진 주소를 의미하며 192.168.0.1 과 같이 나타냅니다.  
   -> 단지 데이터가 전달 될 수 있도록 주소만 가지는 역할을 담당합니다.  
   -> MAC(물리적인 장비의 고유 주소) 주소와는 다르게 IP는 통신사(다른 주체)로 부터 할당 받는 것이므로 변동될 수 있습니다.  
 
 - TCP/IP : 통신을 위해 IP 기반으로 TCP가 사용되어서 TCP/IP 라고 불립니다.  
 - TCP : 데이터 신뢰, 추적 / IP : 주소 배달지 

-----

<br>  

### TCP vs UDP  

 <br>  
 
 #### TCP와 UDP  
 * 두 프로토콜 모두 데이터 전송을 목적으로 하는 전송계층 프로토콜입니다.  
 - TCP : 인터넷 상에서 데이터 전송을 위해 IP와 함께 사용되는 프로토콜   
 - UDP : 데이터를 데이터그램 단위로 처리하는 프로토콜   

 #### 특징   
 - TCP : 신뢰성있는 데이터 전송을 보장하며 패킷에 일련 번호를 부여하여 데이터 손실을 최소화하고 순서를 재조합하여 클라이언트에게 전달   
 - UDP : 비연결형 프로토콜로 연결을 위해 할당되는 논리적인 경로가 없습니다. 각 패킷들은 서로 다른 경로를 통해 전송되고 패킷은 독립적으로 이동하여 클라이언트에게 전달  
 
 <br>  
 
 __TCP__  
 1. 연결형 서비스로 가상 회선 방식 사용(출발 - 도착 연결을 위한 논리적 경로를 배정)    
 2. 3(연결) and 4(해제) way hand-shaking 과정을 통해 통신   
 3. 높은 신뢰성  
 4. 흐름제어, 혼잡제어, 오류제어  
 5. UDP 대비 상대적으로 느리다.  -> 패킷에 대한 응답을 필요로 하기 때문 (CPU 자원 소모, 시간 지연)  
 6. 서버 소켓은 연결만 담당합니다.  
 7. 스트림 전송 (데이터 크기 무제한)   
 8. 서버와 클라이언트는 1:1로 연결  

 __UDP__   
 1. 비연결형 서비스로 데이터그램 방식 사용  
 2. 정보를 보내고 받는다는 신호를 서로간에 주고받지 않습니다.  비 신뢰성 & 실시간 속도  
 3. 신뢰성이 낮다.  
 4. UDP 헤더의 CheckSum 필드를 통해 최소한의 오류만 검출합니다.  
 5. TCP 대비 상대적을 빠릅니다.  
 6. UDP는 논리적 연결 자체가 없어서 Connect 함수가 필요없고 서버 소켓과 클라이언트 소켓의 구분이 없습니다.  
 7. 소켓이 아닌 IP 기반 데이터 전송  
 8. 흐름제어 X  
 9. 서버와 클라이언트는 1:1 ~ N:N 으로 연결  
 
 <br>  
 
 따라서, TCP 는 신뢰성을 필요로하는 메일, 파일 전송 등과 같은 통신에 사용 / UDP는 신뢰성이 낮지만 실시간 전송 속도에 최적화되어 실시간 스트리밍과 같은 통신에 사용됩니다.  
 
 <br><br>  
 
 -----

### TCP & UDP 헤더를 들여다보자  

<br>  

 #### TCP Header   
  <img src="./images/tcpheader.jpg" width="80%">   
  
  - Source Port Address : Well-Known port(0 to 1023), Registered port(1024 to 49151), Dynamic port(49152 to 65535)    
  
  - Destination Port Address : 목적지 어플리케이션이 사용하는 포트 번호   

  
  |Port|Service|
  |:-:|:-|
  |21|FTP(파일)|
  |23|TELNET(장비관리)|
  |25|SMTP(메일)|
  |80|HTTP(웹)|
  |110|POP3(메일)|
  |194|IRC|
  |443|HTTPS(Secure)|
  |8080|Alternative HTTP|
  
  
  - Sequence number : 전송 데이터의 모든 바이트에는 고유 일련 번호가 부여되어 세그먼트 순서가 어긋나거나 분실되어도 이를 재배열 조합할 수 있습니다.   
  - Acknowledgment number : 다음 세그먼트(전송 계층 단위)를 수신할 준비가 되었다는 신호입니다.  
  - Control flags : 8개의 서로 다른 제어 비트   
     ###### CWR : Congestion Window Reduced) – 혼잡 윈도우 크기 감소  
     ######  ECN : Explicit Congestion Notification) – 혼잡을 알림   
     ######  URG(Urgent) : Urgent Pointer 필드가 가리키는 세그먼트 번호까지 긴급 데이터를 포함되어 있다는 것을 뜻한다  
      ######  이 플래그가 설정되지 않았다면 Uregent Pointer 필드는 무시되어야 한다.  
     ######  ACK(Acknowledgment) : 확인 응답 메시지  
     ######  PSH(Push) : 데이터를 포함한다는 것을 뜻한다.  
     ######  RST(Reset) : 수신 거부를 하고자 할때 사용  
     ######  SYN(Synchronize) : 가상 회선이 처음 개설될 때 두 시스템의 TCP 소프트웨어는 의미 있는 확인 메시지를 전송하기 위해 일련 번호를서로 동기화해야 한다.  
     ######  FIN(Finish) : 작업이 끝나고 가상 회선을 종결하고자 할 때 사용  

  - checksum : TCP 세그먼트의 내용이 유효한 내용인지 검증 & 손상 여부를 검사할 수 있는 CheckSum 값  
  

 #### UDP Header  
  <img src="./images/udpheader.png" width="80%">   
  
  - Source Port : 송신자의 포트번호  Well-Known port(0 to 1023), Registered port(1024 to 49151), Dynamic port(49152 to 65535)    
  - Destination Port : 수신자의 포트번호  Well-Known port(0 to 1023), Registered port(1024 to 49151), Dynamic port(49152 to 65535)    
  - UDP Length : UDP 헤더와 데이터를 합친 길이 정보  
  - UDP CheckSum : UDP 헤더와 데이터를 모두 포함하여 체크하기 위한 최소한의 CheckSum   

 
 
 -----
  
 
 <br><br><br>
 
 ### TCP의 3-way-handshake와 4-way-handshake   
 
 <br>
 
 - 신뢰성 있는 연결을 통해 안전한 통신 방식   
 - 3 way handshake : 연결을 맺을때!   
 - 4 way handshake : 연결을 끊을때!   

 <br>

 - 3 way handshake : TCP/IP 프로토콜을 통해 응용프로그램이 데이터를 전송하기 전 __정확한 연결 및 전송을 보장하기 위헤 상대방과 사전에 세션을 수립하는 과정__ 을 의미합니다.   
 1. Client -> Server : TCP SYNC  : 서버에 접속을 요청하는 SYN 패킷을 전송하고 클라이언트는 SYN/ACK 응답을 기다립니다.  
 2. Server -> Client : TCP SYNC ACK  : 서버는 SYN 요청을 받고 클라이언트에게 알겠다는 ACK 와 SYN flag 가 설정된 패킷을 발송한 후 클라이언트의 ACK 응답을 기다립니다.   
 3. Client -> Server : TCP ACK  : 클라이언트는 서버로부터 ACK 와 SYN 신호르 받아 ACK 를 보내고 연결이 성사됩니다.   
 <img src="./images/3way.png" width="40%">   
 
 <br>
 
 - 4 way handshake : TCP/IP 프로토콜의 __연결된 세션을 종료하기 위해__ 수행되는 절차입니다.    
 1. Client -> Server : 클라이언트가 서버에 연결을 종료하겠다는 FIN flag를 전송한다.    
 2. Server -> Client : 서버는 ACK 메시지를 보내고 자신의 통신이 끝날때까지 기다리는 상태가 됩니다.   
 3. Server -> Client : 서버가 통신이 끝났으면 연결이 종료되었다고 클라이언트에게 FIN 플래그를 전송한다.   
 4. Client -> Server : 클라이언트는 서버에 ACK 신호를 보낸다.   
 <img src="./images/4way.png" width="40%">    
 
 
 - 만약, 서버에서 클라이언트로 FIN을 전송하기 전에 전송한 패킷이 Routing 지연이나 패킷 유실로 인한 재전송으로 인해 FIN 패킷보다 늦게 도착하는 상황이 발생한다면??   
  : Client에서 세션을 종료시킨 후 뒤늦게 도착하는 패킷이 있을 수 있으니 일정시간동안 세션을 유지하고 잉여패킷을 기다리는 과정을 거칩니다. 이를 Time_Wait 라고 합니다.   
  
 <br><br> 
 
 ### HTTP vs HTTPS(Http + SSL)    
  #### HTTP? 서버/클라이언트 모델을 따라 데이터를 주고 받기 위한 프로토콜 입니다.   
  
  - HTTP 는 기본 포트로 80 포트를 사용하며 대체 포트인 8080, 8081이 있습니다.   
  - HTTPS 는 기본 포트로 443 포트를 사용하며, 네트워크 상에서 중간에 제 3자가 정보를 볼 수 없도록 공개키 암호화를 지원합니다.   
  - SSL : Secure Socket Layer   
  
  <br>
  
  - HTTP는 어플리케이션 레벨의 프로토콜로 TCP/IP 위에서 작동합니다. HTTP는 상태를 가지고 있지 않는 Stateless(상태정보X) 프로토콜이며 Method, Path, Version, Header, Body로 구성됩니다. 
  - 하지만, HTTP는 평문데이터를 전송하는 프로토콜이기에 HTTP로 기밀 정보를 주고 받기에는 보안상 문제가 발생합니다.   
  - HTTPS는 HTTP에서 데이터 암호화가 추가된 프로토콜이며 __공개키 암호화__ 를 사용합니다.(실제 데이터 암호화느 대칭키, 키 교환에는 공개키 암호화를 사용 <- 속도개선)    
  - 공개키[비대칭키](RSA) 암호화 : 비밀키 & 공개키  
   -> 공개키 : 모두에게 공개가능한 키   
   -> 개인키 : 나만 가지고 비밀로 해야하는 키    
  - 공개키 암호화 : __공개키__ 로 암호화하면 __개인키__ 로만 복호화할 수 있습니다. (누군가 개인키를 가진사람에게 비밀로 정보를 전송하는 용도)   
  - 개인키 암호화 : __개인키__ 로 암호화하면 __공개키__ 로만 복호화할 수 있습니다. (자기가 자기 자신임을 인증하는 용도)    
  
  암호문을 B만 볼 수 있도록 기밀성을 유지하여 전송    
  <img src="./images/publickey1.png" width="40%">    
   
  누구나 볼 수 있지만 A가 서명한 것임을 인증   
  <img src="./images/publickey2.png" width="40%">    
  
  <br>
  
  #### HTTPS 동작 과정!  
  - HTTPS 는 데이터를 암호화하여 전송하기에 제 3자가 데이터를 탈취하더라도 기밀을 유지할 수 있습니다. 서버와 클라이언트 사이에는 클라이언트가 데이터를 확인하기 위해 복호화 할 수 있는 공개키가 필요하게 됩니다. 일반적으로는 인증된 기관으로부터 공개키를 전송하여 인증서를 발급하는 방식으로 HTTPS 통신이 이루어집니다.   
  1. A는 HTTP 기반 애플리케이션에 HTTPS를 적용하기 위해 공개키/개인키를 발급합니다.   
  2. 인증된 기관에 A의 공개키를 저장하는 인증서 발급을 요청합니다. (공개키가 포함된 인증서)   
  3. 인증 기관은 이름, 서버의 공개키, 서버 정보를 기반으로 인증서를 생성하고 인증기관의 개인키로 암호화하여 A에게 이를 제공합니다. (인증서 발급자가 인증기관임을 증명)   
  4. A기업은 클라이언트에게 암호화된 인증서를 제공합니다. (인증서 제공) 
  5. 브라우저는 인증 기관의 공개키를 이미 갖고있어 암호화된 인증서를 복호화할 수 있습니다. (CA의 공개키를 통해 인증서 복호화 가능 -> CA의 인증서임을 검증 가능)  
  6. 암호화된 인증서를 복호화하여 A기업의 공개키를 알 수 있고 이를 통해 데이터를 암호화하여 요청을 전송합니다. (A의 공개키로 암호화하여 데이터 요청 -> A만 개인키로 복호화 가능)  
  
  따라서, 단순한 정보 조회를 위한 통신이라면 HTTP, 민감한 정보가 포함되었다면 암호화 기술이 포함된 프로토콜인 HTTPS를 사용하면 됩니다.    
  
  <br><br> 
  
 ### HTTP 요청과 응답 Header   
  #### 요청    
  - HTTP 요청의 헤더 정보는 크게 3부분으로 분류할 수 있습니다.   
  - 일반헤더, 요청/응답 헤더, 엔티티 헤더  
  
  
 1. 일반헤더 : HTTP Body와는 관련 없고 생성된 날짜 및 시간, 연결과 같은 통신에 대한 일반 정보가 포함됩니다. 요청/응답에 공통으로 사용됩니다.    
 &nbsp; -  Date, Connection, Content-Length, Cache-Control, Content-Type    


 2. 요청(Request)/응답(Response) 헤더 : 요청과 응답에 대한 정보가 들어있는 헤더이며 URL, Method, 브라우저 정보 등이 포함됩니다.     
 &nbsp;  - Request. Host, User-Agent, Accept, Cookie, Origin, Authorization    
 &nbsp;  - Response. Server, Access-Control-Allow-Origin, Allow, Location, Content-Security-Policy, Access-Control-Expose-Header   
  
  
 3. 엔티티 헤더 : 메시지, Body 본문에 대한 정보가 포함됩니다. 컨텐츠의 길이, 언어, 인코딩, 만료날짜 등의 정보가 포함되어 있습니다.    
 &nbsp;  - Content-Length, Content-Language, Content-Encoding   


 <br>  
 
 * Request Method  
   GET(URI 요청, Query String)    
   POST(Body에 데이터 전송)    
   HEAD(Header 정보만 요청)   
   PUT(Body에 데이터 전송)   
   PATCH(단 1개의 정보만 수정)    
   DELETE(URI 요청, 삭제), OPTIONS       
  


 ### CORS   
  #### Cross Origin Resource Sharing : 교차 출처 리소스 공유   
  - 다른 출처의 자원에 접근할 수 있는 권한을 부여하도록 브라우저에게 알려주는 체제이며 보안상의 이유로 기본적으로 브라우저는 교차 출처의 요청을 제한합니다.   
  - CORS 허용의 경우  
   1. XMLHttpRequest  
   2. WebGl 텍스쳐   
   3. drawImage()를 사용한 이미지/비디오 프레임  
   4. 이미지로부터 호출되는 CSS   

