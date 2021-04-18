---
title: "crtp.hpp"
---

# Header file `crtp.hpp`

``` cpp
#include "etl/version.hpp"
#include "etl/cstddef.hpp"

namespace etl
{
    template <typename Type, template <typename> typename CrtpTag>
    struct crtp;
}
```
