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
void main() {
  Idol blackPink = Idol("블랙핑크", ["지수", "제니", "리사", "로제"]);

  Idol bts = Idol.fromList([
    ["RM", "진", "슈가", "제이홉", "지민", "뷔", "정국"],
    "BTS",
  ]);

  print(blackPink.firstMember);
  print(bts.firstMember);
  
  blackPink.firstMember = "코드팩토리";
  bts.firstMember = "아이언맨";
  
  print(blackPink.firstMember);
  print(bts.firstMember);
}

class Idol {
  String name;
  List<String> members;

  Idol(this.name, this.members);

  Idol.fromList(List values)
      : this.members = values[0],
        this.name = values[1];

  void sayHello() {
    print("안녕하세요 ${this.name}입니다.");
  }

  void introduce() {
    print("저희 멤버는 ${this.members}입니다.");
  }

  // getter
  String get firstMember {
    return this.members[0];
  }
  
  // setter
  set firstMember(String name) {
    this.members[0] = name;
  }
}

```

- 왜 게터, 세터를 사용하는가?

  - 함수 : 로직이 많이 들어가는 형태
  - 게터, 세터 : 간단한 가공

- 현대 프로그래밍에서는 setter를 거의 쓰지 않는다.

## private 변수

현재 파일 외에서 사용할 수 없게 하는 변수
같은 파일 내에서만 사용 가능

- 무엇이든 앞에 _(underscore)로 사용

## 상속(inheritance)

부모 클래스의 모든 속성을 자식 클래스가 부여받는다.

```dart
void main() {
  print("------- Idol -------");
  Idol apink = Idol(name: "에이핑크", membersCount: 5);

  apink.sayName();
  apink.sayMembersCount();

  print("-------Boy Group-------");

  BoyGroup bts = BoyGroup("BTS", 7);

  bts.sayMembersCount();
  bts.sayName();
  bts.sayMale();

  print("-------Girl Group-------");

  GirlGroup redVelvet = GirlGroup("Red Velvet", 5);

  redVelvet.sayName();
  redVelvet.sayMembersCount();
  redVelvet.sayFemale();
  
  print("-------Type Comparison-------");
  print(apink is Idol);
  print(apink is BoyGroup);
  print(apink is GirlGroup);
  
  print("-------Type Comparison2-------");
  print(bts is Idol);
  print(bts is BoyGroup);
  print(bts is GirlGroup);
  
  print("-------Type Comparison3-------");
  print(redVelvet is Idol);
  print(redVelvet is BoyGroup);
  print(redVelvet is GirlGroup);
}

// 상속 - inheritance
// 상속을 받으면 부모 클래스의 모든 속성을
// 자식 클래스가 부여받는다.

class Idol {
  // 이름
  String name;

  // 멤버 숫자
  int membersCount;

  Idol({
    required this.name,
    required this.membersCount,
  });

  void sayName() {
    print("저는 ${this.name}입니다.");
  }

  void sayMembersCount() {
    print("${this.name}은 ${this.membersCount}명의 멤버가 있습니다.");
  }
}

class BoyGroup extends Idol {
  BoyGroup(
    String name,
    int membersCount,
  ) : super(name: name, membersCount: membersCount);

  void sayMale() {
    print("저는 남자 아이돌입니다.");
  }
}

class GirlGroup extends Idol {
  GirlGroup(
    String name,
    int membersCount,
  ) : super(name: name, membersCount: membersCount);

  void sayFemale() {
    print("저는 여자 아이돌입니다.");
  }
}
```

## method overriding

```dart
void main() {
  TimesTwo tt = TimesTwo(2);

  print(tt.calculate());

  TimesFour tf = TimesFour(2);

  print(tf.calculate());
}

// method - function (class 내부에 있는 함수)
// override - 덮어쓰기 (우선시하다.)

class TimesTwo {
  final int number;

  TimesTwo(
    this.number,
  );

  // method
  int calculate() {
    return number * 2;
  }
}

class TimesFour extends TimesTwo {
  TimesFour(int number) : super(number);

  @override
  // @override는 없어도 가능하나, 직관적으로 보여줄 수 있음
  int calculate() {
    // return super.number * 4;
    // return number * 4; 도 가능
    return super.calculate() * 2;
    // this.calculate() 는 불가능하다.
  }
}

```

## static keyword

```dart
void main() {
  Employee seulgi = Employee("슬기");
  Employee chorong = Employee("초롱");
  Employee jenny = Employee("제니");
  
  seulgi.name = "코드팩토리";
  seulgi.printNameAndBuilding();
  chorong.printNameAndBuilding();
  
  Employee.building = "오투타워";
  
  seulgi.printNameAndBuilding();
  chorong.printNameAndBuilding();
  jenny.printNameAndBuilding();
  
  Employee.printBuilding();
}

class Employee {
  // static 은 instance에 귀속되지 않고 class 에 귀속된다.
  // 알바생이 일하고 있는 건물
  static String? building;
  // 알바생 이름
  String name;
  
  Employee(
    this.name,
  );
  
  void printNameAndBuilding() {
    print("제 이름은 $name 입니다. $building 건물에서 근무하고 있습니다.");
  }
  
  static void printBuilding() {
    print("저희는 $building 건물에서 근무중입니다.");
  }
}
```

## Interface

- interface 명령어가 없으므로 class 로 생성

```dart
void main() {
  BoyGroup bts = BoyGroup("BTS");
  GirlGroup redVelvet = GirlGroup("RedVelvet");

  bts.sayName();
  redVelvet.sayName();

  print(bts is IdolInterface);
  print(bts is BoyGroup);
  print(bts is GirlGroup);

  print(redVelvet is IdolInterface);
  print(redVelvet is BoyGroup);
  print(redVelvet is GirlGroup);
}

// interface
// 설계로 작성한 것이기 때문에 따로 작성할 필요가 없음.

// abstract : 추상적
// abstract 가 써져있으면 instance로 사용하지 마라 라는 의미가 담겨 있음
abstract class IdolInterface {
  String name;

  IdolInterface(this.name);

  // abstract를 추가할 경우 형태만 작성할 수 있음.
  void sayName();
}

class BoyGroup implements IdolInterface {
  String name;

  BoyGroup(this.name);

  void sayName() {
    print("제 이름은 $name 입니다.");
  }
}

class GirlGroup implements IdolInterface {
  String name;

  GirlGroup(this.name);

  void sayName() {
    print("제 이름은 $name 입니다.");
  }
}
```

## Generic

타입을 외부에서 받을 때 사용

```dart
void main() {
  Lecture<String, String> lecture1 = Lecture("123", "lecture1");
  
  lecture1.printIdType();
  
  Lecture<int, String> lecture2 = Lecture(123, "lecture2");
  
  lecture2.printIdType();
}

// generic - 타입을 외부에서 받을 때 사용
class Lecture<T, X> {
  final T id;
  final X name;
  
  Lecture(this.id, this.name);
  
  void printIdType() {
    print(id.runtimeType);
  }
}
```

## Object Oriented Programming

```dart
void main() {
  Test test = Test();
 
}

// Object Oriented Programming
// 객체 지향 프로그래밍

class Test {}
// 사실상 class Test extends Object{}이다.
```

