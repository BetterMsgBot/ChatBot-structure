<h1 align="center">π<br>ChatBot-structure</h1>

<p align="center">
μ΄ λ¬Έμλ 'BetterMsgBot' μ `Project StarLight`κ° μ¬μ©νλ<br>
νμ€ API κ΅¬μ‘° λ° μ€κ³ λ°©μμ λν΄ μμ ν©λλ€.
</p>

> **Note**: μμ§ κ°λ° μ€μΈ κ΅¬μ‘°μλλ€. κ΅¬μ‘°λ₯Ό μμ νκ³  μΆμΌμλ©΄ κ³ λ―Ό μμ΄ PRμ λ£μ΄ μ£ΌμΈμ.

### μ€κ³ λ°©μ
+ λͺ¨λ  `core API` λ° `νμ₯ API`λ λ¨μΌ ν΄λμ€(Api)λ‘ 
λ¬Άμ§ μκ³ , λͺ©μ μ κ΅¬λΆνμ¬ λ¨μ ν΄λμ€λ‘ λλλλ€.
  + ex)
    + `Projects.get(projectName)`
    + `Timer.schedule(duration, callback)`

+ `API 1`μ λ¨μΌ μ½λ°± ν¨μ κΈ°λ° λ°©μμ΄ μλ `EventEmitter`
λ°©μμ μ¬μ©ν©λλ€. μ΄νμμ  μ΄ μλ‘μ΄ λ°©μμ `BotClient`λ‘ λΆλ¦λλ€.
> `Project StarLight` νμ μΌλ‘, `EventEmitter` ν΄λμ€λ 
> νλ¬κ·ΈμΈμ μν νμ₯μ±μ μ κ³΅ν©λλ€.

+ μ€ν κ°λ₯ν μΈμ΄λ₯Ό `Language` κ°μ²΄λ‘ μ μν©λλ€.
+ νλμ λ΄ μΈμ€ν΄μ€λ₯Ό `Project` κ°μ²΄λ‘ μ μν©λλ€.
  + `Project` κ°μ²΄λ λ΄ μ€μ κ³Ό μ»΄νμΌλ `engine` κ°μ²΄λ₯Ό ν¬ν¨ν©λλ€.

### Core API
+ `BotClient`
  + `EventEmitter` λ°©μμ μ΄λ²€νΈ λ¦¬μ€λ κ°μ²΄
  + μλμ λͺμλ μ΄λ²€νΈ νμμ μ¬μ©ν΄ μ΄λ²€νΈ μμ 
    + `on(eventType, callBack)`
      + `eventType` μ νμ μ΄λ²€νΈ λ¦¬μ€λλ₯Ό λ±λ‘ν¨
      ####
    + `once(eventType, callBack)`
      + *ν λ²λ§ νΈμΆλλ* `eventType` μ νμ λ¦¬μ€λλ₯Ό λ±λ‘ν¨

### νμ₯ API
+ `Languages`
  + νΉμ  μΈμ΄μ λν κ°μ²΄ λ°ν
    + `get()`
      + νμ¬ νλ‘μ νΈμ μΈμ΄ λ°ν
    + `get(languageId)`
      + IDκ° `languageId`μΈ μΈμ΄ λ°ν, μμ μ `null` λ°ν
####
+ `Projects`
  + νΉμ  νλ‘μ νΈμ λν `BotProject` κ°μ²΄ λ°ν
    + `get()`
      + νμ¬ νλ‘μ νΈ λ°ν
    + `get(projectName)`
      + μ΄λ¦μ΄ `projectName`μΈ νλ‘μ νΈ λ°ν, μμ μ `null` λ°ν
    + `getUptime()`
      + νμ¬ νλ‘μ νΈμ μνμμ λ°ν
    + `getUptime(projectName)`
      + μ΄λ¦μ΄ `projectName`μΈ νλ‘μ νΈμ μνμμ λ°ν, ν΄λΉ νλ‘μ νΈκ° μκ±°λ κΊΌμ Έ μλ€λ©΄ `null` λ°ν
####
+ `Timer`
  + λΉλκΈ°μ μΌλ‘ μλνλ νμ΄λ¨Έλ₯Ό μ€μ ν¨
    + `schedule(delay, callback)`
      + `delay` μ΄ν `callback`μ νΈμΆνλ νμ΄λ¨Έλ₯Ό μ€μ ν¨ (λ°λ¦¬μ΄ λ¨μ)
      + `java.util.Timer` λ°ν
    ####
    + `schedule(initialDelay, period, callback)`
      + `initialDelay` μ΄ν `period`λ§λ€ λ°λ³΅μ μΌλ‘ `callback`μ νΈμΆνλ νμ΄λ¨Έλ₯Ό μ€μ ν¨ (λ°λ¦¬μ΄ λ¨μ)
      + `java.util.Timer` λ°ν

###### /* μΆν μΆκ° μμ  */

### μ΄λ²€νΈ νμ
+ `BotClient`μμ μ¬μ© κ°λ₯ν κΈ°λ³Έ μ΄λ²€νΈ νμ
+ [SpreadSheet λ¬Έμ](https://docs.google.com/spreadsheets/d/103k-cqYOIrk9ZpHiu1ZbEKqFNTkxnJXrrPJKfLvxUlY)
