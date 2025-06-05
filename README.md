**Flutter 학습일지**

flutter doctor <br>
flutter pub get <br>
flutter run -d chrome <br>

MariaDB <br>
Service Name : MariaDB <br>
TCP port : 3306 <br>

**flutter project 구조** <br>
android : 안드로이드 프로젝트 관련 파일 (안드로이드 스튜디오로 실행 가능) <br>
ios : ios 프로젝트 관련 파일 (엑스코드로 실행가능-맥전용) <br>
lib : 플러터 앱 개발을 위한 다트 파일 (플러터 sdk 설치 필요) <br>
test : 플러터 앱 개발 중 테스트 파일 (테스트 편의성 제공) <br>

<br>

**루트에 있는 파일** <br>
pubspec.yaml : 패키지, 이미지, 폰트 설정 (직접 관리) <br>
README.md : 프로젝트 소개 (직접 관리) <br>
.gitignore : git에 커밋,푸쉬 등 소스 코드를 업로드 할 때 필요 없는 파일 기록 (직접관리) <br>
.metadata : Flutter SDK 정보 (자동 관리) <br>
.packages : Flutter SDK에 사용하는 기본 패키지 경로 (자동 관리) <br>
first_flutter_app.iml : 파일이 자동으로 생성될 때 만들어지는 폴더 위치 (자동 관리) <br>
pubspec.lock : pubspec.yaml파일에 적용된 패키지 위치 (자동 관리) <br>

<br>

Flutter 메인 Source 파일 - main.dart <br>
```
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  // This widget is the root of your application.
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      theme: ThemeData(
        colorScheme: ColorScheme.fromSeed(seedColor: Colors.deepPurple),
        useMaterial3: true,
      ),
      home: const MyHomePage(title: 'Flutter Demo Home Page'),
    );
  }
}

class MyHomePage extends StatefulWidget {
```

<br>

runApp()함수는 binding.dart 클래스에 정의되어 있으며 플러터 앱을 시작하는 역할을 한다. 이 함수에 플러터 앱을 시작하면서 화면에 표시할 위젯을 전달한다. <br>

<br>

```
class MyApp extends StatelessWidget {
  const MyApp({super.key});

  // This widget is the root of your application.
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      theme: ThemeData(
        colorScheme: ColorScheme.fromSeed(seedColor: Colors.deepPurple),
        useMaterial3: true,
      ),
      home: const MyHomePage(title: 'Flutter Demo Home Page'),
    );
  }
}
```

<br>

extends를 통해 **StatelessWidget**이라는 클래스를 상속받는다. <br>
MyApp 클래스에서는 @override 애너테이션을 이용해 build()라는 함수를 재정의하였다. <br>
build()함수에서 어떤 위젯을 만들 것인지를 정의 한다.

처음 runApp()을 이용해 클래스를 실행할 때는 MaterialApp()함수를 반환해야 한다. MaterialApp()함수는 그림을 그리는 도구에 속하는 title. theme, home등이 정의되어 있다. <br>

<br>

**상태 연결에 따른 위젯 구분** <br>
플러터 앱을 구성하는 위젯은 **stateless**와 **statefull** 두 가지로 구분할 수 있다. <br>

stateless위젯은 내용을 갱신할 필요가 없어 화면에 보이기 전에 모든 로딩을 마친다. 이렇듯 상태를 연결할 필요가 없는 위젯을 stateless위젯이라고 하며 **StatelessWidget**클래스를 상속받아 만든다. <br>
statefull위젯은 내용을 갱신할 필요가 있어 앱이 위젯의 상태를 감시하다가 위젯이 특정 상태가 되면 알맞은 처리를 한다. 이처럼 상태가 연결된 동적인 위젯을 statefull위젯이라고 하며 **StatefullWidget**클래스를 상속받아 만든다. <br>

