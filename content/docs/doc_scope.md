---
title: "scope.hpp"
---

# Header file `scope.hpp`

``` cpp
#include "etl/version.hpp"
#include "etl/cstddef.hpp"
#include "etl/type_traits.hpp"
#include "etl/utility.hpp"

namespace etl
{
    template <typename FuncT>
    struct scope_exit;
}
```

### Struct `etl::scope_exit`

``` cpp
template <typename FuncT>
struct scope_exit
{
};
```

The class template `scope_exit` is a general-purpose scope guard intended to call its exit function when a scope is exited. \\details A `scope_exit` may be either active, i.e. calls its exit function on destruction, or inactive, i.e. does nothing on destruction. A `scope_exit` is active after constructed from an exit function. A `scope_exit` can become inactive by calling `release()` on it either manually or automatically (by the move constructor). An inactive `scope_exit` may also be obtained by initializing with another inactive `scope_exit`. Once a `scope_exit` is inactive, it cannot become active again.

-----
