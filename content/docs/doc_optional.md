---
title: "optional.hpp"
---

# Header file `optional.hpp`

``` cpp
#include "etl/version.hpp"
#include "etl/memory.hpp"
#include "etl/new.hpp"
#include "etl/type_traits.hpp"
#include "etl/utility.hpp"

namespace etl
{
    struct nullopt_t;

    constexpr auto const nullopt = etl::nullopt_t{{}};

    template <typename ValueType>
    class optional;

    template <typename T, typename U>
    constexpr bool operator==(optional<T> const& lhs, optional<U> const& rhs);

    template <typename T, typename U>
    constexpr bool operator!=(optional<T> const& lhs, optional<U> const& rhs);

    template <typename T, typename U>
    constexpr bool operator<(optional<T> const& lhs, optional<U> const& rhs);

    template <typename T, typename U>
    constexpr bool operator>(optional<T> const& lhs, optional<U> const& rhs);

    template <typename T, typename U>
    constexpr bool operator<=(optional<T> const& lhs, optional<U> const& rhs);

    template <typename T, typename U>
    constexpr bool operator>=(optional<T> const& lhs, optional<U> const& rhs);

    template <typename T>
    constexpr bool operator==(optional<T> const& opt, etl::nullopt_t) noexcept;

    template <typename T>
    constexpr bool operator==(etl::nullopt_t, optional<T> const& opt) noexcept;

    template <typename T>
    constexpr bool operator!=(optional<T> const& opt, etl::nullopt_t) noexcept;

    template <typename T>
    constexpr bool operator!=(etl::nullopt_t, optional<T> const& opt) noexcept;

    template <typename T>
    constexpr bool operator<(optional<T> const&, etl::nullopt_t) noexcept;

    template <typename T>
    constexpr bool operator<(etl::nullopt_t, optional<T> const& opt) noexcept;

    template <typename T>
    constexpr bool operator<=(optional<T> const& opt, etl::nullopt_t) noexcept;

    template <typename T>
    constexpr bool operator<=(etl::nullopt_t, optional<T> const&) noexcept;

    template <typename T>
    constexpr bool operator>(optional<T> const& opt, etl::nullopt_t) noexcept;

    template <typename T>
    constexpr bool operator>(etl::nullopt_t, optional<T> const&) noexcept;

    template <typename T>
    constexpr bool operator>=(optional<T> const&, etl::nullopt_t) noexcept;

    template <typename T>
    constexpr bool operator>=(etl::nullopt_t, optional<T> const& opt) noexcept;

    template <typename ValueType>
    constexpr etl::optional<etl::decay_t<ValueType>> make_optional(ValueType&& value);

    template <typename ValueType, typename ... Args>
    constexpr etl::optional<ValueType> make_optional(Args &&... args);
}
```

### Struct `etl::nullopt_t`

``` cpp
struct nullopt_t
{
};
```

etl::nullopt\_t is an empty class type used to indicate optional type with uninitialized state. In particular, etl::optional has a constructor with nullopt\_t as a single argument, which creates an optional that does not contain a value.

-----

### Variable `etl::nullopt`

``` cpp
constexpr auto const nullopt = etl::nullopt_t{{}};
```

etl::nullopt is a constant of type etl::nullopt\_t that is used to indicate optional type with uninitialized state.

-----

### Function `etl::operator==`

``` cpp
template <typename T, typename U>
constexpr bool operator==(optional<T> const& lhs, optional<U> const& rhs);
```

Compares two optional objects, lhs and rhs.

-----

### Function `etl::operator!=`

``` cpp
template <typename T, typename U>
constexpr bool operator!=(optional<T> const& lhs, optional<U> const& rhs);
```

Compares two optional objects, lhs and rhs.

-----

### Function `etl::operator<`

``` cpp
template <typename T, typename U>
constexpr bool operator<(optional<T> const& lhs, optional<U> const& rhs);
```

Compares two optional objects, lhs and rhs.

-----

### Function `etl::operator>`

``` cpp
template <typename T, typename U>
constexpr bool operator>(optional<T> const& lhs, optional<U> const& rhs);
```

