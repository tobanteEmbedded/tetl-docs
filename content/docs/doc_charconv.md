---
title: "charconv.hpp"
---

# Header file `charconv.hpp`

``` cpp
#include "etl/version.hpp"
#include "etl/cstdint.hpp"
#include "etl/system_error.hpp"

namespace etl
{
    enum class chars_format
    : etl::uint8_t;

    struct to_chars_result;

    struct from_chars_result;
}
```

### Enumeration `etl::chars_format` \[Strings\]

``` cpp
enum class chars_format
: etl::uint8_t
{
    scientific = 0x1,
    fixed = 0x2,
    hex = 0x4,
    general = fixed | scientific
};
```

A BitmaskType used to specify floating-point formatting for to\_chars and from\_chars.

-----

### Struct `etl::to_chars_result` \[Strings\]

``` cpp
struct to_chars_result
{
};
```

Primitive numerical output conversion.

-----

### Struct `etl::from_chars_result` \[Strings\]

``` cpp
struct from_chars_result
{
};
```

Primitive numerical input conversion

-----
