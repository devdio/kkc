# Util Function

## remap  
```python
def remap(value, source_range, target_range):
    """Remap a value from the source range to the target range.

    Examples ::

         >>> remap(50, (0, 100), (0, 10))
         5.0

         >>> remap(5, (0, 10), (0, 100))
         50.0

         >>> remap(5, (0, 10), (10, 20))
         15.0

         >>> remap(15, (10, 20), (0, 10))
         5.0

    :param value: The value to be remapped.

    :param source_range: The source range for :code:`value`
    :type source_range: tuple

    :param target_range: The target range for :code:`value`
    :type target_range: tuple

    """
    s0, s1 = source_range
    t0, t1 = target_range
    S = s1 - s0
    T = t1 - t0
    return t0 + ((value - s0) / S) * T

```

