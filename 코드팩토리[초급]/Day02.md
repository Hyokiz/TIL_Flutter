# 2. 객체지향 프로그래밍

# OOP(Object Oriented Programming)

객체 지향 프로그래밍

## Class 정의

- 설계서를 만든다.
- Idol

  - Name(이름)
  - Members(멤버들)
  - sayHello(인사하기)
  - Introduce(멤버 소개하기)

## Instance

- 결과물을 만드는 것.

## Class를 통해 Programming 을 하는 것이 OOP, 즉 객체 지향 프로그래밍이다.

```dart
void main() {
  Idol blackPink = Idol();

  print(blackPink.name); // 블랙핑크
  print(blackPink.members); // [지수, 제니, 리사, 로제]
  blackPink.sayHello(); // 안녕하세요. 블랙핑크입니다.
  blackPink.introduce(); // 저희 멤버는 지수, 제니, 리사, 로제가 있습니다.
}

// Idol class
// name (이름) - 변수
// members (멤버들) - 변수
// sayHello (인사) - 함수
// introduce (멤버소개) - 함수

// constructor (생성자)
class Idol {
  // 가장 간단한 형태의 class
  String name = "블랙핑크";
  List<String> members = ["지수", "제니", "리사", "로제"];

  void sayHello() {
    print("안녕하세요. 블랙핑크입니다.");
  }

  void introduce() {
    print("저희 멤버는 지수, 제니, 리사, 로제가 있습니다.");
  }
}
```
## constructor

```dart
void main() {
  Idol blackPink = Idol(
    "블랙핑크",
    ["지수", "제니", "리사", "로제"],
  );

  Idol bts = Idol(
    "BTS",
    ["RM", "진", "슈가", "제이홉", "지민", "뷔", "정국"],
  );

  print(bts.name);
  print(bts.members);
}

// Idol class
// name (이름) - 변수
// members (멤버들) - 변수
// sayHello (인사) - 함수
// introduce (멤버소개) - 함수

// constructor (생성자)
class Idol {
  // 가장 간단한 형태의 class
  String name;
  List<String> members;

  Idol(this.name, this.members);
  
  void sayHello() {
    print("안녕하세요. ${this.name}입니다.");
  }

  void introduce() {
    print("저희 멤버는 ${this.members}가 있습니다.");
  }
}
```

## named constructor

```dart
class Idol {
  String name;
  List<String> members;

  Idol(this.name, this.members);

  Idol.fromList(List values)
    : this.members = values[0]
      this.name = values[1]
}

void main() {
  Idol bts = Idol.fromList(
    [
      ["RM", "진", "슈가"],
      "BTS",
    ]
  );
}
```

## immutable programming

한번 값을 선언하면 변경할 수 없게 만드는 프로그래밍

- final 키워드를 사용한다.
- const 는 const로 선언할 수 있는 타입 constructor 앞에 붙이는 식으로 사용.
- 효율을 올리는데 중요한 부분

```dart
class Idol {
  final String name;
  final List<String> members;

  const Idol(this.name, this.members);

  void main() {
    Idol blackPink = const Idol(
      "블랙핑크",
      ["지수", "제니", "리사", "로제"]
    );
  }
}
```

```dart
void main() {
  Idol blackPink = Idol(
    "블랙핑크",
    ["지수", "제니", "리사", "로제"]
  );
  Idol blackPink2 = Idol(
    "블랙핑크",
    ["지수", "제니", "리사", "로제"]
  );

  print(blackPink == blackPink2) // false

    Idol blackPink = const Idol(
    "블랙핑크",
    ["지수", "제니", "리사", "로제"]
  );
  Idol blackPink2 = const Idol(
    "블랙핑크",
    ["지수", "제니", "리사", "로제"]
  );

  print(blackPink == blackPink2) // true
}
```

## 게터와 세터

- Getter

  - 데이터를 가져올 때

- Setter

  - 데이터를 설정할 때

```dart
class Idol {
  String name;
  List<String> members;

  Idol(this.name, this.members);

  Idol.fromList(List values)
    : this.members = values[0]
      this.name = values[1]
  // getter
  String get firstMember {
    return this.members[0];
  }
}
```