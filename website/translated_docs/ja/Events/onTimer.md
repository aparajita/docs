---
id: onTimer
title: On Timer
---

| Code | Can be called by | 定義                                                                |
| ---- | ---------------- | ----------------------------------------------------------------- |
| 27   | フォーム             | The number of ticks defined by the `SET TIMER` command has passed |


## 説明

This event is generated only if the form method contains a previous call to the `SET TIMER` command.

When the `On Timer` form event property is selected, only the form method will receive the event, no object method will be called.