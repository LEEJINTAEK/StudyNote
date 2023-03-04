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

<img width="388" alt="DNS" src="https://user-images.githubusercontent.com/109197023/222902526-87c66732-d947-4443-9952-615203edc370.PNG">

위를 참조하여 동작과정 예시를 보자

<br />

```plaintext

1. DNS Query (from Web Browser to Local DNS) : "제가 원하는 웹 사이트의 IP 주소를 알고 계신가요?" Local DNS 서버에게 전달

2. DNS Query (from Local DNS to Root DNS) : "제가 원하는 웹 사이트의 IP 주소를 알고 계신가요?" Root DNS서버에게 전달

3. DNS Response (from Root DNS to Local DNS) : "저는 모르지만 , Com 도메인을 관리하는 네임서버의 이름과 IP 주소를 알려드릴 테니 거기에 물어보세요"

4. DNS Query (from Local DNS to com NS) : “ 안녕하세요. www. naver. com의 IP 주소를 알고 계신가요?"

5. DNS Response (from com NS to Local DNS) : "저는 모르지만 , Com 도메인을 관리하는 네임서버의 이름과 IP 주소를 알려드릴 테니 거기에 물어보세요"

6. DNS Query (from Local DNS to naver. com NS) : “ 안녕하세요. www. Naver .com의 IP 주소를 알고 계신가요?"

7. DNS Response (from naver .com NS to Local DNS) : "저는 모르지만 해당 웹은 www. g.naver. com이라는 이름으로 통해요. g.naver .com 도메인을 관리하는 네임서버의 이름과 IP 주소를 알려드릴테니 거기에 물어보세요"

8. DNS Query (from Local DNS to g.naver. com NS) : “ 안녕하세요. www. g.naver. com의 IP 주소를 알고 계신가요?"

9. DNS Response (from g.naver .com NS to Local DNS) : " 네 www. g.naver .com의 IP 주소는 222.222.222.22와 333.333.333.33입니다"

10. DNS Response (from Local DNS to Web Browser) : "네 www. naver .com의 IP 주소는 222.222.222.22와 333.333.333.33입니다"

```

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
