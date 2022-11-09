mermaid_test.md 
      #Mermaid 실습
 

 #mermaid 실습
 -순서도 실습

```mermaid 
flowchart 
      a([밥을 먹지 않았다])
      b((String status = hunger <br> Srting = nothing))
      c(배가 고픈가?)
      d(먹을 것이 있는가)
      e(밥을 먹는다)
      f(먹을 것이 있는가)
      g([end])
      aa[배불러]

      

      %% 연결
      a --> b --> c -->|yes| d --> e --> f --> g
      
      c --> aa --> h
      h[안먹는다]
      c --> |No| h
      d --> |No| h
      f[먹지 않는다]
    
```



```mermaid
sequenceDiagram
    actor A as 사용자
    participant B as 인증 시스템
    A --> B: 아이디/비밀번호 입력
    activate B
    B -> A: 인증완료
    deactivate B
```

```mermaid
sequenceDiagram
    actor A as 사용자
    participant B as 인증 시스템
    A ->>+ B: 아이디/비밀번호 입력
    A ->>+ B: catcha 입력
    B -->>- A: catcha 성공
    B -->>- A: 인증 완료
```

```mermaid
sequenceDiagram
actor A as 사용자
participant B as 인증 시스템
A ->>+ B: 아이디/비밀번호 입력
B -->>- A: 인증완료
```

```mermaid
sequenceDiagram
    autonumber
    actor A as 사용자
    participant B as 인증 시스템
    A ->>+ B: 아이디/비밀번호 입력
    A ->>+ B: catcha 입력
    B -->>- A: catcha 성공
    B -->>- A: 인증 완료
```

```mermaid
sequenceDiagram
    actor A as 사용자
    participant B as 인증 시스템
    
    # `right of` 적용
    Note right of A: 일반사용자
    Note right of B: 깃허브
    
    A ->>+ B: 아이디/비밀번호 입력
    B -->>- A: 인증완료
```

```mermaid
sequenceDiagram 
    actor A as 사용자
    participant B as 인증 시스템
    
    # `lett of` 적용
    Note left of A: 일반사용자
    Note left of B: 깃허브
    
    A ->>+ B: 아이디/비밀번호 입력
    B -->>- A: 인증완료
```

```mermaid
sequenceDiagram
    participant A as Data Updater
    participant B as DB
    loop 1시간마다 수행
        A ->> B: send update data
        B -->> A: update result
    end
```

```mermaid
sequenceDiagram
    actor A as 사용자
    participant B as 서버
    
    A ->> B: 서비스 상태 요청
    
    alt 가능
        B -> A: 서비스 가능 상태입니다.
    else 불가능
        B -> A: 현재 서비스 중단 상태입니다.
    else 점검중
        B -> A: 점검중... 기다려 주세요
    end
```

```mermaid
sequenceDiagram
    par 강감찬 to 이순신
        강감찬 ->> 이순신: 안녕하세요?

    and 강감찬 to 홍길동
        강감찬 ->> 홍길동: 안녕하세요?
    end
    
    이순신 -->> 강감찬: 강 장군! 오랜만이오.
    홍길동 -->> 강감찬: 장군님, 홍길동 여기 있습니다.
```

```mermaid
sequenceDiagram
    participant U as user
    participant C as Client
    participant S as Server
    participant D as Detabase

    U ->> C: Full username
    U ->> C: Full password
    C ->> U : Enable "Login" button
    U ->> C : Click "Login" button 

    
    C ->> + S: POST/login
         S ->>+ D: SELECT FROM users
          Note over S,D: See login.py for 
         D -->>- S: result
    S -->>- C: {authnticiated : true}

    C--> U: redirect  "/home"

```

```mermaid
classDiagram
    class BankAccount
    BankAccount: String owner
    BankAccount: Bigdecimal balance
    BankAccount: deposit(amount)
    BankAccount: withdrawal(amount)
```

```mermaid
classDiagram
    class BankAccount{
        +String 소유자
        -Int 잔액
        +deposit(금액) bool
        +withdrawl(금액) int
    }
```
```{mermaid}
classDiagram
    classA <|-- classB
    classC *-- classD
    classE o-- classF
    classG <-- classH
    classI <.. classJ
    classK <|.. classL
    classM -- classN
    classO .. classP
```

```{mermaid}
classDiagram
    Customer "1" --> "*" Ticket
    Student "1" --> "1..*" Course
    우주 --> "many" star : Contains
```

```{mermaid}
classDiagram
  direction LR

  class 학생 {
    -학생증: 학생증
  }
  class 학생증 {
    -id : int
    -name : string
  }
  class 자전거 {
    -id : int
    -name : string
  }
  학생 "1" --o "1" 학생증 : 가지고다닌다
  학생 "1" --o "1" 자전거 : 탄다
```


```mermaid
classDiagram 
    direction LR
    class Person{
    +name : str
    +phoneNumber : str
    +emailAddress : str
    +purchaseParkingPass() }

    class Student{
        +studentNumber : int
        +averageMark : int
        +isEligibleToEnroll(str) : boll
        +getSeminarsTaken() : int
    }

    class Professor{
        /salary : int
        #staffNumber : int
        -yearsOfService : int
        +numberOfClasses : int
    }
    
        class Address{
        +street: str
        +city: str
        +state: str
        +postalCode: int
        +country: str
        -validate() bool
        +outputAsLabel() str
    }

   Person <|-- Student
    Person <|-- Professor
    Student "0..*"<--"1..5" Professor : supervise
    Person "0..1"-->"1" Address : lives in


```