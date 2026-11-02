---
title: Open data
tags: [visiting, data]
last_updated: 2026-11-02
---

# Open data

The Visitor Office publishes a few data sets about the island. This page shows their format and
some examples of how to use them.

## Island summary (JSON)

```json
{
  "island": "Tessaluna",
  "villages": ["Highfold", "North Harbour", "Old Town", "South Harbour"],
  "lighthouse": { "lit": 212, "height_m": 31, "flashes": 2, "period_s": 10 }
}
```

## Ships (YAML)

```yaml
- ship: Vessaro Star
  seats: 320
  bicycles: true
- ship: Little Gull
  seats: 140
  bicycles: false
```

## Timetable (CSV)

```csv
departure,from,to,ship
07:00,South Harbour,Vessara Coast,Vessaro Star
09:15,South Harbour,Vessara Coast,Little Gull
11:30,Vessara Coast,South Harbour,Vessaro Star
```

The same data, with fares, is in the [timetable spreadsheet](../transport/ferry-timetable.ods).

## Querying the timetable (SQL)

```sql
SELECT ship, COUNT(*) AS crossings
FROM crossing
WHERE suspended = 0
GROUP BY ship
ORDER BY crossings DESC;
```

## Will the ferry sail? (Python)

```python
def ferry_sails(wind_knots: float, limit: float = 28.0) -> bool:
    """Crossings are suspended when the Spinner exceeds the limit."""
    return wind_knots <= limit

print(ferry_sails(31.5))  # False
```

## A booking service (PHP)

```php
<?php

final class Crossing
{
    public function __construct(
        private string $ship,
        private int $freeSeats,
    ) {
    }

    public function book(int $seats): bool
    {
        if ($seats > $this->freeSeats) {
            return false;
        }
        $this->freeSeats -= $seats;
        return true;
    }
}
```

## Listing the crossings (JavaScript)

```javascript
const crossings = [
  { ship: 'Vessaro Star', time: '07:00' },
  { ship: 'Little Gull', time: '09:15' },
];
crossings.forEach((c) => console.log(`${c.time} ${c.ship}`));
```

## Downloading the files (shell)

```bash
#!/bin/sh
for file in summary.json ships.yaml timetable.csv; do
  echo "Downloading $file"
done
```

The `freeSeats` counter in the example never goes below zero, and `$file` is a shell variable.

    The Visitor Office updates the data sets every Monday.
