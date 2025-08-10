# Now

- Returns current, future, or past datetime
- Can function in place of ago operator

## Examples

```KQL
print current = now(),     // current datetime
      future  = now(+1d),  // 1 day from now
      past    = now(-1d)   // 1 day ago or same as ago(1d)

```
