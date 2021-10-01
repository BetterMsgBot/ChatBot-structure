<h1 align="center">📜<br>ChatBot-structure</h1>

<p align="center">
This documentation defines common API structure used in
<br>'BetterMsgBot' and `Project StarLight`
</p>

> **Note**: This structure is still under development. If you want to modify structure, please put PR without any worries.

### Structure design approach
+ Every `core API`s and `extension API`s are grouped into several classes
with distinct purposes, not into single `Api` class.
    + Examples
        + `Projects.get(projectName)`
        + `Timer.schedule(duration, callback)`

+ Uses `EventEmitter` method instead of `Function-based` method used in
`API 1`. In the following, this new method is designated as `BotClient`.
> For `Project StarLight`, `EventEmitter` class offers
> extension support for plugins.

+ Defines an executable programming language object as `Language`.
+ Defines a bot instance as `Project`.
    + `Project` object includes bot configuration and compiled `engine` object.

### Core API
+ `BotClient`
    + An event listener object of `EventEmitter` system
    + Uses the event types described below
        + `on(eventType, callback)`
            + Registers event listener of `eventType`
          ####
        + `once(eventType, callback)`
            + Registers `one-time` event listener of `eventType`

### Extension API
+ `Languages`
    + Returns an object for specific language
        + `get()`
            + Returns the language used in current project
        + `get(languageId)`
            + Returns the language whose id is `languageId`,
          otherwise returns `null`
####
+ `Projects`
    + Returns an object for specific project
        + `get()`
            + Returns current project is `BotProject`
        + `get(projectName)`
            + Returns the project named `projectName` is `BotProject`,
          otherwise returns `null`
        + `getUptime()`
            + Returns current project Uptime
        + `getUptime(projectName)`
            + Returns the project named `projectName` Uptime,
          otherwise returns `null`
####
+ `Timer`
    + Sets the timer which works asynchronously
        + `schedule(delay, callback)`
            + Runs `callback` after `delay` (in millisecond)
            + Returns `java.util.Timer`
      ####
        + `schedule(initialDelay, period, callback)`
            + Runs `callback` every `period` after `initialDelay` (in millisecond)
            + Returns `java.util.Timer`

###### /* To be continued.. */

### Event types
+ Basic event types that can be used on `BotClient`
+ [Spreadsheet document](https://docs.google.com/spreadsheets/d/103k-cqYOIrk9ZpHiu1ZbEKqFNTkxnJXrrPJKfLvxUlY)
