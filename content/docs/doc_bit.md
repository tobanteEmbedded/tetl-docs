---
title: "bit.hpp"
---

# Header file `bit.hpp`

``` cpp
#include "etl/version.hpp"
#include "etl/cstring.hpp"
#include "etl/limits.hpp"
#include "etl/type_traits.hpp"

namespace etl
{
    enum class endian;

    template <typename To, typename From>
    constexpr enable_if_t<(sizeof(To) == sizeof(From)) && is_trivially_copyable_v<From> && is_trivially_copyable_v<To>, To> bit_cast(From const& src) noexcept;

    template <typename T>
    constexpr enable_if_t<detail::bit_unsigned_int_v<T>, T> rotl(T t, int s) noexcept;

    template <typename T>
    constexpr enable_if_t<detail::bit_unsigned_int_v<T>, T> rotr(T t, int s) noexcept;

    template <typename T>
    constexpr enable_if_t<detail::bit_unsigned_int_v<T>, int> popcount(T input) noexcept;

    template <typename T>
    constexpr enable_if_t<detail::bit_unsigned_int_v<T>, bool> has_single_bit(T x) noexcept;

    template <typename T>
    constexpr enable_if_t<detail::bit_unsigned_int_v<T>, int> countl_zero(T x) noexcept;

    template <typename T>
    constexpr enable_if_t<detail::bit_unsigned_int_v<T>, int> countl_one(T x) noexcept;

    template <typename T>
    constexpr enable_if_t<detail::bit_unsigned_int_v<T>, int> bit_width(T x) noexcept;

    template <typename T>
    constexpr enable_if_t<detail::bit_unsigned_int_v<T>, T> bit_ceil(T x) noexcept;

    template <typename T>
    constexpr enable_if_t<detail::bit_unsigned_int_v<T>, T> bit_floor(T x) noexcept;
}
```

### Enumeration `etl::endian` \[Numeric\]

``` cpp
enum class endian
{
    little = 1234,
    big = 4321,
    native = 1234
};
```

Indicates the endianness of all scalar types. If all scalar types are little-endian, `endian::native` equals `endian::little`. If all scalar types are big-endian, `endian::native` equals `endian::big`.

*Notes:* [cppreference.com/w/cpp/types/endian](https://en.cppreference.com/w/cpp/types/endian)

-----

### Function `etl::bit_cast` \[Numeric\]

``` cpp
template <typename To, typename From>
constexpr enable_if_t<(sizeof(To) == sizeof(From)) && is_trivially_copyable_v<From> && is_trivially_copyable_v<To>, To> bit_cast(From const& src) noexcept;
```

Obtain a value of type To by reinterpreting the object representation of from. Every bit in the value representation of the returned To object is equal to the corresponding bit in the object representation of from.

*Notes:* [cppreference.com/w/cpp/numeric/bit\_cast](https://en.cppreference.com/w/cpp/numeric/bit_cast)

The values of padding bits in the returned To object are unspecified. If there is no value of type To corresponding to the value representation produced, the behavior is undefined. If there are multiple such values, which value is produced is unspecified. This overload only participates in overload resolution if sizeof(To) == sizeof(From) and both To and From are TriviallyCopyable types.

-----

### Function `etl::rotl` \[Numeric\]

``` cpp
template <typename T>
constexpr enable_if_t<detail::bit_unsigned_int_v<T>, T> rotl(T t, int s) noexcept;
```

Computes the result of bitwise left-rotating the value of x by s positions. This operation is also known as a left circular shift.

-----

### Function `etl::rotr` \[Numeric\]

``` cpp
template <typename T>
constexpr enable_if_t<detail::bit_unsigned_int_v<T>, T> rotr(T t, int s) noexcept;
```

Computes the result of bitwise right-rotating the value of x by s positions. This operation is also known as a right circular shift.

-----

### Function `etl::popcount` \[Numeric\]

``` cpp
template <typename T>
constexpr enable_if_t<detail::bit_unsigned_int_v<T>, int> popcount(T input) noexcept;
```

Returns the number of 1 bits in the value of x.

This overload only participates in overload resolution if T is an unsigned integer type (that is, unsigned char, unsigned short, unsigned int, unsigned long, unsigned long long, or an extended unsigned integer type).

-----

### Function `etl::has_single_bit` \[Numeric\]

``` cpp
template <typename T>
constexpr enable_if_t<detail::bit_unsigned_int_v<T>, bool> has_single_bit(T x) noexcept;
```

Checks if x is an integral power of two.

*Return values:* true if x is an integral power of two; otherwise false.

This overload only participates in overload resolution if T is an unsigned integer type (that is, unsigned char, unsigned short, unsigned int, unsigned long, unsigned long long, or an extended unsigned integer type).

-----

### Function `etl::countl_zero` \[Numeric\]

``` cpp
template <typename T>
constexpr enable_if_t<detail::bit_unsigned_int_v<T>, int> countl_zero(T x) noexcept;
```

Returns the number of consecutive 0 bits in the value of x, starting from the most significant bit (“left”).

*Return values:* The number of consecutive 0 bits in the value of x, starting from the most significant bit.

This overload only participates in overload resolution if T is an unsigned integer type (that is, unsigned char, unsigned short, unsigned int, unsigned long, unsigned long long, or an extended unsigned integer type).

-----

### Function `etl::countl_one` \[Numeric\]

``` cpp
template <typename T>
constexpr enable_if_t<detail::bit_unsigned_int_v<T>, int> countl_one(T x) noexcept;
```

Returns the number of consecutive 1 (“one”) bits in the value of x, starting from the most significant bit (“left”).

*Return values:* The number of consecutive 1 bits in the value of x, starting from the most significant bit.

This overload only participates in overload resolution if T is an unsigned integer type (that is, unsigned char, unsigned short, unsigned int, unsigned long, unsigned long long, or an extended unsigned integer type).

-----

### Function `etl::bit_width` \[Numeric\]

``` cpp
template <typename T>
constexpr enable_if_t<detail::bit_unsigned_int_v<T>, int> bit_width(T x) noexcept;
```

If x is not zero, calculates the number of bits needed to store the value x, that is, 1+⌊log2(x)⌋. If x is zero, returns zero.

This overload only participates in overload resolution if T is an unsigned integer type (that is, unsigned char, unsigned short, unsigned int, unsigned long, unsigned long long, or an extended unsigned integer type).

-----

### Function `etl::bit_ceil` \[Numeric\]

``` cpp
template <typename T>
constexpr enable_if_t<detail::bit_unsigned_int_v<T>, T> bit_ceil(T x) noexcept;
```

Calculates the smallest integral power of two that is not smaller than x. If that value is not representable in T, the behavior is undefined. Call to this function is permitted in constant evaluation only if the undefined behavior does not occur.

*Return values:* The smallest integral power of two that is not smaller than x.

This overload only participates in overload resolution if T is an unsigned integer type (that is, unsigned char, unsigned short, unsigned int, unsigned long, unsigned long long, or an extended unsigned integer type).

-----

### Function `etl::bit_floor` \[Numeric\]

``` cpp
template <typename T>
constexpr enable_if_t<detail::bit_unsigned_int_v<T>, T> bit_floor(T x) noexcept;
```

If x is not zero, calculates the largest integral power of two that is not greater than x. If x is zero, returns zero.

*Return values:* Zero if x is zero; otherwise, the largest integral power of two that is not greater than x.

This overload only participates in overload resolution if T is an unsigned integer type (that is, unsigned char, unsigned short, unsigned int, unsigned long, unsigned long long, or an extended unsigned integer type).

-----
