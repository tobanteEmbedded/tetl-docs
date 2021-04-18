---
title: "bitset.hpp"
---

# Header file `bitset.hpp`

``` cpp
#include "etl/version.hpp"
#include "etl/algorithm.hpp"
#include "etl/array.hpp"
#include "etl/cstddef.hpp"
#include "etl/limits.hpp"
#include "etl/string_view.hpp"

namespace etl
{
    template <etl::size_t N>
    struct bitset;
}
```

### Struct `etl::bitset` \[Utility\]

``` cpp
template <etl::size_t N>
struct bitset
{
    class reference;

    constexpr bitset() noexcept = default;

    constexpr bitset(unsigned long long val) noexcept;

    template <typename CharT, typename Traits>
    explicit bitset(basic_string_view<CharT, Traits> const& str, typename basic_string_view<CharT, Traits>::size_type pos = 0, typename basic_string_view<CharT, Traits>::size_type n = basic_string_view<CharT, Traits>::npos, CharT zero = CharT('0'), CharT one = CharT('1'));

    template <typename CharT>
    explicit bitset(CharT const* str, typename basic_string_view<CharT>::size_type n = basic_string_view<CharT>::npos, CharT zero = CharT('0'), CharT one = CharT('1'));

    constexpr bitset<N>& set() noexcept;

    constexpr bitset<N>& set(etl::size_t pos, bool value = true);

    constexpr bitset<N>& reset() noexcept;

    constexpr bitset<N>& reset(etl::size_t pos) noexcept;

    constexpr bitset<N>& flip() noexcept;

    constexpr bitset<N>& flip(etl::size_t pos) noexcept;

    constexpr etl::bitset::reference operator[](etl::size_t const pos);

    constexpr bool operator[](etl::size_t const pos) const;

    constexpr bool test(etl::size_t const pos) const;

    constexpr bool all() const noexcept;

    constexpr bool any() const noexcept;

    constexpr bool none() const noexcept;

    constexpr etl::size_t count() const noexcept;

    constexpr etl::size_t size() const noexcept;

    constexpr bool operator==(bitset<N> const& rhs) const noexcept;

    constexpr bool operator!=(bitset<N> const& rhs) const noexcept;

    constexpr bitset<N>& operator&=(bitset<N> const& other) noexcept;

    constexpr bitset<N>& operator|=(bitset<N> const& other) noexcept;

    constexpr bitset<N>& operator^=(bitset<N> const& other) noexcept;

    constexpr bitset<N> operator~() const noexcept;
};
```

The class template bitset represents a fixed-size sequence of N bits. Bitsets can be manipulated by standard logic operators.

\\todo Converted to and from strings and integers. Add operators & more docs. \\todo Add tests for sizes that are not a power of two. Broken at the moment. \\todo What if position index is out of bounds? Return nullptr?

### Class `etl::bitset::reference`

``` cpp
class reference
{
public:
    constexpr etl::bitset::reference& operator=(bool value) noexcept;

    constexpr etl::bitset::reference& operator=(etl::bitset::reference const& x) noexcept;

    constexpr operator bool() const noexcept;

    constexpr bool operator~() const noexcept;

    constexpr etl::bitset::reference& flip() noexcept;
};
```

The primary use of etl::bitset::reference is to provide an l-value that can be returned from operator\[\].

This class is used as a proxy object to allow users to interact with individual bits of a bitset, since standard C++ types (like references and pointers) are not built with enough precision to specify individual bits.

### Function `etl::bitset::reference::operator=`

``` cpp
constexpr etl::bitset::reference& operator=(bool value) noexcept;
```

Assigns a value to the referenced bit.

-----

### Function `etl::bitset::reference::operator=`

``` cpp
constexpr etl::bitset::reference& operator=(etl::bitset::reference const& x) noexcept;
```

Assigns a value to the referenced bit.

*Return values:* \*this

-----

### Conversion operator `etl::bitset::reference::operator bool`

``` cpp
constexpr operator bool() const noexcept;
```

Returns the value of the referenced bit.

-----

### Function `etl::bitset::reference::operator~`

``` cpp
constexpr bool operator~() const noexcept;
```

Returns the inverse of the referenced bit.

-----

### Function `etl::bitset::reference::flip`

``` cpp
constexpr etl::bitset::reference& flip() noexcept;
```

Inverts the referenced bit.

*Return values:* \*this

-----

-----

### Constructor `etl::bitset::bitset`

``` cpp
constexpr bitset() noexcept = default;
```

Constructs a bitset with all bits set to zero.

-----

### Constructor `etl::bitset::bitset`

``` cpp
constexpr bitset(unsigned long long val) noexcept;
```

Constructs a bitset, initializing the first (rightmost, least significant) M bit positions to the corresponding bit values of val, where M is the smaller of the number of bits in an unsigned long long and the number of bits N in the bitset being constructed. If M is less than N (the bitset is longer than 64 bits, for typical implementations of unsigned long long), the remaining bit positions are initialized to zeroes.

-----

### Constructor `etl::bitset::bitset`

