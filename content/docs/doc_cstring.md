---
title: "cstring.hpp"
---

# Header file `cstring.hpp`

``` cpp
#include "etl/version.hpp"
#include "etl/cassert.hpp"
#include "etl/cstddef.hpp"

namespace etl
{
    constexpr char* strcpy(char* dest, char const* src);

    constexpr char* strncpy(char* dest, char const* src, etl::size_t const count);

    constexpr etl::size_t strlen(char const* str);

    constexpr char* strcat(char* dest, char const* src);

    constexpr char* strncat(char* dest, char const* src, etl::size_t const count);

    constexpr int strcmp(char const* lhs, char const* rhs);

    constexpr int strncmp(char const* lhs, char const* rhs, etl::size_t const count);

    constexpr void* memcpy(void* dest, void const* src, etl::size_t n);

    constexpr void* memset(void* s, int c, etl::size_t n);

    constexpr void* memmove(void* dest, void const* src, etl::size_t n);
}
```

### Function `etl::strcpy` \[Strings\]

``` cpp
constexpr char* strcpy(char* dest, char const* src);
```

Copies the character string pointed to by src, including the null terminator, to the character array whose first element is pointed to by dest.

*Return values:* dest

The behavior is undefined if the dest array is not large enough. The behavior is undefined if the strings overlap.

-----

### Function `etl::strncpy` \[Strings\]

``` cpp
constexpr char* strncpy(char* dest, char const* src, etl::size_t const count);
```

Copies at most count characters of the byte string pointed to by src (including the terminating null character) to character array pointed to by dest.

*Return values:* dest

If count is reached before the entire string src was copied, the resulting character array is not null-terminated. If, after copying the terminating null character from src, count is not reached, additional null characters are written to dest until the total of count characters have been written. If the strings overlap, the behavior is undefined.

-----

### Function `etl::strlen` \[Strings\]

``` cpp
constexpr etl::size_t strlen(char const* str);
```

Returns the length of the C string str.

-----

### Function `etl::strcat` \[Strings\]

``` cpp
constexpr char* strcat(char* dest, char const* src);
```

Appends a copy of the character string pointed to by src to the end of the character string pointed to by dest. The character src\[0\] replaces the null terminator at the end of dest. The resulting byte string is null-terminated.

The behavior is undefined if the destination array is not large enough for the contents of both src and dest and the terminating null character. The behavior is undefined if the strings overlap.

-----

### Function `etl::strncat` \[Strings\]

``` cpp
constexpr char* strncat(char* dest, char const* src, etl::size_t const count);
```

Appends a byte string pointed to by src to a byte string pointed to by dest. At most count characters are copied. The resulting byte string is null-terminated.

The destination byte string must have enough space for the contents of both dest and src plus the terminating null character, except that the size of src is limited to count. The behavior is undefined if the strings overlap.

-----

### Function `etl::strcmp` \[Strings\]

``` cpp
constexpr int strcmp(char const* lhs, char const* rhs);
```

Compares the C string lhs to the C string rhs.

This function starts comparing the first character of each string. If they are equal to each other, it continues with the following pairs until the characters differ or until a terminating null-character is reached.

-----

### Function `etl::strncmp` \[Strings\]

``` cpp
constexpr int strncmp(char const* lhs, char const* rhs, etl::size_t const count);
```

Compares at most count characters of two possibly null-terminated arrays. The comparison is done lexicographically. Characters following the null character are not compared.

The behavior is undefined when access occurs past the end of either array lhs or rhs. The behavior is undefined when either lhs or rhs is the null pointer.

-----

### Function `etl::memcpy` \[Strings\]

``` cpp
constexpr void* memcpy(void* dest, void const* src, etl::size_t n);
```

Copy the first n bytes pointed to by src to the buffer pointed to by dest. Source and destination may not overlap. If source and destination might overlap, memmove() must be used instead.

-----

### Function `etl::memset` \[Strings\]

``` cpp
constexpr void* memset(void* s, int c, etl::size_t n);
```

Copies the value of c (converted to an unsigned char) into each of the ﬁrst n characters of the object pointed to by s.

-----

### Function `etl::memmove` \[Strings\]

``` cpp
constexpr void* memmove(void* dest, void const* src, etl::size_t n);
```

Copy the first n bytes pointed to by src to the buffer pointed to by dest. Source and destination may overlap.

*Notes:* Check original implementation. They use `__np_anyptrlt` which is not portable. [clc-wiki.net](https://clc-wiki.net/wiki/C_standard_library:string.h:memmove)

-----
