---
title: "tuple.hpp"
---

# Header file `tuple.hpp`

``` cpp
#include "etl/version.hpp"

namespace etl
{
    template <typename First, typename ... Rest>
    struct tuple;

    template <typename First>
    struct tuple<First>;
}
```

### Struct `etl::tuple`

``` cpp
template <typename First, typename ... Rest>
struct tuple
: tuple<Rest...>
{
};
```

\\todo Implement index\_sequence & tuple\_size

-----
