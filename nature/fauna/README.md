---
title: Fauna
tags: [nature, animals]
last_updated: 2026-11-02
---

# Fauna

| Animal | Habitat | Active |
|---|---|---|
| [Silver snail](silver-snail.md) | meadows | at night |
| [Copper crab](copper-crab.md) | salt pans | by day |
| [Spinner falcon](spinner-falcon.md) | cliffs | by day |

```mermaid
classDiagram
    class Animal {
        +String name
        +String habitat
        +move()
    }
    class SilverSnail {
        +glow()
    }
    class CopperCrab {
        +dig()
    }
    class SpinnerFalcon {
        +hover()
    }
    Animal <|-- SilverSnail
    Animal <|-- CopperCrab
    Animal <|-- SpinnerFalcon
```
