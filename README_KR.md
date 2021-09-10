<h1 align="center">📜<br>BetterMsgBot-structure</h1>

<p align="center">
이 문서는 'BetterMsgBot' 와 `Project StarLight`에 적용된<br>
표준 API 구조 및 설계 방식에 대해 서술합니다
</p>

> **Note**: 아직 개발중인 구조입니다. 원하시는 구조가 있다면 고민없이 pr넣어주세요.

### 설계 방식
+ 모든 `core API` 및 `확장 API`는 하나의 Api 클래스로 
묶는것이 아닌 용도를 특정할 수 있는 단위 클래스로 나눠 표시합니다.
  + ex)
  + `Projects.get(projectName);`
  + `Timer.schedule(duration, callback);`

+ `API1`의 `Function-based` 방식이 아닌 `EventEmitter`
방식을 사용합니다. 이하에선 편의를 위해 `BotClient`로 명시합니다.
> `Project StarLight` 한정으로, `EventEmitter` 클래스는 
> 플러그인에 대한 확장성을 제공합니다.

+ 실행 가능한 언어를 `Language` 객체로 정의합니다.
+ 하나의 봇을 포함하는 단위를 `Project` 객체로 정의합니다.
  + `Project` 내에는 봇 설정과 언어의 컴파일된 `engine` 객체를 포함합니다.

### Core API
+ `BotClient`
  + `EventEmitter` 방식의 이벤트 리스너 객체
  + 이하 명시할 이벤트 타입을 사용해 이벤트 수신
    + `on(eventType, callBack)`
      + `eventType`에 상응하는 이벤트 리스너 등록
      ####
    + `once(eventType, callBack)`
      + `eventType`에 상응하는 *한번만 호출되는* 리스너 등록

### 확장 API
+ `Languages`
  + 특정 언어에 대한 객체 반환
    + `get()`
      + 현재 프로젝트의 언어 반환
    + `get(languageId)`
      + `languageId`를 ID 로서 가지는 언어 반환, 없을 시 `null` 반환
####
+ `Projects`
  + 특정 프로젝트에 대한 객체 반환
    + `get()`
      + 현재 프로젝트 반환
    + `get(projectName)`
      + `projectName`을 이름으로서 가지는 프로젝트 반환, 없을 시 `null` 반환
####
+ `Timer`
  + 비동기적으로 작동하는 타이머 설정
    + `schedule(delay, callback)`
      + `delay` 이후 `callback`을 호출하는 타이머 설정 (millisecond로 처리)
      + `java.util.Timer` 반환
    ####
    + `schedule(initialDelay, period, callback)`
      + `initialDelay` 이후 `period`마다 `callback`을 호출하는 순환 타이머 설정 (millisecond로 처리)
      + `java.util.Timer` 반환

###### /* 추후 추가 예정 */

### 이벤트 타입
+ `BotClient`에서 사용 가능한 기본 이벤트 타입
+ [SpreadSheet 문서](https://docs.google.com/spreadsheets/d/103k-cqYOIrk9ZpHiu1ZbEKqFNTkxnJXrrPJKfLvxUlY)

