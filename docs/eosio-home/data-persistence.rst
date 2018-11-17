2.4 데이터 지속성
================
데이터 지속성을 알기 위해서, 간단한 주소록 스마트 컨트랙트를 작성할 것이다.
이 주소록 컨트랙트는 여러가지 이유에서 현실적이지 않지만, 
eosio의 ``multi_index`` 기능을 사용하지 않는 비지니스 로직으로 인해 산만해지지 않으면서도 EOSIO에서 데이터 지속성이 어떻게 동작하는지를 배울 수 있는 좋은 컨트랙트이다.

.. rubric:: Step 1: 새로운 디렉토리 만들기

먼저 컨트랙트 디렉토리를 생성하고 위치를 확인한다.

.. code-block:: console

  cd pwd

컨트랙트를 위한 새로운 디렉토리를 생성하고 디렉토리로 진입한다.
  
.. code-block:: console

  mkdir addressbook
  cd addressbook

.. rubric:: Step 2: 파일 만들고 열기

.. code-block:: console

  touch addressbook.cpp

당신이 사용하는 에디터에서 파일을 열어라

.. rubric:: Step 3: 상속 Standard Class를 작성하고 EOSIO를 Include 한다

이전 튜토리얼에서 당신은 hello world 컨트랙트를 작성하고, 컨트랙트 작성의 기초를 배웠을 것이다.
당신은 아래의 구조에 익숙해질 것이다. 클래스의 이름은 ``addressbook`` 이라고 명명하였다.

.. code-block:: c++

  #include <eosiolib/eosio.hpp>

  using namespace eosio;

  class [[eosio::contract]] addressbook : public eosio::contract {
    public:
        
    private: 
    
  };

.. rubric:: Step 4: 테이블을 위해 데이터 구조체를 생성한다

테이블을 구성하고 인스턴스화 하기 전에, 주소록의 데이터 구조를 나타내는 구조체를 작성해야 한다.
이 구조체를 "schema"로 생각하면 된다. 주소록 테이블에는 인명 정보가 포함될 것이고, 이를 위해 "person"이라는 구조체를 생성한다.

.. code-block:: c++

  struct person {};

multi_index table을 위해 schema를 정의할 때 기본키(primary key)로 사용하기 위한 고유값이 필요하다.

이 컨트랙트에서는 키로 ``name`` 타입을 사용한다. 
컨트랙트에서 

