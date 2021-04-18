---
title: "variant.hpp"
---

# Header file `variant.hpp`

``` cpp
#include "etl/version.hpp"
#include "etl/cstddef.hpp"
#include "etl/new.hpp"
#include "etl/type_traits.hpp"
#include "etl/utility.hpp"
#include "etl/warning.hpp"

namespace etl
{
    struct monostate;

    constexpr bool operator==(etl::monostate, etl::monostate) noexcept;

    constexpr bool operator!=(etl::monostate, etl::monostate) noexcept;

    constexpr bool operator<(etl::monostate, etl::monostate) noexcept;

    constexpr bool operator>(etl::monostate, etl::monostate) noexcept;

    constexpr bool operator<=(etl::monostate, etl::monostate) noexcept;

    constexpr bool operator>=(etl::monostate, etl::monostate) noexcept;

    template <etl::size_t I, typename T>
    struct variant_alternative;

    template <etl::size_t I, typename ... Types>
    struct variant_alternative<I, variant<Types...>;

    template <etl::size_t I, typename T>
    struct variant_alternative<I, T const>;

    template <etl::size_t I, typename T>
    using variant_alternative_t = typename variant_alternative<I, T>::type;

    constexpr auto const variant_npos = static_cast<etl::size_t>(-1);

    template <typename ... Types>
    class variant;

    template <typename T, typename ... Types>
    constexpr bool holds_alternative(etl::variant<Types...> const& v) noexcept;

    template <etl::size_t I, typename ... Types>
    constexpr etl::add_pointer_t<etl::variant_alternative_t<I, etl::variant<Types...>>> get_if(etl::variant<Types...>* pv) noexcept;

    template <etl::size_t I, typename ... Types>
    constexpr etl::add_pointer_t<const etl::variant_alternative_t<I, etl::variant<Types...>>> get_if(etl::variant<Types...> const* pv) noexcept;

    template <typename T, typename ... Types>
    constexpr etl::add_pointer_t<T> get_if(etl::variant<Types...>* pv) noexcept;

    template <typename T, typename ... Types>
    constexpr etl::add_pointer_t<const T> get_if(etl::variant<Types...> const* pv) noexcept;
}
```

### Struct `etl::monostate`

``` cpp
struct monostate
{
};
```

Unit type intended for use as a well-behaved empty alternative in etl::variant. In particular, a variant of non-default-constructible types may list etl::monostate as its first alternative: this makes the variant itself default-constructible

-----

### Function `etl::operator==`

``` cpp
constexpr bool operator==(etl::monostate, etl::monostate) noexcept;
```

All instances of etl::monostate compare equal.

-----

### Function `etl::operator!=`

``` cpp
constexpr bool operator!=(etl::monostate, etl::monostate) noexcept;
```

All instances of etl::monostate compare equal.

-----

### Function `etl::operator<`

``` cpp
constexpr bool operator<(etl::monostate, etl::monostate) noexcept;
```

All instances of etl::monostate compare equal.

-----

### Function `etl::operator>`

``` cpp
constexpr bool operator>(etl::monostate, etl::monostate) noexcept;
```

All instances of etl::monostate compare equal.

-----

### Function `etl::operator<=`

``` cpp
constexpr bool operator<=(etl::monostate, etl::monostate) noexcept;
```

All instances of etl::monostate compare equal.

-----

### Function `etl::operator>=`

``` cpp
constexpr bool operator>=(etl::monostate, etl::monostate) noexcept;
```

All instances of etl::monostate compare equal.

-----

### Struct `etl::variant_alternative`

``` cpp
template <etl::size_t I, typename T>
struct variant_alternative;
```

Provides compile-time indexed access to the types of the alternatives of the possibly cv-qualified variant, combining cv-qualifications of the variant (if any) with the cv-qualifications of the alternative.

\\todo Implement

-----

### Struct `etl::variant_alternative`

``` cpp
template <etl::size_t I, typename ... Types>
struct variant_alternative<I, variant<Types...>
{
};
```

Provides compile-time indexed access to the types of the alternatives of the possibly cv-qualified variant, combining cv-qualifications of the variant (if any) with the cv-qualifications of the alternative.

\\todo Implement

-----

### Struct `etl::variant_alternative`

``` cpp
template <etl::size_t I, typename T>
struct variant_alternative<I, T const>
{
};
```

