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

1. 기초적인 숫자와 문자 다루기

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

2. 문자 자세히 다루기
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

3. 
4. 
