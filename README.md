# GraphQL-Test

## Graph QL 이란?

Facebook에서 만든 쿼리언어이다. 등장한지 얼마되지 않았지만, 인기가 가파르게 올라가고 있다.

Graph QL 과 Structed Query Language 은 쿼리언어이다. 하지만 언어적 구조차이가 있다.
사용방법도 다르다. 
* sql은 DB System 에 저장되어있는 데이터를 효율적으로 가져오는것이 목적, 백엔드에서 사용
* gql은 클라이언트가 데이터를 서버로부터 효율적으로 가져오는게 목적, 클라이언트가 사용

서버에서 gql로 작성된 쿼리를 입력받아 처리한 값을 다시 클라이언트에게 돌려준다. 
HTTP API자체가 특정 DB나 플렛폼에 종속적이지 않은것과 마찬가지로 gql또한 종속적이지 않다.
일반적으로 gql의 인터페이스간 송수신은 네트워크 레이어 L7의 HTTP POST 메서드와 웹소켓 프로토콜을 이용한다.
필요에 따라서는 L4의 TCP/UDP를 활용하거나 L2형식의 이더넷 프레임을 활용할 수 있다.

![GraphQL 파이프라인](https://user-images.githubusercontent.com/48010847/66223332-2fdbc080-e70e-11e9-8dff-bd03c560e9a6.png)

---
## REST API와 비교

REST API는 URL, METHOD등을 조합하기 때문에 많은 Endpoint가 있지만, gql은 하나의 Endpoint다.
gql API에서는 불러오는 데이터의 종류를 쿼리 조합을 통하여 결정 한다. 
REST API는 각 Endpoint마다 DB SQL Query가 달라지지만 gql API는 gql 스키마의 타입마다 DB SQL Query가 달라진다.

![HTTP와 gql의 기술 스택 비교](https://user-images.githubusercontent.com/48010847/66223703-12f3bd00-e70f-11e9-9988-8df4741860ca.png)

![REST API와 GraphQL API의 사용](https://user-images.githubusercontent.com/48010847/66223713-18e99e00-e70f-11e9-9839-f359a1b57ec4.png)

위와 같이 GraphQL API를 사용하면 한번의 네트워크 호출로 처리 가능하다.
    
---

## GraphQL의 구조

### 쿼리/뮤테이션

쿼리와 뮤테이션, 응답내용의 구조는 매우 직관적이다. 요청하는 쿼리문과 응답내용은 거의 일치한다.

![GraphQL쿼리문과 응답데이터](https://user-images.githubusercontent.com/48010847/66233955-738ef400-e727-11e9-9ec1-dbe6ff3e457d.png)

gql에서는 쿼리와 뮤테이션을 나누는데 이 둘은 별 차이는 없지만, 쿼리는 데이터를 읽고, 뮤테이션은 데이터를 변조하는데 사용한다는 개념적인 규약

![일반 쿼리 - 오퍼레이션 네임 쿼리](https://user-images.githubusercontent.com/48010847/66259539-0cd40e00-e7ed-11e9-9d6b-20a5f2eb1aa3.png)

일반 쿼리 - 처음 시작이 중괄호'{' 문자
오퍼레이션 네임 쿼리 - 시작이 query
일반적인 클라이언트에서는 static한 쿼리문 작성 안함. 주로 정보를 불러올 때 id값이나 다른 인자값을 가지고 데이터를 불러옴
gql에는 쿼리에 변수라는 개념이 있는데, gql을 구현한 클라이언트에서는 이 변수에 프로그래밍으로 값을 할당 할 수 있는 함수 인터페이스가 존재.
react apollo client는 variables라는 파라미터에 원하는 값을 넣는다.

![오퍼레이션 네임 쿼리](https://user-images.githubusercontent.com/48010847/66259599-ba472180-e7ed-11e9-917f-2debb8f284fd.png)

오퍼레이션 네임 쿼리는 편리하다. 비유하자면 쿼리용 함수 이다. DB에서의 프로시져와 비슷함.
이 개념 덕에 REST API를 호출 할 때와는 다르게 한번의 통신으로 원하는 데이터를 가져올 수 있다.
DB의 프로시져는 DBA or 백앤드에서 작성 관리하지만, gql 오퍼레이션 네임 쿼리는 클라이언트에서 작성 관리한다.
gql을 사용하면 백앤드의 의존성이 줄어드나, 데이터 schema에 대한 협업 의존성은 존재.

### 스키마/타입

![스키마/타입](https://user-images.githubusercontent.com/48010847/66259645-4a856680-e7ee-11e9-83ce-72c4d10c4695.png)

* 오브젝트 타입: Character
* 필드: name, appearsIn
* 스칼라 타입: String, ID, Int 등
* 느낌표: 필수값을 의미
* 대괄호: 배열을 의미

### 리졸버






[여기서 퍼왔어요](https://tech.kakao.com/2019/08/01/graphql-basic/)
