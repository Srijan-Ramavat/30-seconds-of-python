---
title: required_keys
tags: utility,intermediate
---

Required keys are available in the object or not.

- param d: The dict to check
- param keys: The keys to check :attr:`obj` for. This can either be a single string, or an iterable of strings
- param allow_none: Whether ``None`` values are allowed

```py
def required_keys(d: dict, keys: list or str, allow_none=True):
    if is_str_type(keys):
        keys = [keys]
    for k in keys:
        if k not in d:
            raise ValueError("'{}' must be set".format(k))
        if not allow_none and d[k] is None:
            raise ValueError("'{}' cannot be None".format(k))
    return True
```

```py
obj = {
  "key1":"value",
  "key2":None
}
# example 1
keys = ['key1','key2']
result = required_keys(obj, keys) # result -> True

#example 2
keys = 'key1'
result = required_keys(obj, keys) # result -> True

#example 3
keys = 'key3'
result = required_keys(obj, keys) # result -> Function raises ValueError

#exmaple 4
keys = ['key1','key2']
result = required_keys(obj, keys, allow_none=False) # result -> Function raises ValueError

```
