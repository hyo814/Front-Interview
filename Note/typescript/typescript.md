# 💻 타입스크립트란(TypeScript)

## 👨🏻‍💻 타입스크립트란?

- 타입스크립트는 동적 타입 언어인 자바스크립트의 약점을 보완하기 위해 `정적인 타입`을 부여한 언어이다. 즉, 자바스크립트의 확장된 언어라고 볼 수 있다.
- 타입스크립트는 사용하면 `컴파일 시 타입 체킹`을 하기 때문에 `오류 포착`도 쉽고, 명시적으로 타입을 지정하기 때문에 `개발자의 의도를 명확하게 파악`하기 쉽다.
- 타입스크립트는 자바스크립트와 달리 브라우저에서 실행하려면 파일을 한번 변환해주는 `컴파일 과정`이 필요하다.
- 자바스크립트는 동적 타입 언어이기 때문에 런타임(프로그램이 동작되어지는 때) 속도는 빠르지만 타입 안정성이 보장되지 않는다. 반면에 타입스크립트는 컴파일 시 시간이 조금 걸리지만 `안정성을 보장한다.`
- 코드 작성 시 매번 타입을 결정해야 하기 때문에 번거롭고 `코드량이 증가`하며, `컴파일 시간이 오래 걸린다는 단점`이 있다.
- 리액트의 경우 브라우저는 자바스크립트 밖에 모르기 때문에 `tsx` 파일을 자바스크립트로 변환하는 `트랜스파일링`이 필요하다. 이때, 변환 과정에서 에러를 잡을 수 있다.

<br />

## 👨🏻‍💻 타입스크립트 특징

- ES6 모듈 및 네임스페이스
  - 타입스크립트는 ES6에서 제공하는 `모듈 선언(export)`과 `모듈 호출 방식(import)`을 지원한다. 또한 클래스가 커지고 개수가 많아지면 유사한 기능의 `클래스들을 그룹으로 구분`지어야 할 필요가 있는데 이때 타입스크립트는 `네임 스페이스`를 지원하여 라이브러리 단위의 모듈 구성이 가능하다.
- 클래스와 인터페이스
  - 타입스크립트는 ES6의 클래스 특징을 받아들이고, `인터페이스 특징을 지원`함으로서 강력한 객체지향 프로그래밍 환경을 제공한다. 기존 객체지향 프로그래밍 언어에서 사용하는 `키워드 (class, interface, extends)`를 그대로 사용할 수 있다.
- 타입 시스템
  - 타입 스크립트는 `타입 시스템`을 지원한다. 타입 시스템은 자바스크립트의 타입을 확장하고 `Type Annotation`을 통해 변수에 타입을 선언할 수 있다. 이렇게 타입이 지정되면 엄격한 타이핑이 적용돼 타입 안정성을 보장한다.

<br />