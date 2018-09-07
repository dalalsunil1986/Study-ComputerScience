# DATABASE
체계화된 데이터의 모임이다. 즉, 작성된 목록으로써 여러 응용 시스템들의 통합 된 정보들을 저장하여 운영할 수 있는 공용 데이터들의 묶음이다.

* 공용 데이터 (Shared Data) : 다양한 사용자들이 필요한 정보를 공동으로 이용할 목적으로 만들어진 자료이다.
* 운영 데이터 (Operational Data) : 한 조직체가 유지되고 운영되는데 필요한 모든 개체 데이터와 관계 데이터의 집합이다.
* 통합 데이터 (Integrated Data) : 데이터 집단에서 자료의 중복이나 군더더기를 제거하여 최적화시킨 데이터의 집합이다.
* 저장 데이터 (Stored Data) : 컴퓨터 시스템이 접근 가능한 저장 매체에 저당 된 데이터의 집합이다.

## ★ DATABASE MANAGEMENT SYSTEM (DBMS)
The database management system (DBMS) is the software that interacts with end users, applications, and the database itself to capture and analyze data. A general-purpose DBMS allows the definition, creation, querying, update, and administration of databases. A database is generally stored in a DBMS-specific format which is not portable, but different DBMSs can share data by using standards such as SQL and ODBC or JDBC. The sum total of the database, the DBMS and its associated applications can be referred to as a "database system". Often the term "database" is used to loosely refer to any of the DBMS, the database system or an application associated the database.

## ★ DATABASE Transation
트랜잭션은 하나의 논리적 단위를 구성하는 데이터베이스 연산의 모임이다. 동시에 여러 트랜잭션이 수행되기 위해서 데이터베이스의 일관성이 보장되어야 하며 이를 위해 동시성 제어(concurrency control)와 회복 제어(recovery control)를 위한 모듈이 있으며 이 둘을 합쳐 트랜잭션 관리 모듈(transaction management module)이라고 한다. 데이터베이스 시스템은 각각의 트랜잭션에 대해 **원자성(Atomicity), 일관성(Consistency), 고립성(Isolation), 영구성(Durability)** 을 보장한다.

* 동시성제어 모듈(concurreny control module): 데이터베이스를 일관성 있게 유지하기 위하여 동시에 수행되는 트랜잭션들 사이의 상호작용을 제어한다.
* 회복제어 모듈(recovery control module): 데이터베이스를 일관성 있게 유지하기 위하여 업데이트를 하는 동안 시스템 장애에도 데이터베이스의 기존 상태가 유지된다.

### # ACID
ACID(원자성, 일관성, 고립성, 지속성)는 데이터베이스 트랜잭션이 안전하게 수행된다는 것을 보장하기 위한 성질을 가리키는 약어이다.

* **원자성(Atomicity)** : 트랜잭션과 관련된 작업들이 부분적으로 실행되다가 중단되지 않는 것을 보장하는 능력이다. 예를 들어, 자금 이체는 성공할 수도 실패할 수도 있지만 보내는 쪽에서 돈을 빼 오는 작업만 성공하고 받는 쪽에 돈을 넣는 작업을 실패해서는 안된다. 원자성은 이와 같이 중간 단계까지 실행되고 실패하는 일이 없도록 하는 것이다.
* **일관성(Consistency)** : 트랜잭션이 실행을 성공적으로 완료하면 언제나 일관성 있는 데이터베이스 상태로 유지하는 것을 의미한다. 무결성 제약이 모든 계좌는 잔고가 있어야 한다면 이를 위반하는 트랜잭션은 중단된다.
* **고립성(Isolation)** : 트랜잭션을 수행 시 다른 트랜잭션의 연산 작업이 끼어들지 못하도록 보장하는 것을 의미한다. 이것은 트랜잭션 밖에 있는 어떤 연산도 중간 단계의 데이터를 볼 수 없음을 의미한다. 은행 관리자는 이체 작업을 하는 도중에 쿼리를 실행하더라도 특정 계좌간 이체하는 양 쪽을 볼 수 없다. 공식적으로 고립성은 트랜잭션 실행내역은 연속적이어야 함을 의미한다. 성능관련 이유로 인해 이 특성은 가장 유연성 있는 제약 조건이다. 자세한 내용은 관련 문서를 참조해야 한다.
* **지속성(Durability)** : 성공적으로 수행된 트랜잭션은 영원히 반영되어야 함을 의미한다. 시스템 문제, DB 일관성 체크 등을 하더라도 유지되어야 함을 의미한다. 전형적으로 모든 트랜잭션은 로그로 남고 시스템 장애 발생 전 상태로 되돌릴 수 있다. 트랜잭션은 로그에 모든 것이 저장된 후에만 commit 상태로 간주될 수 있다.

