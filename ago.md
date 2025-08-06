# Ago

- Calculates past date relative to the current date

## Print 1 Hour

```KQL
print ago(1h)
```

## All time unites

```KQL
print OneDay         = ago(1d), // Day
      OneHour        = ago(1h),   // Hour
      OneMinute      = ago(1m),   // Minute
      OneSecond      = ago(1s),   // Second
      OneMillisecond = ago(1ms),   // Millisecond
      OneMicrosecond = ago(1microsecond),   // Microsecond
      OneTick        = ago(1tick)    // Tick or 100 nano seconds
```
