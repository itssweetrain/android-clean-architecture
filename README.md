editing...
# android-clean-architecture
applied android clean architecture with mvvm pattern
# Architecture
![Clean-architecture-concept-Parallelism-between-software-architecture-and-building](https://user-images.githubusercontent.com/76150928/187150463-75388b9a-e89f-4ef0-889a-9687902b0f3c.png)

## 등장 배경
클린 아키텍쳐의 큰 두 가지 가치는, 
1. 같은 목표를 가진다.
2. 소프트웨어를 계층(layer)로 나눠서 관심사를 분리한다. 
아키텍쳐는 선을 긋는 기술이며, 엉클 밥은 이 선을 경계(boundary)라고 부른다. 경계를 이렇게 쓰는 이유는 핵심적인 비즈니스 로직을 오염시키지 못하게 만들려는 목적으로 쓰인다는 것이다. 또한 이렇게 관심사를 분리함으로써 내부에서 외부의 것을 알지 못하게 한다.

> 소프트웨어 아키텍쳐는 선을 긋는 기술이며, 나는 이러한 선을 경계(boundary)라고 부른다. 경계는 소프트웨어 요소를 서로 분리하고, 경계 한편에 있는 요소가 반대편에 있는 요소를 알지 못하도록 막는다.
Robert C.Martin, Clean Architecture, Ch.17
이런 가치를 실현시키고 단일 아이디어로 통합하길 원하면서 소개한 아이디어가 클린 아키텍쳐이자 경계로 나누어진 구성요소들이다.

이 4가지의 구성요소는 서로의 의존도가 어느정도인가를 기준으로 계층을 이루고 있다.
의존성 규칙의 방향을 보면 가장 외부 UI나 data source가 의존도가 높고, use case, entity의 방향으로 낮아지는 것을 볼 수 있다.

의존성 규칙의 가장 큰 개념으로서는,
1. 안쪽의 원 즉 비즈니스 로직은 바깥의 원, 즉 UI나 data source에 대해 전혀 알지 못한다.
2. 또한 안쪽 영역으로 갈수록 추상화와 정책의 수준이 높아지며, 반대로 갈수록 구체적인 세부사항으로 구성된다.

크게 안쪽에는 도메인의 영역인 entity, use case 그리고 가장 최상층에는 infrastructure, 그 둘 사이를 이어주는 adapter가 있다.
어플리케이션의 핵심이자 비즈니스 규칙인 도메인은 다시 Entity와 Use case로 나눌 수 있다.
그리고 adapter 은 도메인과 인프라 사이의 경계선으로 생성된다.



# Structure
## 기본 구성
* entity : 다른 구성요소에 의존하지 않는 비즈니스 로직이자, 데이터 구조, 메소드들의 집합체이다. 따라서 핵심 업무 규칙을 캡슐화하고 이렇게 캡슐화된 엔티티는 가장 변하지 않는 영역
* use case : entity를 사용해서 어플리케이션 고유의 비즈니스 로직을 실현한다. 시스템의 동작을 사용자의 입장에서 표현한 시나리오이다. 어떻게 시스템이 자동화되는지 말해주고 어떻게 어플리케이션이 행동하고 실행하는지 결정한다.
* adapter : 도메인과 인프라 사이의 통역하고 변환하는 역할을 한다. 즉, 본인의 계층 안밖에 있는 Data나 Event를 교환하기 위한 존재.
* infrastructure : 일반적으로 DB, 프레임워크 같은 것들로 구성이 되는 영역.

# Libraries and Tools used
* [Hilt](https://developer.android.com/training/dependency-injection/hilt-android)
* [Retrofit2](https://github.com/square/retrofit)
* [OkHttp3](http://square.github.io/okhttp/)
* [Gson](https://github.com/google/gson)
* [Architecture Components - LiveData/ViewModel](https://developer.android.com/topic/libraries/architecture/index.html)
* [View Binding](https://developer.android.com/topic/libraries/view-binding)

