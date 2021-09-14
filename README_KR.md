<h1 align="center">📜<br>ChatBot-structure</h1>

<p align="center">
이 문서는 'BetterMsgBot' 와 `Project StarLight`가 사용하는<br>
표준 API 구조 및 설계 방식에 대해 서술합니다.
</p>

> **Note**: 아직 개발 중인 구조입니다. 구조를 수정하고 싶으시면 고민 없이 PR을 넣어 주세요.

### 설계 방식
+ 모든 `core API` 및 `확장 API`는 단일 클래스(Api)로 
묶지 않고, 목적을 구분하여 단위 클래스로 나눕니다.
  + ex)
    + `Projects.get(projectName)`
    + `Timer.schedule(duration, callback)`

+ `API 1`의 단일 콜백 함수 기반 방식이 아닌 `EventEmitter`
방식을 사용합니다. 이하에선 이 새로운 방식을 `BotClient`로 부릅니다.
> `Project StarLight` 한정으로, `EventEmitter` 클래스는 
> 플러그인을 위한 확장성을 제공합니다.

+ 실행 가능한 언어를 `Language` 객체로 정의합니다.
+ 하나의 봇 인스턴스를 `Project` 객체로 정의합니다.
  + `Project` 객체는 봇 설정과 컴파일된 `engine` 객체를 포함합니다.

### Core API
+ `BotClient`
  + `EventEmitter` 방식의 이벤트 리스너 객체
  + 아래에 명시된 이벤트 타입을 사용해 이벤트 수신
    + `on(eventType, callBack)`
      + `eventType` 유형의 이벤트 리스너를 등록함
      ####
    + `once(eventType, callBack)`
      + *한 번만 호출되는* `eventType` 유형의 리스너를 등록함

### 확장 API
+ `Languages`
  + 특정 언어에 대한 객체 반환
    + `get()`
      + 현재 프로젝트의 언어 반환
    + `get(languageId)`
      + ID가 `languageId`인 언어 반환, 없을 시 `null` 반환
####
+ `Projects`
  + 특정 프로젝트에 대한 객체 반환
    + `get()`
      + 현재 프로젝트 반환 이때 `BotProject` 클래스 반환
    + `get(projectName)`
      + 이름이 `projectName`인 프로젝트 반환 이때 `BotProject` 클래스 반환, 없을 시 `null` 반환
####
+ `Timer`
  + 비동기적으로 작동하는 타이머를 설정함
    + `schedule(delay, callback)`
      + `delay` 이후 `callback`을 호출하는 타이머를 설정함 (밀리초 단위)
      + `java.util.Timer` 반환
    ####
    + `schedule(initialDelay, period, callback)`
      + `initialDelay` 이후 `period`마다 반복적으로 `callback`을 호출하는 타이머를 설정함 (밀리초 단위)
      + `java.util.Timer` 반환

###### /* 추후 추가 예정 */

### 이벤트 타입
+ `BotClient`에서 사용 가능한 기본 이벤트 타입
+ [SpreadSheet 문서](https://docs.google.com/spreadsheets/d/103k-cqYOIrk9ZpHiu1ZbEKqFNTkxnJXrrPJKfLvxUlY)
