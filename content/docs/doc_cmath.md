---
title: "cmath.hpp"
---

# Header file `cmath.hpp`

``` cpp
#include "etl/version.hpp"
#include "etl/type_traits.hpp"

namespace etl
{
    using float_t = float;
    using double_t = double;

    //=== isinf ===//
    constexpr bool isinf(float arg);
    constexpr bool isinf(double arg);
    constexpr bool isinf(long double arg);
    template <typename IntegralType>
    constexpr enable_if_t<is_integral_v<IntegralType>, bool> isinf(IntegralType arg);

    //=== isnan ===//
    constexpr bool isnan(float arg);
    constexpr bool isnan(double arg);
    constexpr bool isnan(long double arg);

    template <typename IntegralType>
    constexpr enable_if_t<is_integral_v<IntegralType>, bool> isnan(IntegralType arg);

    //=== isfinite ===//
    constexpr bool isfinite(float arg);
    constexpr bool isfinite(double arg);
    constexpr bool isfinite(long double arg);

    //=== lerp ===//
    constexpr float lerp(float a, float b, float t) noexcept;
    constexpr double lerp(double a, double b, double t) noexcept;
    constexpr long double lerp(long double a, long double b, long double t) noexcept;

    //=== abs ===//
    constexpr int abs(int n) noexcept;
    constexpr long abs(long n) noexcept;
    constexpr long long abs(long long n) noexcept;
}
```

### Type alias `etl::float_t`

``` cpp
using float_t = float;
```

Most efficient floating-point type at least as wide as float.

-----

### Type alias `etl::double_t`

``` cpp
using double_t = double;
```

Most efficient floating-point type at least as wide as double.

-----

### Function `etl::isinf` \[Numeric\]

``` cpp
(1) constexpr bool isinf(float arg);

(2) constexpr bool isinf(double arg);

(3) constexpr bool isinf(long double arg);

(4) template <typename IntegralType>
constexpr enable_if_t<is_integral_v<IntegralType>, bool> isinf(IntegralType arg);
```

Determines if the given floating point number arg is a positive or negative infinity.

*Return values:* true if arg is infinite, false otherwise

*Notes:* [cppreference.com/w/cpp/numeric/math/isinf](https://en.cppreference.com/w/cpp/numeric/math/isinf)

-----

### Function `etl::isnan` \[Numeric\]

``` cpp
(1) constexpr bool isnan(float arg);

(2) constexpr bool isnan(double arg);

(3) constexpr bool isnan(long double arg);
```

Determines if the given floating point number arg is a not-a-number (NaN) value.

*Notes:* [cppreference.com/w/cpp/numeric/math/isnan](https://en.cppreference.com/w/cpp/numeric/math/isnan)

-----

### Function `etl::isnan`

``` cpp
template <typename IntegralType>
constexpr enable_if_t<is_integral_v<IntegralType>, bool> isnan(IntegralType arg);
```

Determines if the given floating point number arg is a not-a-number (NaN) value.

*Notes:* [cppreference.com/w/cpp/numeric/math/isnan](https://en.cppreference.com/w/cpp/numeric/math/isnan)

-----

### Function `etl::isfinite` \[Numeric\]

``` cpp
(1) constexpr bool isfinite(float arg);

(2) constexpr bool isfinite(double arg);

(3) constexpr bool isfinite(long double arg);
```

Determines if the given floating point number arg has finite value i.e. it is normal, subnormal or zero, but not infinite or NaN.

*Notes:* [cppreference.com/w/cpp/numeric/math/isfinite](https://en.cppreference.com/w/cpp/numeric/math/isfinite)

-----

### Function `etl::lerp` \[Numeric\]

``` cpp
(1) constexpr float lerp(float a, float b, float t) noexcept;

(2) constexpr double lerp(double a, double b, double t) noexcept;

(3) constexpr long double lerp(long double a, long double b, long double t) noexcept;
```

Computes a+t(b−a), i.e. the linear interpolation between a and b for the parameter t (or extrapolation, when t is outside the range \[0,1\]).

*Notes:* [cppreference.com/w/cpp/numeric/lerp](https://en.cppreference.com/w/cpp/numeric/lerp)

-----

### Function `etl::abs` \[Numeric\]

``` cpp
(1) constexpr int abs(int n) noexcept;

(2) constexpr long abs(long n) noexcept;

(3) constexpr long long abs(long long n) noexcept;
```

Computes the absolute value of an integer number. The behavior is undefined if the result cannot be represented by the return type. If abs is called with an unsigned integral argument that cannot be converted to int by integral promotion, the program is ill-formed.

-----