Compares two optional objects, lhs and rhs.

-----

### Function `etl::operator<=`

``` cpp
template <typename T, typename U>
constexpr bool operator<=(optional<T> const& lhs, optional<U> const& rhs);
```

Compares two optional objects, lhs and rhs.

-----

### Function `etl::operator>=`

``` cpp
template <typename T, typename U>
constexpr bool operator>=(optional<T> const& lhs, optional<U> const& rhs);
```

Compares two optional objects, lhs and rhs.

-----

### Function `etl::operator==`

``` cpp
template <typename T>
constexpr bool operator==(optional<T> const& opt, etl::nullopt_t) noexcept;
```

Compares opt with a nullopt. Equivalent to when comparing to an optional that does not contain a value.

-----

### Function `etl::operator==`

``` cpp
template <typename T>
constexpr bool operator==(etl::nullopt_t, optional<T> const& opt) noexcept;
```

Compares opt with a nullopt. Equivalent to when comparing to an optional that does not contain a value.

-----

### Function `etl::operator!=`

``` cpp
template <typename T>
constexpr bool operator!=(optional<T> const& opt, etl::nullopt_t) noexcept;
```

Compares opt with a nullopt. Equivalent to when comparing to an optional that does not contain a value.

-----

### Function `etl::operator!=`

``` cpp
template <typename T>
constexpr bool operator!=(etl::nullopt_t, optional<T> const& opt) noexcept;
```

Compares opt with a nullopt. Equivalent to when comparing to an optional that does not contain a value.

-----

### Function `etl::operator<`

``` cpp
template <typename T>
constexpr bool operator<(optional<T> const&, etl::nullopt_t) noexcept;
```

Compares opt with a nullopt. Equivalent to when comparing to an optional that does not contain a value.

-----

### Function `etl::operator<`

``` cpp
template <typename T>
constexpr bool operator<(etl::nullopt_t, optional<T> const& opt) noexcept;
```

Compares opt with a nullopt. Equivalent to when comparing to an optional that does not contain a value.

-----

### Function `etl::operator<=`

``` cpp
template <typename T>
constexpr bool operator<=(optional<T> const& opt, etl::nullopt_t) noexcept;
```

Compares opt with a nullopt. Equivalent to when comparing to an optional that does not contain a value.

-----

### Function `etl::operator<=`

``` cpp
template <typename T>
constexpr bool operator<=(etl::nullopt_t, optional<T> const&) noexcept;
```

Compares opt with a nullopt. Equivalent to when comparing to an optional that does not contain a value.

-----

### Function `etl::operator>`

``` cpp
template <typename T>
constexpr bool operator>(optional<T> const& opt, etl::nullopt_t) noexcept;
```

Compares opt with a nullopt. Equivalent to when comparing to an optional that does not contain a value.

-----

### Function `etl::operator>`

``` cpp
template <typename T>
constexpr bool operator>(etl::nullopt_t, optional<T> const&) noexcept;
```

Compares opt with a nullopt. Equivalent to when comparing to an optional that does not contain a value.

-----

### Function `etl::operator>=`

``` cpp
template <typename T>
constexpr bool operator>=(optional<T> const&, etl::nullopt_t) noexcept;
```

Compares opt with a nullopt. Equivalent to when comparing to an optional that does not contain a value.

-----

### Function `etl::operator>=`

``` cpp
template <typename T>
constexpr bool operator>=(etl::nullopt_t, optional<T> const& opt) noexcept;
```

Compares opt with a nullopt. Equivalent to when comparing to an optional that does not contain a value.

-----

### Function `etl::make_optional`

``` cpp
template <typename ValueType>
constexpr etl::optional<etl::decay_t<ValueType>> make_optional(ValueType&& value);
```

Creates an optional object from value.

-----

### Function `etl::make_optional`

``` cpp
template <typename ValueType, typename ... Args>
constexpr etl::optional<ValueType> make_optional(Args &&... args);
```

Creates an optional object constructed in-place from args…

-----
