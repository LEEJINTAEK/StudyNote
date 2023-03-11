# 📖 DNS 동작

<br />
<br />

## DNS란??

인터넷을 이용하여 웹 서핑이나 이메일 등을 사용할 때 도메인 이름(www.naver.com) 과 같이
입력하고 접속한다. <br />
실제 서버는 ip주소로 통신하지만, 우리는 기억하기 쉬운 도메인 이름을 사용하는 것이다. <br />
**결국 도메인 주소(www.naver.com)을 ip주소로 변환하는 과정이 필요한데 이것을 담당하는 것이 DNS이다**

<br />
<br />

## DNS 동작 과정?

<br />

**1. 반복적 질의**

<img width="500" alt="DNS" src="https://user-images.githubusercontent.com/109197023/222902526-87c66732-d947-4443-9952-615203edc370.PNG">

위를 참조하여 동작과정 예시를 보자

<br />

```plaintext

1. DNS Query (from Web Browser to Local DNS) : "제가 원하는 웹 사이트의 IP 주소를 알고 계신가요?"
 Local DNS 서버에게 전달

2. DNS Query (from Local DNS to Root DNS) : "제가 원하는 웹 사이트의 IP 주소를 알고 계신가요?"
 Root DNS서버에게 전달

3. DNS Response (from Root DNS to Local DNS) : "저는 모르지만 , Com 도메인을 관리하는 네임서버의 이름과 IP 주소를 알려드릴 테니 거기에 물어보세요"

4. DNS Query (from Local DNS to com NS) : “ 안녕하세요. www. naver. com의 IP 주소를 알고 계신가요?"

5. DNS Response (from com NS to Local DNS) : "저는 모르지만 , Com 도메인을 관리하는 네임서버의 이름과 IP 주소를 알려드릴 테니 거기에 물어보세요"

6. DNS Query (from Local DNS to naver. com NS) : “ 안녕하세요. www. Naver .com의 IP 주소를 알고 계신가요?"

7. DNS Response (from naver .com NS to Local DNS) : "저는 모르지만 해당 웹은 www. g.naver. com이라는 이름으로
통해요. g.naver .com 도메인을 관리하는 네임서버의 이름과 IP 주소를 알려드릴테니 거기에 물어보세요"

8. DNS Query (from Local DNS to g.naver. com NS) : “ 안녕하세요. www. g.naver. com의 IP 주소를 알고 계신가요?"

9. DNS Response (from g.naver .com NS to Local DNS) : " 네 www. g.naver .com의 IP 주소는
222.222.222.22와 333.333.333.33입니다"

10. DNS Response (from Local DNS to Web Browser) : "네 www. naver .com의 IP 주소는
222.222.222.22와 333.333.333.33입니다"

```

<br />
<br />

**2. 재귀적 질의**

<br />

<img width="400" alt="재귀적" src="https://user-images.githubusercontent.com/109197023/224461526-6990deef-1a3c-4a8c-bf0e-c78bcf58d082.PNG">

<br />

```plaintext

1. 로컬 DNS에게 요청을 함 -> 로컬은 해당 정보를 가지고 있지 않다면 루트 DNS 서버에게 요청하는 IP 알고 있냐고 물어봄

2. 루트 DNS 서버는 모르기 때문에 최상위 DNS 서버에게 물어봄

3. 최상위 DNS 서버도 모르기 때문에 책임 DNS 서버에게 물어봄

4. 책임 DNS 서버는 알고 있기 때문에 알려줌. (최상위 DNS에게 다시)

5. 최상위 DNS는 받은 정보를 다시 루트 DNS에게 알려줌

6. 루트 DNS는 로컬 DNS에게 받은 정보를 알려줌

7. 로컬 DNS는 최종적으로 사용자에게 받은 정보를 전달하고 자신의 DNS 레코드에 해당 정보를 추가함.
```

- 이렇게 재귀적 질의는 재귀적인 방법을 이용하여 질의를 하는것이고 반복적 질의는 DNS 서버마다 로컬 DNS가 반복적으로 질문을 하는 방법을 말한다.
- 재귀적 질의인지 반복적 질의인지는 와이어샤크로 dns 프로토콜을 뜯어봐야한다. 어플리케이션 계층의 정보중에 Recursion desired 가 1로 되어 있으면 재귀적 질의로 되있는거고 0으로 되어있으면 재귀적 질의를 사용하는 것이다.

<br />
<br />

(추가) 자주쓰는 도메인 네임

```plaintext
Kr : 각 국가별 사용을 위해 정의한 도메인으로 ISO 3166 [4]에서 정의하는 국가 코드에 기반함

com : 기업과 같은 상용 조직을 위한 도메인

edu : 교육 기관들을 위한 도메인

net : 네트워크 서비스 제공자와 관련된 시스템을 위한 도메인
```

<br />
<br />

## 출처

> https://www.youtube.com/watch?v=imRGWxRU65Q

> https://ja-gamma.tistory.com/entry/DNS%EA%B0%9C%EB%85%90%EB%8F%99%EC%9E%91%EC%9B%90%EB%A6%AC

> https://wogh8732.tistory.com/24
