# Dart 언어 완전정복

## 1. 기본기

- 구글에 dartpad 검색 후 실행
- 기능 

  - Format : 코드 정리

```dart
void main() {
  print("Hello Code Factory");
}
```

- 변수 선언

```dart
void main() {
  // variable
  var name = "Code Factory";

  print(name);

  name = "Flutter";

  print(name);
}
```

- 정수 

```dart
void main() {
  // 정수
  // integer
  int number1 = 10;

  print(number1);

  int number2 = 15;

  print(number2);

  int number3 = -20;

  print(number3);
}

void main() {
  int number1 = 2;
  int number2 = 4;

  print(number1 + number2); // 6
  print(number1 - number2); // -2
  print(number1 / number2); // 0.5
  print(number1 * number2); // 8
}
```

- 실수 

```dart
void main() {
  // 실수
  // double
  double number1 = 2.5;
  double number2 = 0.5;

  print(number1 + number2); // 3
  print(number1 - number2); // 2
  print(number1 / number2); // 5
  print(number1 * number2); // 1.25
}
```

- bool

```dart
void main() {
  // true/false
  // Boolean
  bool isTrue = true;
  bool isFalse = false;

  print(isTrue); //true
  print(isFalse); // false
}
```

- string

```dart
void main() {
  // 글자 타입
  // String
  String name = "레드벨벳";
  String name2 = "코드팩토리";

  print(name);
  print(name2);

  // var vs String
  // var은 값으로 타입을 정함.
  var name3 = "블랙핑크";
  var number = 20;

  print(name3.runtimeType); // String
}
```

```dart
void main() {
  String name = "레드벨벳";
  String name2 = "슬기";
  
  print("${name} ${name2}");
}
```
- 백틱(``)이 아닌 따옴표('', "")로 정의한다.

- dynamic

```dart
void main() {
  dynamic name = "코드팩토리";

  print(name);

  dynamic number = 1;

  print(number);

  var name2 = "블랙핑크";

  print(name2);
}
```
- var과 dynamic 의 차이

  - var : 한번 선언한 타입으로 fix
  - dynamic : 변경 가능
  - 
```dart
void main() {
  dynamic name = "코드팩토리";

  var name2 = "블랙핑크";

  print(name.runtimeType); // String
  print(name2.runtimeType); // String

  name = 2; // 가능
  name2 = 5; // 불가능
}

```

- nullable

```dart
void main() {
  // nullable - null이 될 수 있다.
  // non-nullable - null이 될 수 없다.
  // null - 아무런 값도 있지 않다.
  String name = "코드팩토리";

  print(name);

  name = null; // 불가능

  String? name2 = "블랙핑크";

  name2 = null; // 가능

  print(name2!) // 가능
}
```

  - ?를 넣으면 null도 넣을 수 있다.
  - !를 넣으면 null이 절대 아니라는 의미

- final

  - 일반적인 변수 선언 앞에 선언
  - 변수의 값 변경 X
  - const와 비슷
  - 타입 생략 가능

```dart
void main() {
  final String name = "코드팩토리";

  print(name);

  name = "블랙핑크"; // 불가능
}
```

- const 

  - 알고 있는 내용
  - 타입 생략 가능

```dart
void main() {
  const name2 = "블랙핑크";

  print(name2);
}
```

- Datetime


```dart
void main() {
  DateTime now = DateTime.now();

  print(now); // 이 코드가 실행이 되는 순간의 시간이 나옴

  DateTime now2 = DateTime.now();

  print(now2); // now2와 다름
}
```

```dart
void main() {
  final DateTime now = DateTime.now(); // 가능

  print(now);

  const DateTime now2 = DateTime.now(); // 불가능
}
```

  - final 과 const 의 차이

    - const : 빌드 타임의 값을 알고 있어야 함
    - final : 빌드 타입의 값을 알고 있지 않아도 됨.

    - Run을 누르는 순간 -> 빌드 타임

- operator

```dart
void main() {
  int number = 2;

  print(number);
  print(number + 2);
  print(number - 2);
  print(number * 2);
  print(number / 2);

  print("------------------")

  print(number % 2); // 0
  print(number % 3); // 2

  print(number); // 2
  print("------------------")

  number ++;

  print(number); // 3

  number --;
  
  print(number); // 2
}
```

```dart
void main() {
  double number = 4.0;

  print(number); // 4

  number += 1;

  print(number); // 5

  number -= 1;

  print(number); // 4

  number /= 2;
  
  print(number); // 2
}
```

