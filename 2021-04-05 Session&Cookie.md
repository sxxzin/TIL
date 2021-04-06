## Session
* 하나의 클라이언트가 프로그램을 시작해서 종료 될 때까지를 하나의 Session 이라 함. 하나의 세션 동안 여러 번의 요청과 응답이 반복 될 수 있 다.
* Session관리
    * 하나의 Session동안 사용자와 관련된 Data를 계속 유지 하도록 관리하는 것
    * Http Protocol의 Stateless한 특징의 해결책
* Session 관리방법 
    * Session
    * Cookie
    * URLRewriting
## Cookie를 이용한 Session관리
* 쿠키
    * 서버가 브라우저(client)로 전송하는 작은 Text 정보이다
    * 클라이언트의 정보를 클라이언트 컴퓨터에 저장한다.
    * 클라이언트는 서버에 요청시 자신이 가진 데이터를 Http요청정보에 담아서 보내며 key-value형태로 관리된다..
    * 저장 데이터(쿠키정보)는 문자열만 가능하고 저장양에도 제한이 있다. (데이터 크기 : 4KB, 사이트당 :20개, 총 : 300개)
* 장점
    * 서버의 부하를 줄인다.
* 단점
    * 관리할수있는데이터의종류,크기제약,보안상취약
* 쿠키생성
    * javax.servlet.http.Cookie를 사용
    ``` 
    Cookie c = new Cookie(“popup”,”no”);
    response.addCookie(c); //응답시 쿠키가 전송된다.
    ``` 
* 클라이언트가 보내온 쿠키정보 조회
    ``` 
    Cookie [] cc = request.getCookies(); //보내온 쿠키가 없으면 빈 배열 리턴 
    ```
* 주요메소드
    * String getName(
    * String getValue()
    * setMaxAge(int sec) // 24*60*60 =하루동안 유지

## Session을 이용한 Session관리
* 클라이언트의 정보를 Server측에 저장.
* Javax.servlet.http.HttpSession객체를 이용하여 관리.
* 장점
    * 저장 데이터 타입이나 크기에 제한 없다. 
    * 보안상유리
* 단점
    * 서버에부담
* 생성방법
    ```
     HttpSession session = request.getSession();
     ```
    * 기존 세션이 있으면 기존 세션객체를, 없으면 새로 생성해서 return 
    ```
     HttpSession session = request.getSession(false);
     ```
    * 기존 세션이 있으면 기존 세션객체를, 없으면 null 리턴
* HttpSession의 주요메소드
    * setAttribute(String name, Object value) 
    * Object getAttribute(String name)
    * removeAttribute(String name)
    * setMaxInactiveInterval(int sec)
    * invalidate()
