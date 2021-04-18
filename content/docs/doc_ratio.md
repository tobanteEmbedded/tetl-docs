---
title: "ratio.hpp"
---

# Header file `ratio.hpp`

``` cpp
#include "etl/version.hpp"
#include "etl/cstddef.hpp"
#include "etl/numeric.hpp"
#include "etl/type_traits.hpp"

namespace etl
{
    template <etl::intmax_t Num, etl::intmax_t Denom = 1>
    struct ratio;

    template <typename R1, typename R2>
    using ratio_add = ratio<R1::num * R2::den + R2::num * R1::den, R1::den * R2::den>;

    template <typename R1, typename R2>
    using ratio_subtract = ratio<R1::num * R2::den - R2::num * R1::den, R1::den * R2::den>;

    template <typename R1, typename R2>
    using ratio_multiply = ratio<R1::num * R2::num, R1::den * R2::den>;

    template <typename R1, typename R2>
    using ratio_divide = ratio<R1::num * R2::den, R1::den * R2::num>;

    template <typename R1, typename R2>
    struct ratio_equal;

    template <typename R1, typename R2>inline constexpr bool ratio_equal_v = ratio_equal<R1, R2>::value;

    template <typename R1, typename R2>
    struct ratio_not_equal;

    template <typename R1, typename R2>inline constexpr bool ratio_not_equal_v = ratio_not_equal<R1, R2>::value;

    template <typename R1, typename R2>
    struct ratio_less;

    template <typename R1, typename R2>inline constexpr bool ratio_less_v = ratio_less<R1, R2>::value;

    template <typename R1, typename R2>
    struct ratio_less_equal;

    template <typename R1, typename R2>inline constexpr bool ratio_less_equal_v = ratio_less_equal<R1, R2>::value;

    template <typename R1, typename R2>
    struct ratio_greater;

    template <typename R1, typename R2>inline constexpr bool ratio_greater_v = ratio_greater<R1, R2>::value;

    template <typename R1, typename R2>
    struct ratio_greater_equal;

    template <typename R1, typename R2>inline constexpr bool ratio_greater_equal_v = ratio_greater_equal<R1, R2>::value;
}
```

### Struct `etl::ratio`

``` cpp
template <etl::intmax_t Num, etl::intmax_t Denom = 1>
struct ratio
{
};
```

The typename template provides compile-time rational arithmetic support. Each instantiation of this template exactly represents any finite rational number as long as its numerator Num and denominator Denom are representable as compile-time constants of type intmax\_t.

-----

### Alias template `etl::ratio_add`

``` cpp
template <typename R1, typename R2>
using ratio_add = ratio<R1::num * R2::den + R2::num * R1::den, R1::den * R2::den>;
```

The alias template ratio\_add denotes the result of adding two exact rational fractions represented by the ratio specializations R1 and R2.

The result is a ratio specialization `ratio<U, V>`, such that given `Num == R1::num * R2::den + R2::num * R1::den` and `Denom == R1::den * R2::den` (computed without arithmetic overflow), U is ratio\<Num, Denom\>::num and V is ratio\<Num, Denom\>::den.

\\todo Check overflow.

-----

### Alias template `etl::ratio_subtract`

``` cpp
template <typename R1, typename R2>
using ratio_subtract = ratio<R1::num * R2::den - R2::num * R1::den, R1::den * R2::den>;
```

The alias template ratio\_subtract denotes the result of subtracting two exact rational fractions represented by the ratio specializations R1 and R2.

The result is a ratio specialization `ratio<U, V>`, such that given Num == R1::num \* R2::den - R2::num \* R1::den and Denom == R1::den \* R2::den (computed without arithmetic overflow), U is ratio\<Num, Denom\>::num and V is ratio\<Num, Denom\>::den.

\\todo Check overflow.

-----

### Alias template `etl::ratio_multiply`

``` cpp
template <typename R1, typename R2>
using ratio_multiply = ratio<R1::num * R2::num, R1::den * R2::den>;
```

The alias template ratio\_multiply denotes the result of multiplying two exact rational fractions represented by the ratio specializations R1 and R2.

The result is a ratio specialization `ratio<U, V>`, such that given Num == R1::num \* R2::num and Denom == R1::den \* R2::den (computed without arithmetic overflow), U is ratio\<Num, Denom\>::num and V is ratio\<Num, Denom\>::den.

\\todo Check overflow.

-----

### Alias template `etl::ratio_divide`

``` cpp
template <typename R1, typename R2>
using ratio_divide = ratio<R1::num * R2::den, R1::den * R2::num>;
```

The alias template ratio\_divide denotes the result of dividing two exact rational fractions represented by the ratio specializations R1 and R2.

The result is a ratio specialization `ratio<U, V>`, such that given Num == R1::num \* R2::den and Denom == R1::den \* R2::num (computed without arithmetic overflow), U is ratio\<Num, Denom\>::num and V is ratio\<Num, Denom\>::den.

\\todo Check overflow.

-----

### Struct `etl::ratio_equal`

``` cpp
template <typename R1, typename R2>
struct ratio_equal
: bool_constant<R1::num==R2::num&&R1::den==R2::den>
{
};
```

Compares two ratio objects for equality at compile-time. If the ratios R1 and R2 are equal, provides the member constant value equal true. Otherwise, value is false.

-----

### Struct `etl::ratio_not_equal`

``` cpp
template <typename R1, typename R2>
struct ratio_not_equal
: bool_constant<!ratio_equal_v<R1,R2>>
{
};
```

Compares two ratio objects for equality at compile-time. If the ratios R1 and R2 are not equal, provides the member constant value equal true. Otherwise, value is false.

-----

### Struct `etl::ratio_less`

``` cpp
template <typename R1, typename R2>
struct ratio_less
: bool_constant<(R1::num*R2::den<R2::num*R1::den)>
{
};
```

Compares two ratio objects for equality at compile-time. If the ratio R1 is less than the ratio R2, provides the member constant value equal true. Otherwise, value is false.

-----

### Struct `etl::ratio_less_equal`

``` cpp
template <typename R1, typename R2>
struct ratio_less_equal
: bool_constant<(R1::num*R2::den<=R2::num*R1::den)>
{
};
```

Compares two ratio objects for equality at compile-time. If the ratio R1 is less than or equal to the ratio R2, provides the member constant value equal true. Otherwise, value is false.

-----

### Struct `etl::ratio_greater`

``` cpp
template <typename R1, typename R2>
struct ratio_greater
: bool_constant<(R1::num*R2::den>R2::num*R1::den)>
{
};
```

Compares two ratio objects for equality at compile-time. If the ratio R1 is greater than the ratio R2, provides the member constant value equal true. Otherwise, value is false.

-----

### Struct `etl::ratio_greater_equal`

``` cpp
template <typename R1, typename R2>
struct ratio_greater_equal
: bool_constant<(R1::num*R2::den>=R2::num*R1::den)>
{
};
```

Compares two ratio objects for equality at compile-time. If the ratio R1 is greater than or equal to the ratio R2, provides the member constant value equal true. Otherwise, value is false.

-----
