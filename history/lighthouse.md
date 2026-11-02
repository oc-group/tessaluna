---
title: The Long Point Lighthouse
tags: [history, landmarks, sea]
last_updated: 2026-11-02
---

# The Long Point Lighthouse

The lighthouse was lit in **212 AL** on Long Point, the northern tip of the island. It is a white
tower with green bands, 31 metres tall.

![The lighthouse](../assets/lighthouse.png)

## The keeper

For two centuries a keeper lived in the cottage at the foot of the tower and wrote down every
night in [[lighthouse-log|the log]]. Today the light is automatic and the cottage is a small
museum: see [[keeper's cottage]].

## The light

| Feature | Value |
|---|---|
| Colour | white |
| Character | two flashes every 10 seconds |
| Range | 18 nautical miles |

```mermaid
stateDiagram-v2
    [*] --> Off
    Off --> On: sunset
    On --> Flash: every 5 s
    Flash --> On
    On --> Off: sunrise
    On --> Fog: low visibility
    Fog --> On: clear again
```

The lighthouse is at the heart of [[lantern night|Lantern Night]].