## ★ DATABASE Feature
1. 실시간 접근성
2. 지속적인 변화
3. 동시 공유
4. 내용에 대한 참조
5. 데이터 논리적 독립성

### DATABASE Advantage
1. 데이터 중복 최소화
2. 데이터 공유
3. 일관성, 무결성, 보안성 유지
4. 최신의 데이터 유지
5. 데이터의 표준화 가능
6. 데이터의 논리적, 물리적 독립성
7. 용이한 데이터 접근
8. 데이터 저장 공간 절약

### DATABASE Disadvantage
1. 데이터베이스 전문가 필요
2. 많은 비용 부담
3. 데이터 백업과 복구가 어려움
4. 시스템의 복잡함
5. 대용량 디스크로 엑세스가 집중되면 과부하 발생

## ★ DATABASE Objects
#### ※ 속성 (Attribute)
* 데이터베이스를 구축하는 가장 작은 논리적 단위로 파일 시스템의 필드 개념에 해당한다.
* 자체만으로는 정보를 표현할 수 없고 정보를 표현하는 단위인 개체나 관계의 특성을 성명하는 도구의 의미로 사용된다.

#### ※ 개체 (Entitiy)
* 정보를 나타내는 논리적 단위로서 파일 시스템의 레코드에 해당한다.
* 개체는 하나 이상의 속성을 조합하여 구성된다.
* 현실 세계의 표현 단위 역할을 하게 된다.
* 개체는 단독으로 존재할 수 있다.
* 모든 개체는 구별가능하다.

## ★ DATABASE TYPE
### ※ Realtional Database (관계형 데이터베이스)
* 관계형 데이터베이스(關係形 Database, Relational Database, 문화어: 관계자료기지, 관계형자료기지, RDB)는 키(key)와 값(value)들의 간단한 관계를 테이블화 시킨 매우 간단한 원칙의 전산정보 데이터베이스이다.

* 관계형 데이터베이스는 데이터 항목 간에 사전 정의된 관계가 있을 때 그러한 데이터 항목들의 모음을 가리킵니다. 이들 항목은 열과 행으로 이루어진 테이블 집합으로 구성됩니다. 테이블은 데이터베이스에 표시할 해당 객체들에 관한 정보를 수록하는 데 사용됩니다. 테이블의 각 열은 특정 종류의 데이터를 수록하며 필드는 속성의 실제 값을 저장합니다. 테이블의 행은 한 객체 또는 엔터티와 관련된 값들의 모음을 나타냅니다. 테이블의 각 행은 기본 키라고 부르는 고유 식별자로 표시할 수 있고 여러 테이블에 있는 행들은 외래 키를 사용하여 상호 연결될 수 있습니다. 이 데이터는 데이터베이스 테이블 자체를 재구성하지 않고도 여러 가지 방법으로 액세스할 수 있습니다.

### ※ NoSQL Database
* NoSQL 데이터베이스는 단순 검색 및 추가 작업을 위한 매우 최적화된 키 값 저장 공간으로, 레이턴시와 스루풋과 관련하여 상당한 성능 이익을 내는 것이 목적이다. NoSQL 데이터베이스는 빅데이터와 실시간 웹 애플리케이션의 상업적 이용에 널리 쓰인다. 또, NoSQL 시스템은 SQL 계열 쿼리 언어를 사용할 수 있다는 사실을 강조한다는 면에서 "Not only SQL"로 불리기도 한다.