``` cpp
template <typename CharT, typename Traits>
explicit bitset(basic_string_view<CharT, Traits> const& str, typename basic_string_view<CharT, Traits>::size_type pos = 0, typename basic_string_view<CharT, Traits>::size_type n = basic_string_view<CharT, Traits>::npos, CharT zero = CharT('0'), CharT one = CharT('1'));
```
Constructs a bitset using the characters in the etl::basic\_string\_view str.

An optional starting position pos and length n can be provided, as well as characters denoting alternate values for set (one) and unset (zero) bits. Traits::eq() is used to compare the character values. The effective length of the initializing string is min(n, str.size() - pos).

#### Parameters

  - `str` - string used to initialize the bitset
  - `pos` - a starting offset into str
  - `n` - number of characters to use from str
  - `zero` - alternate character for set bits in str
  - `one` - alternate character for unset bits in str

-----

### Constructor `etl::bitset::bitset`

``` cpp
template <typename CharT>
explicit bitset(CharT const* str, typename basic_string_view<CharT>::size_type n = basic_string_view<CharT>::npos, CharT zero = CharT('0'), CharT one = CharT('1'));
```
Constructs a bitset using the characters in the char const\* str.

#### Parameters

  - `str` - string used to initialize the bitset
  - `n` - number of characters to use from str
  - `zero` - alternate character for set bits in str
  - `one` - alternate character for unset bits in str

-----

### Function `etl::bitset::set`

``` cpp
constexpr bitset<N>& set() noexcept;
```

Sets all bits to true.

-----

### Function `etl::bitset::set`

``` cpp
constexpr bitset<N>& set(etl::size_t pos, bool value = true);
```

Sets the bit at the given position to the given value.

*Return values:* \*this

#### Parameters

  - `pos` - Index of the bit to be modified.
  - `value` - The new value for the bit.

-----

### Function `etl::bitset::reset`

``` cpp
constexpr bitset<N>& reset() noexcept;
```

Sets all bits to false.

-----

### Function `etl::bitset::reset`

``` cpp
constexpr bitset<N>& reset(etl::size_t pos) noexcept;
```

Sets the bit at position pos to false.

*Return values:* \*this

#### Parameters

  - `pos` - Index of the bit to be reset.

-----

### Function `etl::bitset::flip`

``` cpp
constexpr bitset<N>& flip() noexcept;
```

Flips all bits (like operator\~, but in-place).

-----

### Function `etl::bitset::flip`

``` cpp
constexpr bitset<N>& flip(etl::size_t pos) noexcept;
```

Flips the bit at the position pos.

*Return values:* \*this

#### Parameters

  - `pos` - Index of the bit to be reset.

-----

### Function `etl::bitset::operator[]`

``` cpp
constexpr etl::bitset::reference operator[](etl::size_t const pos);
```

Returns a reference like proxy to the bit at the position pos. Perfoms no bounds checking.

#### Parameters

  - `pos` - Index of the bit.

-----

### Function `etl::bitset::operator[]`

``` cpp
constexpr bool operator[](etl::size_t const pos) const;
```

Returns the value of the bit at the position pos. Perfoms no bounds checking.

#### Parameters

  - `pos` - Index of the bit.

-----

### Function `etl::bitset::test`

``` cpp
constexpr bool test(etl::size_t const pos) const;
```

Returns the value of the bit at the position pos. Perfoms no bounds checking.

#### Parameters

  - `pos` - Index of the bit.

-----

### Function `etl::bitset::all`

``` cpp
constexpr bool all() const noexcept;
```

Checks if all bits are set to true.

-----

### Function `etl::bitset::any`

``` cpp
constexpr bool any() const noexcept;
```

Checks if any bits are set to true.

-----

### Function `etl::bitset::none`

``` cpp
constexpr bool none() const noexcept;
```

Checks if none bits are set to true.

-----

### Function `etl::bitset::count`

``` cpp
constexpr etl::size_t count() const noexcept;
```

Returns the number of bits that are set to true.

-----

### Function `etl::bitset::size`

``` cpp
constexpr etl::size_t size() const noexcept;
```

Returns the number of bits that the bitset holds.

-----

### Function `etl::bitset::operator==`

``` cpp
constexpr bool operator==(bitset<N> const& rhs) const noexcept;
```

Returns true if all of the bits in \*this and rhs are equal.

-----

### Function `etl::bitset::operator!=`

``` cpp
constexpr bool operator!=(bitset<N> const& rhs) const noexcept;
```

Returns true if all of the bits in \*this and rhs are not equal.

-----

### Function `etl::bitset::operator&=`

``` cpp
constexpr bitset<N>& operator&=(bitset<N> const& other) noexcept;
```

Sets the bits to the result of binary AND on corresponding pairs of bits of \*this and other.

-----

### Function `etl::bitset::operator|=`

``` cpp
constexpr bitset<N>& operator|=(bitset<N> const& other) noexcept;
```

Sets the bits to the result of binary OR on corresponding pairs of bits of \*this and other.

-----

### Function `etl::bitset::operator^=`

``` cpp
constexpr bitset<N>& operator^=(bitset<N> const& other) noexcept;
```

Sets the bits to the result of binary XOR on corresponding pairs of bits of \*this and other.

-----

### Function `etl::bitset::operator~`

``` cpp
constexpr bitset<N> operator~() const noexcept;
```

Returns a temporary copy of \*this with all bits flipped (binary NOT).

-----

-----
