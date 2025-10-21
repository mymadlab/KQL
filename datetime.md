---
layout: home
title: Datetime
---

- Creates a datetime object/type

## Print examples

```KQL
print NoTime       = datetime(2022-11-03), // Omitting the time results in assumption of midnight
      12HourAMTime = datetime(2022-11-03 10:42:33.000 AM),
      12HourPMTime = datetime(2022-11-03 10:42:33.000 AM),
      24HourTimeAM = datetime(2022-11-03 10:42:33.000), // Omitting AM/PM assumes 24 hour clock
      24HourTimePM = datetime(2022-11-03 22:42:33.000)  // Omitting AM/PM assumes 24 hour clock
```
