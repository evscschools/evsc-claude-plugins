---
name: google-apps-script
description: "Use when writing or editing any .gs file for Google Apps Script. Enforces GAS-specific patterns for triggers, PropertiesService, SpreadsheetApp, and the 6-minute execution limit."
---

## Google Apps Script Constraints

### Execution & Timing
- Hard 6-minute execution limit per invocation — never write code that assumes unlimited runtime
- Use `PropertiesService.getScriptProperties()` for state that must survive across trigger invocations
- Time-budget pattern: check `(new Date() - startTime) / 1000 > MAX_RUN_SECONDS` inside batch loops; save position and schedule a retry trigger if exceeded
- `ScriptApp.newTrigger().timeBased().after(ms).create()` for one-shot retry triggers; always save the trigger ID so it can be cleaned up

### Triggers
- Always delete stale triggers before creating new ones — GAS has a hard limit on total triggers per project
- Use `ScriptApp.getProjectTriggers()` + loop to find and delete by handler function name before creating
- `onOpen` is a simple trigger — it cannot call services that require authorization (use installable triggers instead)

### SpreadsheetApp
- Batch reads/writes — never call `getRange().getValue()` inside a loop; read the whole range once, process in memory, write once
- `sheet.getRange(1, 1, rows, cols).getValues()` returns a 2D array — always index as `data[row][col]`
- `SpreadsheetApp.flush()` forces pending writes — use sparingly; it costs execution time

### Scope & Globals
- All `.gs` files share a single global scope — no imports/exports; functions and variables declared at top level are available everywhere
- Avoid naming conflicts across files — prefix internal helpers with `_` if they should be treated as private

### Error Handling
- Wrap all external API calls (UrlFetchApp, AdminDirectory, SpreadsheetApp on external sheets) in try/catch
- `UrlFetchApp.fetch()` throws on network errors — always catch and log; never let an uncaught exception abort a sync mid-batch
- Use `muteHttpExceptions: true` on fetch options and check `response.getResponseCode()` explicitly

### PropertiesService
- String values only — always `JSON.stringify()` before set, `JSON.parse()` after get
- Max value size: 9KB per property — chunk large objects if needed
- `getScriptProperties()` is shared across all executions; `getUserProperties()` is per-user

### Logging
- `Logger.log()` output is visible in Apps Script Executions panel — use for debugging