Provides compile-time indexed access to the types of the alternatives of the possibly cv-qualified variant, combining cv-qualifications of the variant (if any) with the cv-qualifications of the alternative.

\\todo Implement

-----

### Variable `etl::variant_npos`

``` cpp
constexpr auto const variant_npos = static_cast<etl::size_t>(-1);
```

This is a special value equal to the largest value representable by the type etl::size\_t, used as the return value of index() when valueless\_by\_exception() is true.

-----

### Class `etl::variant`

``` cpp
template <typename ... Types>
class variant
{
public:
    template <typename T>
    explicit variant(T&& t);

    ~variant();

    constexpr variant<Types...>& operator=(const variant<Types...>& rhs);

    constexpr etl::size_t index() const noexcept;

    constexpr bool valueless_by_exception() const noexcept;

    auto data() const noexcept;
};
```

The class template etl::variant represents a type-safe union. An instance of etl::variant at any given time either holds a value of one of its alternative types.

### Constructor `etl::variant::variant`

``` cpp
template <typename T>
explicit variant(T&& t);
```

Converting constructor.

Constructs a variant holding the alternative type T.

-----

### Destructor `etl::variant::~variant`

``` cpp
~variant();
```

If valueless\_by\_exception is true, does nothing. Otherwise, destroys the currently contained value.

\\todo This destructor is trivial if etl::is\_trivially\_destructible\_v\<T\_i\> is true for all T\_i in Types…

-----

### Function `etl::variant::operator=`

``` cpp
constexpr variant<Types...>& operator=(const variant<Types...>& rhs);
```

Copy-assignment

If both \*this and rhs are valueless by exception, does nothing. Otherwise, if rhs holds the same alternative as \*this, assigns the value contained in rhs to the value contained in \*this. If an exception is thrown, \*this does not become valueless: the value depends on the exception safety guarantee of the alternative’s copy assignment.

-----

### Function `etl::variant::index`

``` cpp
constexpr etl::size_t index() const noexcept;
```

Returns the zero-based index of the alternative that is currently held by the variant. If the variant is valueless\_by\_exception, returns variant\_npos.

-----

### Function `etl::variant::valueless_by_exception`

``` cpp
constexpr bool valueless_by_exception() const noexcept;
```

Returns false if and only if the variant holds a value. Currently always returns false, since there is no default constructor.

-----

### Function `etl::variant::data`

``` cpp
auto data() const noexcept;
```

\\todo Remove & replace with friendship for etl::get\_if.

-----

-----

### Function `etl::holds_alternative`

``` cpp
template <typename T, typename ... Types>
constexpr bool holds_alternative(etl::variant<Types...> const& v) noexcept;
```

Checks if the variant v holds the alternative T. The call is ill-formed if T does not appear exactly once in Types…

-----

### Function `etl::get_if`

``` cpp
template <etl::size_t I, typename ... Types>
constexpr etl::add_pointer_t<etl::variant_alternative_t<I, etl::variant<Types...>>> get_if(etl::variant<Types...>* pv) noexcept;
```

Index-based non-throwing accessor: If pv is not a null pointer and pv-\>index() == I, returns a pointer to the value stored in the variant pointed to by pv. Otherwise, returns a null pointer value. The call is ill-formed if I is not a valid index in the variant.

\\todo Implement

-----

### Function `etl::get_if`

``` cpp
template <etl::size_t I, typename ... Types>
constexpr etl::add_pointer_t<const etl::variant_alternative_t<I, etl::variant<Types...>>> get_if(etl::variant<Types...> const* pv) noexcept;
```

Index-based non-throwing accessor: If pv is not a null pointer and pv-\>index() == I, returns a pointer to the value stored in the variant pointed to by pv. Otherwise, returns a null pointer value. The call is ill-formed if I is not a valid index in the variant.

\\todo Implement

-----

### Function `etl::get_if`

``` cpp
template <typename T, typename ... Types>
constexpr etl::add_pointer_t<T> get_if(etl::variant<Types...>* pv) noexcept;
```

Type-based non-throwing accessor: The call is ill-formed if T is not a unique element of Types….

-----

### Function `etl::get_if`

``` cpp
template <typename T, typename ... Types>
constexpr etl::add_pointer_t<const T> get_if(etl::variant<Types...> const* pv) noexcept;
```

Type-based non-throwing accessor: The call is ill-formed if T is not a unique element of Types….

-----
