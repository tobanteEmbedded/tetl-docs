---
title: "version.hpp"
---

# Header file `version.hpp`

``` cpp
#define TETL_VERSION_MAJOR

#define TETL_VERSION_MINOR

#define TETL_VERSION_PATCH

#define TETL_VERSION_STRING

#define TETL_HOSTED

namespace etl
{
    enum class language_standard
    : unsigned char;

    //=== language_standard_compare ===//
    constexpr bool operator==(etl::language_standard lhs, etl::language_standard rhs) noexcept;
    constexpr bool operator!=(etl::language_standard lhs, etl::language_standard rhs) noexcept;
    constexpr bool operator<(etl::language_standard lhs, etl::language_standard rhs) noexcept;
    constexpr bool operator<=(etl::language_standard lhs, etl::language_standard rhs) noexcept;
    constexpr bool operator>(etl::language_standard lhs, etl::language_standard rhs) noexcept;
    constexpr bool operator>=(etl::language_standard lhs, etl::language_standard rhs) noexcept;

    constexpr auto const current_standard = language_standard::cpp_17;
}

#define TETL_CPP_STANDARD
```

## Macro `TETL_VERSION_MAJOR`

``` cpp
#define TETL_VERSION_MAJOR 0
```

The major release version

-----

## Macro `TETL_VERSION_MINOR`

``` cpp
#define TETL_VERSION_MINOR 4
```

The minor release version

-----

## Macro `TETL_VERSION_PATCH`

``` cpp
#define TETL_VERSION_PATCH 0
```

The patch release version

-----

## Macro `TETL_VERSION_STRING`

``` cpp
#define TETL_VERSION_STRING "0.4.0"
```

The library version as a string literal

-----

### Enumeration `etl::language_standard`

``` cpp
enum class language_standard
: unsigned char
{
    cpp_17 = 17,
    cpp_20 = 20,
    cpp_23 = 23
};
```

Enumeration for the currently selected C++ standard version. Unlike the official macro `__cplusplus`, these values only include the published year. This is to make the actual values smaller and therfore fit on smaller word sized chips.

-----

### Function `etl::operator==` \[Utility\]

``` cpp
(1) constexpr bool operator==(etl::language_standard lhs, etl::language_standard rhs) noexcept;

(2) constexpr bool operator!=(etl::language_standard lhs, etl::language_standard rhs) noexcept;

(3) constexpr bool operator<(etl::language_standard lhs, etl::language_standard rhs) noexcept;

(4) constexpr bool operator<=(etl::language_standard lhs, etl::language_standard rhs) noexcept;

(5) constexpr bool operator>(etl::language_standard lhs, etl::language_standard rhs) noexcept;

(6) constexpr bool operator>=(etl::language_standard lhs, etl::language_standard rhs) noexcept;
```

Compares language\_standards

-----

### Variable `etl::current_standard`

``` cpp
constexpr auto const current_standard = language_standard::cpp_17;
```

The currently configured C++ standard.

-----