```dart
void main() {
  // null
  double? number = 4.0;

  print(number);
  
  number = 2.0;

  print(number);

  number = null;

  print(number);

  number ??= 3.0; // number가 null이면 오른쪽 값으로 바꿔라.

  print(number);
}
```

```dart
void main() {
  int number1 = 1;
  int number2 = 2;

  print(number1 > number2); // false
  print(number1 < number2); // true
  print(number1 >= number2);
  print(number1 <= number2);
  print(number1 == number2);
  print(number1 != number2);
}
```

```dart
void main() {
  int number1 = 1;

  print(number1 is int); // true
  print(number1 is String); //false

  print(number is! int); // false
  print(number is! String); // true
}
```

- 논리 오퍼레이터

```dart
void main() {
  // && - and 조건
  // || - or 조건
  bool result = 12 > 10 && 1 >= 0;
  
  print(result); // true

  bool result2 = 12 > 10 && 0 > 1;

  print(result2); // false

  bool result3 = 12 > 10 || 1 > 0;

  print(result3); // true

  bool result4 = 12 > 10 || 0 > 1;

  print(result4); // true

  bool result5 = 12 < 10 || 0 > 1;

  print(result5); // false
}
```

- List

```dart
void main() {
  // List
  // 리스트
  List<String> blackPink = ["제니", "지수", "로제", "리사"];
  List<int> numbers = [1, 2, 3, 4, 5, 6];

  print(blackPink); // [제니, 지수, 로제, 리사]
  print(numbers); // [1, 2, 3, 4, 5, 6]

  // index
  // 순서
  print(blackPink[0]); // 제니

  print(blackPink.length); // 4

  blackPink.add("코드팩토리");

  print(blackPink); // [제니, 지수, 로제, 리사, 코드팩토리]

  blackPink.remove("코드팩토리");

  print(blackPink); // [제니, 지수, 로제, 리사]

  print(blackPink.indexOf("로제"));
}
```

- Map

```dart
void main() {
  // Map
  // Key / Value
  Map<String, String> dictionary = {
    "Harry Potter": "해리포터",
    "Ron Weasley": "론 위즐리",
    "Hermione Granger": "헤르미온느 그레인저",
  };

  print(dictionary);

  Map<String, bool> isHarryPotter = {
    "Harry Potter": true,
    "Ron Weasley": true,
    "Ironman": false,
  };

  print(isHarryPotter);

  isHarryPotter.addAll({
    "Spiderman": false,
  }); // 마지막에 추가 가능

  print(isHarryPotter); // 마지막에 추가됨

  print(isHarryPotter["Ironman"]); // false

  isHarryPotter["Hulk"] = false;

  print(isHarryPotter); // 끝에 추가

  isHarryPotter["Spiderman"] = true;

  print(isHarryPotter); // true로 변경

  print(isHarryPotter.keys); // key 값만 가져오기
  print(isHaaryPotter.values); // value 값만 가져오기
}
```

- Set

```dart
void main() {
  // Set
  final Set<String> names = {
    "Code Factory",
    "Flutter",
    "Black Pink",
  };

  print(names);

  names.add("Jenny");

  print(names); // 추가

  names.remove("Jenny");

  print(names); // 삭제

  print(names.contains("Flutter")); // true
}
```

- if문

```dart
void main() {
  // if 문
  int number = 2;
  
  if (number % 2 == 0) {
    print("값이 짝수입니다.");
  }
}

void main() {
  int number = 3;

  if (number % 2 == 0) {
    print("값이 짝수입니다.");
  } else {
    print("값이 홀수입니다.");
  }
}

void main() {
  int number = 3;

  if (number % 3 == 0) {
    print("나머지가 0입니다.");
  } else if (number % 3 == 1) {
    print("나머지가 1입니다.");
  } else {
    print("나머지가 2입니다.");
  }
}
```

- switch 문

```dart
void main() {
  // switch 문

  int number = 3;

  switch (number % 3) {
    case 0:
      print("나머지가 0입니다.");
      break;
    
    case 1:
      print("나머지가 1입니다.");
      break;

    default:
      print("나머지가 2입니다.");
      break;
  }
}
```

- loop

```dart
void main() {
  // for loop
  for (int i = 0; i < 10; i++) {
    print(i); // 0 ~ 9까지 print
  }
}
```

