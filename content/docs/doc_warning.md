---
title: "warning.hpp"
---

# Header file `warning.hpp`

``` cpp
namespace etl
{
    template <typename ... Types>
    constexpr void ignore_unused(Types &&...);
}
```

### Function `etl::ignore_unused`

``` cpp
template <typename ... Types>
constexpr void ignore_unused(Types &&...);
```

Explicitly ignore arguments or variables.

-----
