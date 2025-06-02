**Dart언어** <br>

모든 Dart프로그램은 반드시 하나의 main 함수를 포함하고 있어야한다.
```
void main() {
  print('Hello, World!');
}
```

<br>

모든 Dart언어로 만든 프로그램들은 실행과 함께 main함수로 진입한다. 이후 main함수를 종료하는 행위는 프로그램을 끝낸다는 의미이다. <br>
(main함수가 만드는 결과 값은 운영체제에게 전달되어 프로그램이 정상적으로 수행된 건지 비정상적으로 수행된 건지 등을 알려주는 목적으로 사용된다.) <br>

<br><br>

**1. 기초적인 숫자와 문자 다루기** <br>

Dart언어에서 숫자는 정수와 실수로 나뉜다. 그리고 이러한 숫자 중 값이 계속 변경 가능한 **변수**와 한번 값이 정해지면 바뀔 수 없는 **상수**가 있다. <br>
글자들을 저장하는 문자열(String)도 값이 정해지면 바뀌지 않는 **상수**와 값을 바꿀 수 있는 **변수**가 있다. <br>

- int : 정수
- double : 실수
- num : 숫자, 정수 혹은 실수
- String : 문자열 (글자, 단어 혹은 문장)
- var : 변수(정수, 실수, 문자열 등을 저장하며 값의 변경가능, **한번 값을 저장하고 나면 같은 타입의 값을 저장해야 한다.**)
- dynamic : 변수(정수, 실수, 문자열 등을 저장하며 값의 변경 가능, **저장하는 값의 타입에 제한 없음**)
- constant : 상수(처음 만드는 시점에 값을 설정하며, 값의 변경 불가능)
- final : 상수(초기에 어떤 값도 가지지않는 상태로 만들어지고, 나중에 상수에 값을 저장할 수 있다. 단, 저장되고 난 뒤에는 값의 변경은 불가능하다.)

```
print("$varInt $varDouble $varString");
// 문자열 내부에 변수의 값을 가져와 출력한다.
```

사칙연산 <br>
- * : 곱하기
- / : 왼쪽 값을 오른쪽 값으로 나눔
- ~/ : 왼쪽 값을 오른쪽 값으로 나눈 몫을 정수로 계산
- % : 왼쪽 값을 오른쪽 값으로 나눈 나머지를 계산

<br><br>

**2. 문자 자세히 다루기** <br>
```
void main() {
  var str1 = 'Single Quotes';
  var str2 = "Double Quotes";
  var str3 = '"Double Quotes" in Single Quotes';
  var str4 = "'Single Quotes' in Double Quotes";
  var str5 = '\'Escape Delimiter\' in single Quotes';

  print("[1]\n$str1 \n$str2 \n$str3 \n$str4 \n$str5");

  str1 += '\n';
  str2 += '\n';
  str3 += '\n';
  str4 += '\n';
  str5 += '\n';
  var str6 = "[2]\n" + str1 + str2 + str3 + str4 + str5;
  print(str6);
}

[1]
Single Quotes 
Double Quotes 
"Double Quotes" in Single Quotes 
'Single Quotes' in Double Quotes 
'Escape Delimiter' in single Quotes
[2]
Single Quotes
Double Quotes
"Double Quotes" in Single Quotes
'Single Quotes' in Double Quotes
'Escape Delimiter' in single Quotes3e
```

toString() : 정수형 변수(혹은 상수)에 저장한 값을 문자열로 변환하는 방법.
toStringAsFixed(N) : 실수형 변수(혹은 상수)에 저장한 값을 문자열로 변환하는 방법, N에 문자열로 변환하고 싶은 실수의 소수점 이하 자릿수를 정한다.

<br><br>

**3. 조건문 다루기** <br>
if-else문과 switch문은 JAVA와 동일하므로 생략한다.<br>

**assert**조건문 : assert는 프로그램이 오류 상태여서 수행을 중단해야 하는지를 판단하는 경우에 주로 사용한다.
```
void main() {
  var programTermination = 'NORMAL';
  
  assert(programTermination == 'NORMAL');
  print("program terminated in normal.");
  
  programTermination = 'ERROR';
  assert(programTermination == 'NORMAL');
  print("program terminated in normal.");
}
// assert(true); 가 되어 아무런 일도 하지않고 다음 줄로 넘어간다.
// assert(false); 가 되어 프로그램이 비정상적으로 중단된다.
```

<br><br>

**4. 반복문으로 작업하기** <br>
for문과 while문은 JAVA와 동일하므로 생략한다.(do-while문도 동일하지만 익숙하지 않아 기록함.) <br>