* NoSQL 데이터베이스는 특정 데이터 모델에 대해 특정 목적에 맞추어 구축되는 데이터베이스로서 현대적인 애플리케이션 구축을 위한 유연한 스키마를 갖추고 있습니다. NoSQL 데이터베이스는 개발의 용이성, 기능성 및 확장성을 널리 인정받고 있습니다. 문서, 그래프, 키 값, 인 메모리, 검색을 포함해 다양한 데이터 모델을 사용합니다. 이 페이지에는 NoSQL 데이터베이스를 실행 전에 보다 잘 이해하여 유용하게 활용할 리소스가 포함되어 있습니다. 수십 년간, 애플리케이션 개발을 위해 지배적으로 사용된 데이터 모델은 관계형 데이터 모델로서 Oracle, DB2, SQL Server, MySQL, PostgreSQL과 같은 관계형 데이터베이스에 의해 사용되었습니다. 2000년대 중반에서 말에 이르러서야 다른 데이터 모델들이 채택되고 사용되는 현상이 눈에 띄기 시작했습니다. 이러한 새로운 데이터베이스와 데이터 모델 등급을 차별화하고 분류하기 위해 "NoSQL"이란 용어가 만들어졌습니다. 흔히 "NoSQL"이란 용어는 "비관계형"과 같은 의미로 사용됩니다.

#### # NoSQL Feature
NoSQL 데이터베이스는 탁월한 사용자 경험을 제공하기 위하여 유연성과 확장성을 비롯해 고성능의 매우 기능적인 데이터베이스를 필요로 하는 모바일, 웹이나 게이밍과 같은 다양한 현대적인 애플리케이션에 적합합니다.

* 유연성: NoSQL 데이터베이스는 일반적으로 유연한 스키마를 제공하여 보다 빠르고 반복적인 개발을 가능하게 해줍니다. 이같은 유연한 데이터 모델은 NoSQL 데이터베이스를 반정형 및 비정형 데이터에 이상적으로 만들어 줍니다.
* 확장성: NoSQL 데이터베이스는 일반적으로 고가의 강력한 서버를 추가하는 대신 분산형 하드웨어 클러스터를 이용해 확장하도록 설계되었습니다. 일부 클라우드 제공자들은 완전관리형 서비스로서 이런 운영 작업을 보이지 않게 처리합니다.
* 고성능: NoSQL 데이터베이스는 특정 데이터 모델(문서, 키 값, 그래프 등) 및 액세스 패턴에 대해 최적화되어 관계형 데이터베이스를 통해 유사한 기능을 충족하려 할 때보다 뛰어난 성능을 얻게 해줍니다.
* 고기능성: NoSQL 데이터베이스는 각 데이터 모델에 맞추어 특별히 구축된 뛰어난 기능의 API와 데이터 유형을 제공합니다.

#### # NoSQL Database Types
1. Key-value stores are the simplest NoSQL databases. Every single item in the database is stored as an attribute name, or key, together with its value. Examples of key-value stores are Riak and Voldemort. Some key-value stores, such as Redis, allow each value to have a type, such as "integer", which adds functionality.
2. Document databases pair each key with a complex data structure known as a document. Documents can contain many different key-value pairs, or key-array pairs, or even nested documents.
3. Wide-column stores such as Cassandra and HBase are optimized for queries over large datasets, and store columns of data together, instead of rows.
4. Graph stores are used to store information about networks, such as social connections. Graph stores include Neo4J and HyperGraphDB.

## REFERENCE
1. [데이터베이스 - 위키백과](https://ko.wikipedia.org/wiki/%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4)
2. [데이터베이스 트랜잭션 - 위키백과](https://ko.wikipedia.org/wiki/%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4_%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98)
3. [관계형 데이터베이스 - 위키백과](https://ko.wikipedia.org/wiki/%EA%B4%80%EA%B3%84%ED%98%95_%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4)
4. [NoSQL - 위키백과](https://ko.wikipedia.org/wiki/NoSQL)
5. [ACID - 위키백과](https://ko.wikipedia.org/wiki/ACID)
6. [NoSQL이란? - Amazon AWS](https://aws.amazon.com/ko/nosql/)