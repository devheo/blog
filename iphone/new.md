---
description: 아이폰
---

# New 글로벌 뱅킹 개발 가이드



1. 프로젝트 구조 정의

* WON기업 파일 구조 및 앱 구동 구조를 준수하되, 화면 및 이벤트 처리는 SwiftUI와 Combine을 사용한다.
  * App 파일 내에 AppDelegate를 생성하여 APNs, 위젯 실행 등 Delegate 함수를 사용한다.
  * Combine을 사용해 데이터 바인딩 처리한다.
  * viewModel을 따로 분리하지 않고 MVC방식으로 구현한다.
* WebView는 업무용, 제휴용을 분리하되 web-app I/F를 위한 Delegate는 동일한 소스를 바라보게 구현 한다.
* 3단계 이상의 복잡한 상속관계는 지양한다.
* 파일 및 폴더는 알파벳 순서로 정렬한다.

2. 네이밍 규칙&#x20;

* 네이밍 및 컨벤션은 아래 Swift APi Design Guideline을 준수한다.
  * [https://www.swift.org/documentation/api-design-guidelines/](https://www.swift.org/documentation/api-design-guidelines/)
* WON기업 네이밍 규칙을 기본적으로 준수한다.
* 안드로이드 프로젝트와 동일한 네이밍을 지향한다.

3. 주석 규칙&#x20;

* func, enum, 등 구역 설정이 필요한 주석은 mark 주석을 반드시 포함시킨다.
* 주석은 file, 상수, 변수, 함수 모두 있어야 하며, 소스레벨의 설명 주석은 복잡한 로직 포함시 추가 한다.
* 주석은  cmd + opt + / 를 사용하여 추가한다.
  * 메소드 별 역할 및 파라미터 설명을 주석으로 추가 (기업소스 참조)

4. 통신규칙&#x20;

* 네이티브 통신은 nsurlsession 을 기반한 모듈, webview는 wkwebview를 기반한 모듈을 이용한다.
* 네이티브 통산과 webview 통신간 세션 문제가 발생하지 않게 개발한다.
* web-app간 I/F는 커스텀프로토콜을 이용하는 형식을 기본으로 한다.
* 단, 리액트 등의 환경 문제로 JS브릿지를 이용할 경우, 보안상의 이슈를 없애면 이용 가능 하다.

5. 기타 제약 사항

* 동적 오픈소스(cocoa pod) 등 이용 금지
* Swift5 language 사용
* 시뮬레이터 빌드 가능환경으로 개발 - 필요 시 타겟 분리
* 주로 사용되는 폰트, 컬러, 이미지명은 하드코딩 대신 enum 이나 상수로 선언하여 사용



\[활용 권장 라이브러리]

* 네트워크 라이브러리 : Alamofire
* Xml parser : SwiftyXMLParser
* 로그출력 : swift-log
* 암호화 : CryptoSwift
* 코딩 컨벤션 : SwiftLint
* 이미지 캐싱 : Kingfisher

