---
title: "cstdarg.hpp"
---

# Header file `cstdarg.hpp`

``` cpp
#include "etl/version.hpp"

namespace etl
{
}

#define va_start(ap, param)

#define va_end(ap)

#define va_arg(ap, type)

#define va_copy(dest, src)
```

## Macro `va_start`

``` cpp
#define va_start(ap, param) __builtin_va_start(ap, param)
```

The va\_start macro enables access to the variable arguments following the named argument parm\_n. va\_start should be invoked with an instance to a valid va\_list object ap before any calls to va\_arg. If the parm\_n is a pack expansion or an entity resulting from a lambda capture, the program is ill-formed, no diagnostic required. If parm\_n is declared with reference type or with a type not compatible with the type that results from default argument promotions, the behavior is undefined.

*Notes:* [cppreference.com/w/cpp/utility/variadic/va\_start](https://en.cppreference.com/w/cpp/utility/variadic/va_start)

-----

## Macro `va_end`

``` cpp
#define va_end(ap) __builtin_va_end(ap)
```

The va\_end macro performs cleanup for an ap object initialized by a call to va\_start or va\_copy. va\_end may modify ap so that it is no longer usable.

*Notes:* [cppreference.com/w/cpp/utility/variadic/va\_end](https://en.cppreference.com/w/cpp/utility/variadic/va_end)

If there is no corresponding call to va\_start or va\_copy, or if va\_end is not called before a function that calls va\_start or va\_copy returns, the behavior is undefined.

-----

## Macro `va_arg`

``` cpp
#define va_arg(ap, type) __builtin_va_arg(ap, type)
```

The va\_arg macro expands to an expression of type T that corresponds to the next parameter from the va\_list ap. Prior to calling va\_arg, ap must be initialized by a call to either va\_start or va\_copy, with no intervening call to va\_end. Each invocation of the va\_arg macro modifies ap to point to the next variable argument.

*Notes:* [cppreference.com/w/cpp/utility/variadic/va\_arg](https://en.cppreference.com/w/cpp/utility/variadic/va_arg)

-----

## Macro `va_copy`

``` cpp
#define va_copy(dest, src) __builtin_va_copy(dest, src)
```

The va\_copy macro copies src to dest.

*Notes:* [cppreference.com/w/cpp/utility/variadic/va\_copy](https://en.cppreference.com/w/cpp/utility/variadic/va_copy)

va\_end should be called on dest before the function returns or any subsequent re-initialization of dest (via calls to va\_start or va\_copy).

-----
