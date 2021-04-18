---
title: "new.hpp"
---

# Header file `new.hpp`

``` cpp
#include "etl/version.hpp"

namespace etl
{
    struct nothrow_t;

    constexpr auto const nothrow = etl::nothrow_t{};
    using new_handler = void(*)();

    constexpr auto const hardware_constructive_interference_size = 64;

    constexpr auto const hardware_destructive_interference_size = 64;

    enum class align_val_t
    : size_t;

    struct destroying_delete_t;

    constexpr auto const destroying_delete = destroying_delete_t{};
}

#define TETL_CACHELINE_SIZE
```

### Struct `etl::nothrow_t`

``` cpp
struct nothrow_t
{
};
```

etl::nothrow\_t is an empty class type used to disambiguate the overloads of throwing and non-throwing allocation functions.

-----

### Variable `etl::nothrow`

``` cpp
constexpr auto const nothrow = etl::nothrow_t{};
```

etl::nothrow is a constant of type etl::nothrow\_t used to disambiguate the overloads of throwing and non-throwing allocation functions.

-----

### Type alias `etl::new_handler`

``` cpp
using new_handler = void(*)();
```

etl::new\_handler is the function pointer type (pointer to function that takes no arguments and returns void), which is used by the functions etl::set\_new\_handler and etl::get\_new\_handler

-----

### Variable `etl::hardware_constructive_interference_size`

``` cpp
constexpr auto const hardware_constructive_interference_size = 64;
```

Minimum offset between two objects to avoid false sharing. Guaranteed to be at least alignof(max\_align\_t).

-----

### Variable `etl::hardware_destructive_interference_size`

``` cpp
constexpr auto const hardware_destructive_interference_size = 64;
```

Maximum size of contiguous memory to promote true sharing. Guaranteed to be at least alignof(max\_align\_t).

-----

### Enumeration `etl::align_val_t`

``` cpp
enum class align_val_t
: size_t
{
};
```

Both new-expression and delete-expression, when used with objects whose alignment requirement is greater than the default, pass that alignment requirement as an argument of type align\_val\_t to the selected allocation/deallocation function.

-----

### Struct `etl::destroying_delete_t`

``` cpp
struct destroying_delete_t
{
};
```

Tag type used to identify the destroying delete form of operator delete.

-----

### Variable `etl::destroying_delete`

``` cpp
constexpr auto const destroying_delete = destroying_delete_t{};
```

Tag type used to identify the destroying delete form of operator delete.

-----
