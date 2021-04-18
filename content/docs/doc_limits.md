---
title: "limits.hpp"
---

# Header file `limits.hpp`

``` cpp
#include "etl/version.hpp"
#include "etl/cfloat.hpp"
#include "etl/climits.hpp"
#include "etl/cmath.hpp"
#include "etl/cstdint.hpp"

namespace etl
{
    enum float_round_style;

    enum float_denorm_style;

    template <typename T>
    class numeric_limits;

    template <>
    class numeric_limits<bool>;

    template <>
    class numeric_limits<char>;

    template <>
    class numeric_limits<signed char>;

    template <>
    class numeric_limits<unsigned char>;

    template <>
    class numeric_limits<short>;

    template <>
    class numeric_limits<unsigned short>;

    template <>
    class numeric_limits<int>;

    template <>
    class numeric_limits<unsigned int>;

    template <>
    class numeric_limits<long>;

    template <>
    class numeric_limits<unsigned long>;

    template <>
    class numeric_limits<long long>;

    template <>
    class numeric_limits<unsigned long long>;

    template <>
    class numeric_limits<float>;

    template <>
    class numeric_limits<double>;
}
```
