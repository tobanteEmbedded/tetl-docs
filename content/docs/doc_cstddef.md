---
title: "cstddef.hpp"
---

# Header file `cstddef.hpp`

``` cpp
#include "etl/version.hpp"
#include "etl/type_traits.hpp"

namespace etl
{
    enum class byte
    : unsigned char;

    template <typename Int>
    constexpr enable_if_t<is_integral_v<Int>, Int> to_integer(etl::byte b) noexcept;

    template <typename Int>
    constexpr enable_if_t<is_integral_v<Int>, etl::byte> operator<<(etl::byte b, Int shift) noexcept;

    template <typename Int>
    constexpr enable_if_t<is_integral_v<Int>, etl::byte> operator>>(etl::byte b, Int shift) noexcept;

    template <typename Int>
    constexpr enable_if_t<is_integral_v<Int>, etl::byte &> operator<<=(etl::byte& b, Int shift) noexcept;

    template <typename Int>
    constexpr enable_if_t<is_integral_v<Int>, etl::byte &> operator>>=(etl::byte& b, Int shift) noexcept;

    constexpr etl::byte operator|(etl::byte l, etl::byte r) noexcept;

    constexpr etl::byte operator&(etl::byte l, etl::byte r) noexcept;

    constexpr etl::byte operator^(etl::byte l, etl::byte r) noexcept;

    constexpr etl::byte operator~(etl::byte b) noexcept;

    constexpr etl::byte& operator|=(etl::byte& l, etl::byte r) noexcept;

    constexpr etl::byte& operator&=(etl::byte& l, etl::byte r) noexcept;

    constexpr etl::byte& operator^=(etl::byte& l, etl::byte r) noexcept;
}
```

### Enumeration `etl::byte`

``` cpp
enum class byte
: unsigned char
{
};
```

etl::byte is a distinct type that implements the concept of byte as specified in the C++ language definition.

Like char and unsigned char, it can be used to access raw memory occupied by other objects, but unlike those types, it is not a character type and is not an arithmetic type. A byte is only a collection of bits, and the only operators defined for it are the bitwise ones. \\notes [cppreference.com/w/cpp/types/byte](https://en.cppreference.com/w/cpp/types/byte)

-----

### Function `etl::to_integer`

``` cpp
template <typename Int>
constexpr enable_if_t<is_integral_v<Int>, Int> to_integer(etl::byte b) noexcept;
```

Equivalent to: `return Int(b);`

*Requires:* etl::is\_integral\_v\<Int\>

-----

### Function `etl::operator<<`

``` cpp
template <typename Int>
constexpr enable_if_t<is_integral_v<Int>, etl::byte> operator<<(etl::byte b, Int shift) noexcept;
```

Equivalent to: `return etl::byte(static_cast<unsigned int>(b) <<` shift)

*Requires:* etl::is\_integral\_v\<Int\>

-----

### Function `etl::operator>>`

``` cpp
template <typename Int>
constexpr enable_if_t<is_integral_v<Int>, etl::byte> operator>>(etl::byte b, Int shift) noexcept;
```

Equivalent to: `return etl::byte(static_cast<unsigned int>(b) >>` shift)

*Requires:* etl::is\_integral\_v\<Int\>

-----

### Function `etl::operator<<=`

``` cpp
template <typename Int>
constexpr enable_if_t<is_integral_v<Int>, etl::byte &> operator<<=(etl::byte& b, Int shift) noexcept;
```

Equivalent to: `return b = b << shift;`

*Requires:* etl::is\_integral\_v\<Int\>

-----

### Function `etl::operator>>=`

``` cpp
template <typename Int>
constexpr enable_if_t<is_integral_v<Int>, etl::byte &> operator>>=(etl::byte& b, Int shift) noexcept;
```

Equivalent to: `return b = b >> shift;`

*Requires:* etl::is\_integral\_v\<Int\>

-----

### Function `etl::operator|`

``` cpp
constexpr etl::byte operator|(etl::byte l, etl::byte r) noexcept;
```

Equivalent to: `return byte(static_cast<unsigned int>(l) | static_cast<unsigned int>(r));`

-----

### Function `etl::operator&`

``` cpp
constexpr etl::byte operator&(etl::byte l, etl::byte r) noexcept;
```

Equivalent to: `return byte(static_cast<unsigned int>(l) & static_cast<unsigned int>(r));`

-----

### Function `etl::operator^`

``` cpp
constexpr etl::byte operator^(etl::byte l, etl::byte r) noexcept;
```

Equivalent to: `return byte(static_cast<unsigned int>(l) ^ static_cast<unsigned int>(r));`

-----

### Function `etl::operator~`

``` cpp
constexpr etl::byte operator~(etl::byte b) noexcept;
```

Equivalent to: `return byte(~static_cast<unsigned int>(b));`

-----

### Function `etl::operator|=`

``` cpp
constexpr etl::byte& operator|=(etl::byte& l, etl::byte r) noexcept;
```

Equivalent to: `return l = l | r;`

-----

### Function `etl::operator&=`

``` cpp
constexpr etl::byte& operator&=(etl::byte& l, etl::byte r) noexcept;
```

Equivalent to: `return l = l & r;`

-----

### Function `etl::operator^=`

``` cpp
constexpr etl::byte& operator^=(etl::byte& l, etl::byte r) noexcept;
```

Equivalent to: `return l = l ^ r;`

-----