```dart
void main() {
  // for loop
  int total = 0;

  List<int> numbers = [1, 2, 3, 4, 5, 6];

  for (int i = 0; i < numbers.length; i++) {
    total += numbers[i];
  }

  print(total); // 21

  total = 0;

  for (int number in numbers) {
    total += number;
  }

  print(total); // 21
}
```

```dart
void main() {
  // while loop

  int total = 0;

  while (total < 10) {
    total += 1;
  }

  print(total); // 10

  total = 0;

  // 보통 안씀
  do {
    total += 1;
  } while (total < 10);
  

  print(total); // 10
}
```

```dart
void main() {
  // while loop

  int total = 0;

  while (total < 10) {
    total += 1;

    if (total == 5) {
      break;
    }
  }

  print(total); // 5

  total = 0;

  for (int i = 0; i < 10; i++) {
    total += 1;
    if (total == 5) {
      break;
    }
  }

  print(total); // 5
}
```

```dart
void main() {
  // while loop
  for (int i = 0; i < 10; i++) {
    if (i == 5) {
      continue;
    }
    print(i); // 5만 빼고 0 ~ 9 까지 출력
  }

}
```

- enum

  - 오타 방지
  - 미래의 나 혹은 다른 사람들에게도 알기 쉽게

```dart
enum Status {
  approved, // 승인
  pending, // 대기
  rejected, // 거절
}

void main() {
  Status status = Status.approved;

  if (status == Status.approved) {
    print("승인입니다.");
  } else if (status == Status.pending) {
    print("대기입니다.");
  } else {
    print("거절입니다.");
  }
}
```

- 함수

  - 반복되는 로직 재활용

```dart
void main() {
  addNumbers();
}

// 세 개의 숫자 (x, y, z)를 더하고 짝수인지 홀수인지 알려주는 함수
addNumbers() {
  print("addNumbers 실행");
  int x = 10;
  int y = 20;
  int z = 30;

  int sum = x + y + z;

  print("x : $x");
  print("y : $y");
  print("z : $z");

  if (sum % 2 == 0) {
    print("짝수입니다.");
  } else {
    print("홀수입니다.");
  }
}
```

```dart
void main() {
  addNumbers(10, 20, 30);
}

addNumbers(int x, int y, int z) {
  int sum = x + y + z;

  print("x : $x");
  print("y : $y");
  print("z : $z");

  if (sum % 2 == 0) {
    print("짝수입니다.");
  } else {
    print("홀수입니다.");
  }
}
```

- optional parameter

  - 없어도 되는 parameter에 []를 씌운다.
  - 기본값 설정 가능
  - 기본값 대신 값을 넣으면 그 값으로 대체된다.

```dart
void main() {
  addNumbers(10, 20, 30);
}

addNumbers(int x, [int y = 20, int z = 30]) {
  int sum = x + y + z;

  print("x : $x");
  print("y : $y");
  print("z : $z");

  if (sum % 2 == 0) {
    print("짝수입니다.");
  } else {
    print("홀수입니다.");
  }
}
```

- named parameter

```dart
void main() {
  addNumbers(x: 10, y: 20, z: 30);
}

addNumbers({
  required int x,
  required int y,
  required int z, // required 를 넣지 않으면 optional parameter 가능
}) {
  int sum = x + y + z;

  print("x : $x");
  print("y : $y");
  print("z : $z");

  if (sum % 2 == 0) {
    print("짝수입니다.");
  } else {
    print("홀수입니다.");
  }
}
```

- void 의 역할

  - 값을 반환
  - return 을 명시해주지 않은 것

- arrow function

```dart
void main() {
  int result = addNumbers(10, y: 20);
}

int addNumbers(int x, {
  required int y,
  int z = 30,
}) => x + y + z;

```

- typedef

```dart
void main() {
  Operation operation = add;

  int result = operation(10, 20, 30);

  print(result); // 60

  operation = subtract;

  int result2 = operation(10, 20, 30);

  print(result2); // -40
}

// signature
typedef Operation = int Function(int x, int y, int z);

// 더하기
int add(int x, int y, int z) => x + y + z;

// 빼기
int subtract(int x, int y, int z) => x - y - z;
```

- typedef 현실적인 사용법

```dart
void main() {
  int result3 = calculate(30, 40, 50, add);

  print(result3); // 120

  int result4 = calculate(40, 50, 60, subtract);

  print(result4); //-70
}

typedef Operation = int Function(int x, int y, int z);

int add(int x, int y, int z) => x + y + z;

int subtract(int x, int y, int z) => x - y - z;

int calculate(int x, int y, int z, Operation operation) {
  return operation(x, y, z)
}

```