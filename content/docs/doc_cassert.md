---
title: "cassert.hpp"
---

# Header file `cassert.hpp`

``` cpp
#include "etl/version.hpp"
#include "etl/warning.hpp"

namespace etl
{
    struct assert_msg;
}

namespace etl
{
    void tetl_default_assert_handler(etl::assert_msg const& msg);
}

#define TETL_TO_STR_IMPL(s)

#define TETL_TO_STR(s)

#define TETL_ASSERT(exp)
```

### Struct `etl::assert_msg`

``` cpp
struct assert_msg
{
};
```

Payload for an assertion.

-----

### Function `etl::tetl_default_assert_handler`

``` cpp
void tetl_default_assert_handler(etl::assert_msg const& msg);
```

The default assert handler. This will be called, if an assertion is triggered at runtime.

-----

## Macro `TETL_ASSERT`

``` cpp
#define TETL_ASSERT(exp) do { if (!(exp)) { auto const msg = ::etl::assert_msg { __LINE__, __FILE__, nullptr, /*The function name causes code bloat.  */ nullptr, /*The stringified expression causes code bloat.  */ }; ::etl::detail::tetl_call_assert_handler(msg); } } while (false)
```

Assertion macro with customizable runtime behavior

-----
