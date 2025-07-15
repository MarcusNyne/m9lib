# uStringFormat

uStringFormat contains static methods for string formatting.

## Bytes
Displays bytes as a string, converting bytes to the largest possible denomination, unless a denomination is specified.

**uStringFormat.Bytes(*Bytes*,*ByteUnits*=None)**
- Supported units: 'tb', 'gb', 'mb', 'kb', 'b'
- When *ByteUnits* is None, units are calculated automatically
  
```python
# automatically select a denomination
bytes_string = uStringFormat.Bytes(1234567)

# format in gigabytes
bytes_string = uStringFormat.Bytes(1234567, "gb")
```

## Parse Bytes
Parse a text string expressing bytes in denominations into a number of bytes.  Supports kb, mb, gb, and tb.

**uStringFormat.ParseBytes(*String*)**
- Returns number of bytes as a integer

```python
# interprets denomination
b1 = uStringFormat.ParseBytes("1.5 kb")
b2 = uStringFormat.ParseBytes("4GB")
b3 = uStringFormat.ParseBytes("10020")
```

## Duration
Displays a duration, converting seconds to the largest possible unit of time, unless a unit is specified.

**uStringFormat.Duration(*Seconds*,*SecUnits*=None)**
- *Seconds* is a float value
- Supported units of time: 'h', 'm', 's'
- When *SecUnits* is *None*, units are calculated automatically
  
```python
# automatically select a denomination
duration_string = uStringFormat.Duration(321)

# format in minutes
duration_string = uStringFormat.Duration(321, "m")
```

## Parse Duration
Parse a text string expressing bytes in denominations into a number of bytes.  Supports kb, mb, gb, and tb.

**uStringFormat.ParseDuration(*String*)**
- Returns duration in milliseconds as an integer

```python
# interprets denomination
d1 = uStringFormat.ParseDuration("12 h")
d2 = uStringFormat.ParseDuration("20seconds")
d3 = uStringFormat.ParseDuration("10020")
```

## String

Converts a string, using substitution.  When using bytes or duration substitution, value must be passed to the method.

**uStringFormat.String(*String*,*Bytes*,*ByteUnits*,*Seconds*,*SecUnits*,*Now*)**
- Performs replacements and returns a string

Supported placeholders:
| Placeholder | Meaning | Parameters |
| :--- | :--- | :--- |
| {YMD} | year, month, day | *Now* (optional) |
| {LTS} | log timestamp | *Now* (optional) |
| {TSM} | seconds since midnight | *Now* (optional) |
| {B} | bytes | *Bytes*, *ByteUnits* (optional) |
| {D} | duration | *Seconds*, *SecUnits* (optional) |
| {PYF} | environment PYFOLDER |  |

## Strip
Strips white spaces from the begining and end of a string.

**uStringFormat.Strip(*Value*)**
- Value can be a string, or a list of strings
