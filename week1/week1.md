# TypeScript Type과 Interface

## Type과 Interface란?

TypeScript에서 **Type**과 **Interface**는 모두 타입을 정의하는 방법입니다. 둘 다 코드의 타입 안정성을 높이고 개발자 경험을 향상시키는 역할을 합니다.

## Type (타입 별칭)

### 기본 문법

```typescript
type UserName = string;
type UserAge = number;
type User = {
  name: UserName;
  age: UserAge;
};
```

### 특징

- **유니온 타입** 지원
- **교차 타입** 지원
- **원시 타입** 정의 가능
- **조건부 타입** 지원

### 예시

```typescript
// 유니온 타입
type Status = "loading" | "success" | "error";

// 교차 타입
type Person = {
  name: string;
} & {
  age: number;
};

// 조건부 타입
type ApiResponse<T> = T extends string ? string : number;
```

## Interface (인터페이스)

### 기본 문법

```typescript
interface User {
  name: string;
  age: number;
  greet(): string;
}
```

### 특징

- **선언 병합** 지원
- **확장(extends)** 가능
- **구현(implements)** 가능
- **객체 타입**에 특화

### 예시

```typescript
// 기본 인터페이스
interface Animal {
  name: string;
  makeSound(): void;
}

// 인터페이스 확장
interface Dog extends Animal {
  breed: string;
  bark(): void;
}

// 선언 병합
interface User {
  name: string;
}
interface User {
  age: number;
}
// 결과: User는 name과 age를 모두 가짐
```

## Type vs Interface 비교

| 특징        | Type         | Interface    |
| ----------- | ------------ | ------------ |
| 유니온 타입 | ✅ 지원      | ❌ 지원 안함 |
| 교차 타입   | ✅ 지원      | ✅ 지원      |
| 선언 병합   | ❌ 지원 안함 | ✅ 지원      |
| 확장        | ❌ 지원 안함 | ✅ extends   |
| 원시 타입   | ✅ 지원      | ❌ 지원 안함 |
| 조건부 타입 | ✅ 지원      | ❌ 지원 안함 |

## 언제 무엇을 사용할까?

### Type을 사용하는 경우

```typescript
// 유니온 타입이 필요한 경우
type Theme = "light" | "dark";

// 원시 타입을 별칭으로 사용하는 경우
type ID = string;
type Timestamp = number;

// 복잡한 타입 변환이 필요한 경우
type NonNullable<T> = T extends null | undefined ? never : T;
```

### Interface를 사용하는 경우

```typescript
// 객체의 구조를 정의하는 경우
interface ApiResponse {
  data: any;
  status: number;
  message: string;
}

// 클래스에서 구현해야 하는 경우
interface Drawable {
  draw(): void;
}

class Circle implements Drawable {
  draw() {
    console.log("Drawing a circle");
  }
}

// 라이브러리나 외부 모듈과의 호환성을 위해 확장이 필요한 경우
interface Window {
  customProperty: string;
}
```

## 실제 사용 예시

```typescript
// API 응답 타입 정의
interface ApiUser {
  id: number;
  name: string;
  email: string;
  createdAt: string;
}

// 유틸리티 타입
type PartialUser = Partial<ApiUser>;
type UserEmail = Pick<ApiUser, "email">;
type UserWithoutId = Omit<ApiUser, "id">;

// 함수 타입 정의
type EventHandler<T> = (event: T) => void;
type AsyncFunction<T, R> = (param: T) => Promise<R>;

// 사용 예시
const handleUserClick: EventHandler<MouseEvent> = (event) => {
  console.log("User clicked:", event.target);
};

const fetchUser: AsyncFunction<number, ApiUser> = async (id) => {
  const response = await fetch(`/api/users/${id}`);
  return response.json();
};
```

## 결론

- **Type**: 유니온, 교차 타입, 원시 타입 별칭, 복잡한 타입 변환이 필요할 때
- **Interface**: 객체 구조 정의, 클래스 구현, 선언 병합이 필요할 때

대부분의 경우 객체 타입을 정의할 때는 **Interface**를, 그 외의 경우에는 **Type**을 사용하는 것이 일반적입니다. 하지만 팀의 코딩 컨벤션과 프로젝트의 요구사항에 따라 일관성 있게 선택하여 사용하는 것이 중요
