---
title: "cctype.hpp"
---

# Header file `cctype.hpp`

``` cpp
#include "etl/version.hpp"
#include "etl/cassert.hpp"
#include "etl/limits.hpp"

namespace etl
{
    constexpr int isalnum(int ch) noexcept;

    constexpr int isalpha(int ch) noexcept;

    constexpr int islower(int ch) noexcept;

    constexpr int isupper(int ch) noexcept;

    constexpr int isdigit(int ch) noexcept;

    constexpr int isxdigit(int ch) noexcept;

    constexpr int isspace(int ch) noexcept;

    constexpr int isblank(int ch) noexcept;

    constexpr int ispunct(int ch) noexcept;

    constexpr int isgraph(int ch) noexcept;

    constexpr int isprint(int ch) noexcept;

    constexpr int iscntrl(int ch) noexcept;

    constexpr int tolower(int ch) noexcept;

    constexpr int toupper(int ch) noexcept;
}
```

### Function `etl::isalnum` \[Strings\]

``` cpp
constexpr int isalnum(int ch) noexcept;
```

Checks if the given character is an alphanumeric character as classified by the default C locale.

*Return values:* Non-zero value if the character is an alphanumeric character, 0 otherwise.

*Notes:* [cppreference.com/w/cpp/string/byte/isalnum](https://en.cppreference.com/w/cpp/string/byte/isalnum)

-----

### Function `etl::isalpha` \[Strings\]

``` cpp
constexpr int isalpha(int ch) noexcept;
```

Checks if the given character is an alphabetic character as classified by the default C locale.

*Return values:* Non-zero value if the character is an alphabetic character, 0 otherwise.

*Notes:* [cppreference.com/w/cpp/string/byte/isalpha](https://en.cppreference.com/w/cpp/string/byte/isalpha)

-----

### Function `etl::islower` \[Strings\]

``` cpp
constexpr int islower(int ch) noexcept;
```

Checks if the given character is classified as a lowercase character according to the default C locale.

*Return values:* Non-zero value if the character is a lowercase letter, zero otherwise.

*Notes:* [cppreference.com/w/cpp/string/byte/islower](https://en.cppreference.com/w/cpp/string/byte/islower)

-----

### Function `etl::isupper` \[Strings\]

``` cpp
constexpr int isupper(int ch) noexcept;
```

Checks if the given character is classified as a uppercase character according to the default C locale.

*Return values:* Non-zero value if the character is a uppercase letter, zero otherwise.

*Notes:* [cppreference.com/w/cpp/string/byte/isupper](https://en.cppreference.com/w/cpp/string/byte/isupper)

-----

### Function `etl::isdigit` \[Strings\]

``` cpp
constexpr int isdigit(int ch) noexcept;
```

Checks if the given character is one of the 10 decimal digits: 0123456789.

*Return values:* Non-zero value if the character is a numeric character, zero otherwise.

*Notes:* [cppreference.com/w/cpp/string/byte/isdigit](https://en.cppreference.com/w/cpp/string/byte/isdigit)

-----

### Function `etl::isxdigit` \[Strings\]

``` cpp
constexpr int isxdigit(int ch) noexcept;
```

Checks if the given character is a hexadecimal numeric character (0123456789abcdefABCDEF).

*Return values:* Non-zero value if the character is a hexadecimal numeric character, zero otherwise.

*Notes:* [cppreference.com/w/cpp/string/byte/isxdigit](https://en.cppreference.com/w/cpp/string/byte/isxdigit)

-----

### Function `etl::isspace` \[Strings\]

``` cpp
constexpr int isspace(int ch) noexcept;
```

Checks if the given character is whitespace character as classified by the default C locale.

*Return values:* Non-zero value if the character is a whitespace character, zero otherwise.

*Notes:* [cppreference.com/w/cpp/string/byte/isspace](https://en.cppreference.com/w/cpp/string/byte/isspace)

-----

### Function `etl::isblank` \[Strings\]

``` cpp
constexpr int isblank(int ch) noexcept;
```

Checks if the given character is a blank character as classified by the currently installed C locale. Blank characters are whitespace characters used to separate words within a sentence. In the default C locale, only space (0x20) and horizontal tab (0x09) are classified as blank characters.

*Return values:* Non-zero value if the character is a blank character, zero otherwise.

*Notes:* [cppreference.com/w/cpp/string/byte/isblank](https://en.cppreference.com/w/cpp/string/byte/isblank)

-----

### Function `etl::ispunct` \[Strings\]

``` cpp
constexpr int ispunct(int ch) noexcept;
```

Checks if the given character is a punctuation character as classified by the current C locale.

*Return values:* Non-zero value if the character is a punctuation character, zero otherwise.

*Notes:* [cppreference.com/w/cpp/string/byte/ispunct](https://en.cppreference.com/w/cpp/string/byte/ispunct)

The default C locale classifies the characters \!”\#$%&’()\*+,-./:;\<=\>?@\[\]^\_\`{|}\~ as punctuation.

-----

### Function `etl::isgraph` \[Strings\]

``` cpp
constexpr int isgraph(int ch) noexcept;
```

Checks if the given character is graphic (has a graphical representation) as classified by the default C locale.

*Return values:* Non-zero value if the character is a punctuation character, zero otherwise.

*Notes:* [cppreference.com/w/cpp/string/byte/isgraph](https://en.cppreference.com/w/cpp/string/byte/isgraph)

-----

### Function `etl::isprint` \[Strings\]

``` cpp
constexpr int isprint(int ch) noexcept;
```

Checks if ch is a printable character as classified by the default C locale.

*Return values:* Non-zero value if the character is a punctuation character, zero otherwise.

*Notes:* [cppreference.com/w/cpp/string/byte/isprint](https://en.cppreference.com/w/cpp/string/byte/isprint)

-----

### Function `etl::iscntrl` \[Strings\]

``` cpp
constexpr int iscntrl(int ch) noexcept;
```

Checks if the given character is a control character as classified by the currently installed C locale. In the default, “C” locale, the control characters are the characters with the codes 0x00-0x1F and 0x7F.

*Return values:* Non-zero value if the character is a control character, zero otherwise.

*Notes:* [cppreference.com/w/cpp/string/byte/iscntrl](https://en.cppreference.com/w/cpp/string/byte/iscntrl)

-----

### Function `etl::tolower` \[Strings\]

``` cpp
constexpr int tolower(int ch) noexcept;
```

Converts the given character to lowercase according to the character conversion rules defined by the default C locale.

*Return values:* Lowercase version of ch or unmodified ch if no lowercase version is listed in the current C locale.

*Notes:* [cppreference.com/w/cpp/string/byte/tolower](https://en.cppreference.com/w/cpp/string/byte/tolower)

In the default “C” locale, the following uppercase letters **ABCDEFGHIJKLMNOPQRSTUVWXYZ** are replaced with respective lowercase letters **abcdefghijklmnopqrstuvwxyz**.

-----

### Function `etl::toupper` \[Strings\]

``` cpp
constexpr int toupper(int ch) noexcept;
```

Converts the given character to uppercase according to the character conversion rules defined by the default C locale.

*Return values:* Converted character or ch if no uppercase version is defined by the current C locale.

*Notes:* [cppreference.com/w/cpp/string/byte/toupper](https://en.cppreference.com/w/cpp/string/byte/toupper)

In the default “C” locale, the following lowercase letters **abcdefghijklmnopqrstuvwxyz** are replaced with respective uppercase letters **ABCDEFGHIJKLMNOPQRSTUVWXYZ**.

-----