**do-while문** : 반복할 작업이 반드시 한번은 수행이 된다는 특징을 갖는다. <br>
```
void main() {
  var number = 1;
  var count = 1;
  do {
    print("$number x $count = ${number * count}");
    count++;
  } while(count <= 3);
}
```

<br>

**continue** : 반복문 안에서 continue가 실행되면 반복문의 흐름이 업데이트 영역으로 이동한다. <br>
**break** : 반복문 안에서 break가 실행되면 프로그램의 흐름을 바로 반복문에서 나온 뒤 다음 작업으로 이동한다.

<br><br>

**5. 함수를 이용하여 반복 작업하기** <br>
```
getMax(3,2); // 3
getSum(3,2); // 5
getMaxNamed(argv1: 3, argv2: 2); // 3

// 함수에서 전달받아야 하는 입력 파라미터의 이름을 함수를 호출하는 시점에서 명시하고 입력 파라미터에게 줄 값을 콜론 기호를 사용하여 할당한다.
// 입력 파라미터의 순서가 바뀌어도 문제가 없다는 장점이 있다.

void main() {
  // Type.1 Normal Function
  int getMax(var argv1, var argv2) {
    if (argv1 >= argv2) {
      return argv1;
    } else {
      return argv2;
    }
  }

  // Type.2 Shorthand Syntax Function
  int getSum(var argv1, var argv2) => argv1 + argv2;

  // 한 줄 정도의 간단한 작업을 수행하는 함수는 굳이 중괄호를 사용하지 않고 수행할 일을 => 기호 뒤에 작성한다.
  // return구문도 사용하지 않고 => 기호 뒤의 문장은 세미클론으로 종료한다.

  // Type.3 Named Parameters
  int getMaxNamed({var argv1, var argv2}) {
    if (argv1 >= argv2) {
      return argv1;
    } else {
      return argv2;
    }
  }

  // 함수를 호출하는 쪽에서 입력 값의 순서가 의미가 없다.

  // Type.4 Optional and Default Parameters in Normal Function
    int getMaxDefault(var argv1, [var argv2 = 1]) {
      if (argv1 >= argv2) {
        return argv1;
      } else {
        return argv2;
      }
    }
  // 입력 파라미터를 주지 않은 경우 함수에서 미리 정한 초깃값으로 설정한다는 표현으로 []를 사용한다.

  // Type.5 Optional and Default Parameters in Named Parameters
  int getMaxNamedDefault({var argv1, var argv2 = 1}) {
    if(argv1 >= argv2) {
      return argv1;
    } else {
      return argv2;
    }
  }
  // 초깃값을 사용하면서 named parameter를 사용하는 경우 []를 사용하지않고 {}내에서 초깃값을 설정한다.
}

```

<br><br>

**6. Class를 이용하여 객체지향 프로그래밍 이해하기** <br>

Class는 일종의 설계도이며 객체(Object)는 설계도에서 찍어낸 실제 물건이라고 생각하면 된다. <br>

**자주 사용하는 클래스의 메서드** <br>

int Class <br>
- abs() : 절대 값을 계산한다.
- gcd() : 최대 공약수를 계산한다.
- toString() : 문자열로 변환한다.
double Class <br>
- abs() : 절대 값을 계산한다.
- gcd() : 최대 공약수를 계산한다.
- toString() : 문자열로 변환한다.
- floor() : 소수점 이하를 버리고 가까운 정수를 계산한다.
- round() : 가까운 정수를 계산한다.
String class <br>
- toLowerCase() : 소문자로 변환한다.
- toUpperCase() : 대문자로 변환한다.
- length() : 문자열의 길이를 계산한다.
- substring() : 문자열의 일부를 추출해서 새로운 문자열을 생성한다.
- [] : 문자열의 특정 글자를 반환한다.
bool class <br>
- toString() : 문자열로 변환한다.
- is : 왼쪽의 변수/상수가 오른쪽의 타입인지 검사한다.
- is! : 왼쪽의 변수/상수가 오른쪽의 타입이 아닌지 검사한다.

<br><br>

**7. List를 이용하여 복수 데이터 처리하기** <br>
List 클래스는 복수의 값을 저장할 수 있으며, 개발자가 지정한 순서대로 일렬로 저장하는 데이터 타입이다. <br>
저장되는 복수의 값은 동일한 데이터 타입일 수도 있고 서로 다른 데이터 타입을 함께 섞어서 저장할 수도 있다. <br>
Dart언어에서 List는 **대괄호[]** 로 묶어서 표현한다.

