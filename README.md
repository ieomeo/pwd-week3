# 3주차 실습 · TypeScript 웹 계산기 (pwd-week3)

TypeScript, HTML5, CSS3를 활용하여 제작한 웹기반 객체/함수형 로직 분리 계산기 프로젝트입니다.

---

## 1. 프로젝트 소개
* **사칙연산 및 유효성 검사**: 덧셈, 뺄셈, 곱셈, 나눗셈 계산 및 0으로 나누기 예외 처리
* **입력 유틸리티**: 지우기(⌫), 전체 초기화(AC), 퍼센트(%), 부호 전환(+/−) 지원
* **관심사 분리 (Separation of Concerns)**:
  * `operations.ts`: 순수 사칙연산 함수 모듈
  * `calculator.ts`: 계산 상태 및 입력 처리 로직
  * `app.ts`: DOM 이벤트 연결 및 화면 렌더링

---

## 2. 프로젝트 실행 방법

1. 의존성 도구 설치 (TypeScript 등)
npm install

2. TypeScript 코드 검사 및 JavaScript 컴파일
npm run check
npm run build

3. 결과 확인
탐색기에서 index.html을 열거나 브라우저에서 직접 실행

---

## 3. 주요 동작 및 담당 파일·함수 정리

* **사칙연산 계산**: `operations.ts`의 `add`, `subtract`, `multiply`, `divide`, `calculate` 함수가 담당하며 12 + 3 = 15, 12 / 3 = 4와 같이 정확한 계산 결과를 반환합니다.
* **0 나누기 오류 처리**: `operations.ts`의 `divide` 함수 및 `calculator.ts`의 `handleKey` (try-catch) 구조가 담당하며 12 / 0 = 입력 시 Error 및 "0으로 나눌 수 없습니다." 예외 메시지를 표시합니다.
* **입력 삭제 (⌫)**: `calculator.ts`의 `handleKey` (`key === 'delete'`) 로직이 담당하며 현재 입력 중인 마지막 숫자 1자리를 지웁니다.
* **부호 전환 (+/−)**: `calculator.ts`의 `handleKey` (`key === 'sign'`) 로직이 담당하며 입력된 양수/음수 부호를 반전합니다.
* **퍼센트 연산 (%)**: `calculator.ts`의 `handleKey` (`key === 'percent'`) 로직이 담당하며 현재 숫자를 100으로 나눈 값으로 변경합니다.
* **천 단위 쉼표 표기**: `app.ts`의 `formatDisplay` 함수가 담당하며 정수 부분에 천 단위 ,를 자동으로 삽입하여 6,110,000 형태로 출력합니다.
* **화면 갱신 및 DOM 반영**: `app.ts`의 `render` 함수가 담당하며 상태(state)의 변화를 감지하여 `#display`와 `#expression` 화면 요소를 갱신합니다.