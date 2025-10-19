---
labels:
  products:
    - oss
title: 'Mute timings vs silences'
---

## Mute timings vs silences

* ways to suppress notifications (!= evaluate alerts)
  * [Mute & active timings](ref:shared-mute-timings)
  * [silences](ref:shared-silences)

|            | Mute timing                                              | Silence                         |
| ---------- |----------------------------------------------------------|---------------------------------|
| **Setup**  | create <br/> add \| notification policies                | matches alerts -- via -- labels |
| **Period** | time interval definitions / can be repeated PERIODICALLY | fixed start & end time          |