```
void main() {
  List iList = [1,2,3,4,5];
  
  iList.length;  // list의 길이
  iList.first;  // list의 가장 첫 element
  iList.last;  // list의 가장 마지막 element
  iList.indexOf(3);  // element 3이 list에서 몇번째 위치에 존재하는가 -> 0부터 시작하기때문에 3은 2번째에 위치하고 있다.

  for( var item in iList ) {...};
  // iList에 있는 element를 하나하나 item에 저장하도록 하는 for구문

  List<int> intList = [1,2,3,4,5];
  // List에 int타입의 값만을 넣을 수 있다.
}
```

<br><br>

**8. Set을 이용하여 집합 데이터 처리하기** <br>
Dart언어에서 집합은 중괄호 {}를 사용하여 표현한다.

```
void main() {
  Set setFill = {1,2};  // Set정의
  Set setEmpty = {};
  
  setFill.add(3);
  // 입력 파라미터가 집합에 추가된다, 추가하는 element가 이미 집합에 존재한다면 add()메서드는 무시된다.
  setEmpty.addAll([3,4,5]); // 입력 파라미터로 전달하는 집합의 element가 모두 추가된다.
  setFill.contains(3);  // 입력 파라미터로 전달된 값이 집합에 존재하면 true를 반환한다.
  setFill.union(setEmpty);  // 두 집합의 합집합을 반환한다.(집합에서 중복은 존재하지 않는다.)
  setFill.intersection(setEmpty); // 두 집합의 교집합을 반환한다.
  setFill.difference(setEmpty); // 메서드를 호출한 집합에만 존재하고 입력으로 받은 집합에는 존재하지않는 집합을 반환한다.
  setFill.remove(3);  // 입력 파라미터가 집합에 존재할 경우 집합에서 제거한다.
  
  Set<int> exSet1 = {1,2,3};  // 집합의 element를 특정 타입으로 제한할 수 있다.
}
```

<br><br>

**9. map을 이용하여 사전 데이터 처리하기** <br>
map은 key와 value의 쌍을 element로 갖는 데이터 타입이다. <br>
**map의 element들은 절대로 중복된 key를 가져서는 안되며 서로 다른 key는 같은 value를 가질 수도 있다.** <br>

<br><br>

**10. Dart 언어 기능 이해하기** <br>

- Cascade 연산자 이해하기
```
void main() {
  List iList = [];
  iList
    ..addAll([2,1])                 // iList에 2,1을 추가한다.
    ..add(0)                        // iList에 0을 추가한다.
    ..sort((a,b)=> a.compareTo(b)); // iList를 오름차순으로 정렬한다.
}
```
이처럼 같은 객체에 대한 메서드를 연속하여 호출하는 경우 Cascade연산자를 사용하여 보다 가독성을 높일 수 있다.

<br>

- forEach 메서드
```
void printStar(var item) {
  print("$item");
}

void main() {
  List iList = [];
  iList
    ..addAll([2,1])                 // iList에 2,1을 추가한다.
    ..add(0)                        // iList에 0을 추가한다.
    ..sort((a,b)=> a.compareTo(b)); // iList를 오름차순으로 정렬한다
  
  iList.forEach(printStar);
}
```
**forEach()메서드의 입력 파라미터는 함수이다.** <br>
위의 코드의 의미는 iList객체의 모든 element들을 printStar()함수의 입력 파라미터로 적용해서 실행하라는 것이다. <br>
ex) printStar(0), printStar(1), printStar(2)... <br>

<br>

- 지수 표현
알파벳 e를 이용하여 표시한다. <br>
ex) num varE = 1.1e2;  // 1.1의 2승을 의미 <br>

<br>

- 문자열을 숫자로 변환
```
num varI = int.parse('1');
num varD = double.parse('1.1');
```
<br>

- 나열형데이터
개발자가 새로운 데이터 타입을 만들 수 있도록 지원하는 문법 <br>
새로운 데이터 타입이 갖는 값은 몇 가지의 값들로 제한되며, 그 외의 값은 다루지 못한다. <br>
```
enum Color { red, green, blue }  // 새로운 데이터 타입을 정의

void main() {
  print(Color.values);    // Color타입의 값은 red, green, blue만 가질 수 있음
  Color chColor = Color.red;  // 객체에 값을 red로 초기화.
}
```
ex) 빛의 삼원색(red,green,blue) , 전기스위치(on,off) 등등.. <br>
