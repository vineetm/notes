In Python3, sequence of characters is represented by either `bytes` or `str`

* `bytes`: raw 8-bit values
* `str`: Unicode chars

String instances **do not have** an assosciated binary encoding.

* To convert `unicode` to `binary` -> `encode`
* To convert `binary` to `unicode` -> `decode`

The core of program should work with `str`. i.e. `bytes` should be converted to `str`

Convert your data to string
```python
def to_str(bytes_or_str):
    if is_instance(bytes_or_str, bytes):
        value = bytes_or_str.decode('utf-8')
    else:
        value = bytes_or_str
    return value
 ```
 
 ```python
def to_bytes(bytes_or_str):
    if is_instance(bytes_or_str, str):
        value = bytes_or_str.encode('utf-8')
    else:
        value = bytes_or_str
    return value
 ```

* In Python3, `bytes` or `str` are never equivalent. Not even empty string
