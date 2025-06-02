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


6. 
