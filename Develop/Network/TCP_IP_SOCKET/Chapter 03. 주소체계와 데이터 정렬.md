#Network 

- [[#소켓에 할당되는 IP 주소와 PORT 번호|소켓에 할당되는 IP 주소와 PORT 번호]]
	- [[#소켓에 할당되는 IP 주소와 PORT 번호#Internet Address|Internet Address]]
	- [[#소켓에 할당되는 IP 주소와 PORT 번호#데이터 전송 절차|데이터 전송 절차]]
	- [[#소켓에 할당되는 IP 주소와 PORT 번호#소켓의 구분에 활용되는 PORT 번호|소켓의 구분에 활용되는 PORT 번호]]
- [[#주소정보의 표현|주소정보의 표현]]
	- [[#주소정보의 표현#구조체 sockaddr_in의 멤버에 대한 분석|구조체 sockaddr_in의 멤버에 대한 분석]]
		- [[#구조체 sockaddr_in의 멤버에 대한 분석#sin_family|sin_family]]
		- [[#구조체 sockaddr_in의 멤버에 대한 분석#sin_port|sin_port]]
		- [[#구조체 sockaddr_in의 멤버에 대한 분석#sin_addr|sin_addr]]
		- [[#구조체 sockaddr_in의 멤버에 대한 분석#sin_zero|sin_zero]]
- [[#네트워크 바이트 순서와 인터넷 주소 변환|네트워크 바이트 순서와 인터넷 주소 변환]]
	- [[#네트워크 바이트 순서와 인터넷 주소 변환#Host Byte Order and Network Byte Order|Host Byte Order and Network Byte Order]]
	- [[#네트워크 바이트 순서와 인터넷 주소 변환#Endian Conversions|Endian Conversions]]
- [[#인터넷 주소의 초기화와 할당|인터넷 주소의 초기화와 할당]]
- [[#Series|Series]]

## 소켓에 할당되는 IP 주소와 PORT 번호

- IP(Internet Protocol)는 인터넷 상에서 데이터를 송수신할 목적으로 컴퓨터에게 부여하는 값
- PORT 번호는 컴퓨터에게 부여하는 값이 아닌, 프로그램 상에서 생성되는 소켓을 구분하기 위해 소켓에 부여되는 번호

### Internet Address

인터넷에 컴퓨터를 연결해서 데이터를 주고 받기 위해서는 IP주소를 부여 받아야 하며, 두 종류로 나뉜다.

- IPv4(Internet Protocol version 4) : 4byte 주소체계
- IPv6(Internet Protocol version 6) : 16byte 주소체계

[IPv4 기준 IP주소는 네트워크 주소와 호스트(컴퓨터를 의미) 주소로 나뉘며, 형태에 따라 A ~ E 클래스로 분류된다. ](https://m.blog.naver.com/kangyh5/221654455325)

![[1_wbYRk65-lnwsWYSFJ656xw.png]]

Network address(Network ID)란 네트워크의 구분을 위한 IP 주소의 일부

### 데이터 전송 절차
1. IP 주소의 Network address(Network ID)만을 참조하여 해당 네트워크를 구성하는 라우터에게 데이터 전송
2. 라우터가 전송된 데이터의 Host address(Host ID)를 참조하여 해당 호스트에게 전송
즉, 네트워크로 데이터가 전송된다는 것은 네트워크를 구성하는 Router또는 Switch로 데이터가 전송됨을 뜻한다.

>네트워크를 구성하기 위해 외부로부터 수신된 데이터를 호스트에게 전달, 호스트가 전달하는 데이터를 외부로 송신해주는 물리적 장치가 필요
>이를 라우터, 스위치라 하는데 그냥 적절한 소프트웨어가 설치, 구성된 컴퓨터에 지나지 않는다.
>기능적으로 라우터가 스위치보다 크지만 사실상 이 둘은 같은 의미로 사용된다.

### 소켓의 구분에 활용되는 PORT 번호

IP만 있다면 목적지 컴퓨터로 데이터를 전송할 순 있지만 데이터를 수신해야하는 최종 목적지인 응용 프로그램까지 데이터를 전송할 수 없다.
NIC(Network Interface Card)라는 데이터 송수신장치가 하나 이상 달려있다.
IP는 데이터를 NIC를 통해 컴퓨터 내부로 전송하는데 사용하지만 컴퓨터 내부로 전송된 데이터를 소켓에 적절히 분배하는 작업은 운영체제가 담당한다.
NIC를 통해서 수신된 데이터 안의 PORT번호를 참조해 일치하는 PORT번호의 소켓에 데이터를 전달한다.

이렇듯 PORT 번호는 하나의 운영체제 내에서 소켓을 구분하는 목적으로 사용되기 때문에 동일한 PORT 번호를 둘 이상의 소켓에 할당할 수 없다.

## 주소정보의 표현

응용 프로그램 상에서의 IP 주소와 PORT 번호 표현을 위한 구조체가 정의되어 있다.
```c
struct sockaddr_in
{
	sa_family_t    sin_family;  // 주소체계(Address Family)
	uint16_t       sin_port;    // 16비트 TCP/UDP PORT 번호
	struct in_addr sin_addr;    // 32비트 IP주소
	char           sin_zero[8]; // 사용되지 않음
}

struct in_addr
{
	in_addr_t      s_addr;      // 32비트 IPv4 인터넷 주소
}
```

### 구조체 sockaddr_in의 멤버에 대한 분석

#### sin_family

| Address Family | Means                                       |
| -------------- | ------------------------------------------- |
| AF_INET        | IPv4 인터넷 프로토콜에 적용하는 주소체계    |
| AF_INET6       | IPv6 인터넷 프로토콜에 적용하는 주소체계    |
| AF_LOCAL       | 로컬 통신을 위한 유닉스 프로토콜의 주소체계 |

#### sin_port

16비트 PORT 번호를 네트워크 바이트 순서로 저장한다.

#### sin_addr

32비트 IP 주소정보를 네트워크 바이트 순서로 저장한다.
간단히 32비트 정수자료형이다.

#### sin_zero

단순히 구조체 sockaddr_in의 크기를 구조체 sockaddr과 일치시키기 위해 삽입된 멤버이며 반드시 0으로 채워야 한다.

## 네트워크 바이트 순서와 인터넷 주소 변환

### Host Byte Order and Network Byte Order

CPU가 데이터를 메모리에 저장, 데이터를 해석하는 방식은 다음과 같이 두 가지로 나뉜다.

- Big Endian : 상위 바이트의 값을 작은 번지수에 저장하는 방식
- Little Endian : 상위 바이트의 값을 큰 번지수에 저장하는 방식

![[little_endian_vs_big_endian.png]]

Host Byte Order가 다른 CPU가 데이터를 주고 받을 때 데이터 해석에 문제가 생길 수 있기 때문에
네트워크를 통해 데이터를 전송할 때에는 통일된 기준(Big Endian)으로 데이터를 전송하기로 약속
-> Network Byte Order

### Endian Conversions

```c
// short형 데이터를 호스트 바이트 순서에서 네트워크 바이트 순서로 변환
unsigned short htons(unsigned short);

// short형 데이터를 네트워크 바이트 순서에서 호스트 바이트 순서로 변환
unsigned short ntohs(unsigned short);

// long형 데이터를 호스트 바이트 순서에서 네트워크 바이트 순서로 변환
unsigned long htonl(unsigned long);

// long 데이터를 네트워크 바이트 순서에서 호스트 바이트 순서로 변환
unsigned long ntohl(unsigned long);
```

Big Endian으로 동작하는 시스템에서 sockaddr_in 구조체 변수에 값을 채울 때 네트워크 바이트 순서로 변환하지 않아도 동작은 하지만 Endian에 상관없이 코드를 작성하는 것이 좋다.

>데이터 송수신 시에는 네트워크 바이트 순서를 자동으로 바꾸어 주기 때문에
>sockaddr_in 구조체 변수에 데이터를 채울 때 이외에는 바이트 순서를 신경쓰지 않아도 된다.

## 인터넷 주소의 초기화와 할당

```c
#include <arpa/inet.h>

in_addr_t inet_addr(const char *string); // 성공 시 빅 엔디안으로 변환된 32비트 정수 값, 실패 시 INADDR_NONE
```
## Series

[[Chapter 01. 네트워크 프로그래밍과 소켓의 이해]]
[[Chapter 02. 소켓의 프로토콜과 그에 따른 데이터 전송 특성]]
[[Chapter 03. 주소체계와 데이터 정렬]]