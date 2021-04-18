---
title: "string_view.hpp"
---

# Header file `string_view.hpp`

``` cpp
#include "etl/version.hpp"
#include "etl/algorithm.hpp"
#include "etl/cassert.hpp"
#include "etl/cstddef.hpp"
#include "etl/iterator.hpp"
#include "etl/memory.hpp"

namespace etl
{
    template <typename CharType, typename Traits = etl::char_traits<CharType>>>
    class basic_string_view;

    template <typename CharType, typename Traits>
    constexpr bool operator==(basic_string_view<CharType, Traits> lhs, basic_string_view<CharType, Traits> rhs) noexcept;

    template <typename CharType, typename Traits>
    constexpr bool operator!=(basic_string_view<CharType, Traits> lhs, basic_string_view<CharType, Traits> rhs) noexcept;

    template <typename CharType, typename Traits>
    constexpr bool operator<(basic_string_view<CharType, Traits> lhs, basic_string_view<CharType, Traits> rhs) noexcept;

    template <typename CharType, typename Traits>
    constexpr bool operator<=(basic_string_view<CharType, Traits> lhs, basic_string_view<CharType, Traits> rhs) noexcept;

    template <typename CharType, typename Traits>
    constexpr bool operator>(basic_string_view<CharType, Traits> lhs, basic_string_view<CharType, Traits> rhs) noexcept;

    template <typename CharType, typename Traits>
    constexpr bool operator>=(basic_string_view<CharType, Traits> lhs, basic_string_view<CharType, Traits> rhs) noexcept;
    using string_view = basic_string_view<char, etl::char_traits<char>>;

    inline namespace literals
    {
        inline namespace string_view_literals
        {
            constexpr etl::string_view operator""_sv(char const* str, etl::size_t len) noexcept;
        }
    }
}
```

### Class `etl::basic_string_view` \[Strings\]

``` cpp
template <typename CharType, typename Traits = etl::char_traits<CharType>>>
class basic_string_view
{
public:
    using traits_type = Traits;
    using value_type = CharType;
    using pointer = CharType*;
    using const_pointer = CharType const*;
    using reference = CharType&;
    using const_reference = CharType const&;
    using const_iterator = CharType const*;
    using iterator = const_iterator;
    using size_type = etl::size_t;
    using difference_type = etl::ptrdiff_t;
    using const_reverse_iterator = etl::reverse_iterator<const_iterator>;
    using reverse_iterator = const_reverse_iterator;

    constexpr basic_string_view() noexcept = default;

    constexpr basic_string_view(const basic_string_view<CharType, Traits>& other) noexcept = default;

    constexpr basic_string_view(CharType const* str, etl::basic_string_view::size_type size);

    constexpr basic_string_view(CharType const* str);

    template <typename Iter, int _concept_requires_110 = 42, ::etl::enable_if_t<(_concept_requires_110 == 43) || (detail::RandomAccessIterator<Iter>), int> = 0>
    constexpr basic_string_view(Iter first, Iter last);

    constexpr basic_string_view<CharType, Traits>& operator=(const basic_string_view<CharType, Traits>& view) noexcept = default;

    constexpr const_iterator begin() const noexcept;

    constexpr const_iterator cbegin() const noexcept;

    constexpr const_iterator end() const noexcept;

    constexpr const_iterator cend() const noexcept;

    constexpr const_reverse_iterator rbegin() const noexcept;

    constexpr const_reverse_iterator crbegin() const noexcept;

    constexpr const_reverse_iterator rend() const noexcept;

    constexpr const_reverse_iterator crend() const noexcept;

    constexpr const_reference operator[](etl::basic_string_view::size_type pos) const;

    constexpr const_reference front() const;

    constexpr const_reference back() const;

    constexpr const_pointer data() const noexcept;

    constexpr size_type size() const noexcept;

    constexpr size_type length() const noexcept;

    constexpr size_type max_size() const noexcept;

    constexpr bool empty() const noexcept;

    constexpr void remove_prefix(etl::basic_string_view::size_type n);

    constexpr void remove_suffix(etl::basic_string_view::size_type n);

    constexpr void swap(basic_string_view<CharType, Traits>& v) noexcept;

    constexpr size_type copy(CharType* dest, etl::basic_string_view::size_type count, etl::basic_string_view::size_type pos = 0) const;

    constexpr basic_string_view<CharType, Traits> substr(etl::basic_string_view::size_type pos = 0, etl::basic_string_view::size_type count = npos) const;

    constexpr int compare(basic_string_view<CharType, Traits> v) const noexcept;

    constexpr int compare(etl::basic_string_view::size_type pos1, etl::basic_string_view::size_type count1, basic_string_view<CharType, Traits> v) const;

    constexpr int compare(etl::basic_string_view::size_type pos1, etl::basic_string_view::size_type count1, basic_string_view<CharType, Traits> v, etl::basic_string_view::size_type pos2, etl::basic_string_view::size_type count2) const;

    constexpr int compare(CharType const* s) const;

    constexpr int compare(etl::basic_string_view::size_type pos1, etl::basic_string_view::size_type count1, CharType const* s) const;

    constexpr int compare(etl::basic_string_view::size_type pos1, etl::basic_string_view::size_type count1, CharType const* s, etl::basic_string_view::size_type count2) const;

    constexpr bool starts_with(basic_string_view<CharType, Traits> sv) const noexcept;

    constexpr bool starts_with(CharType c) const noexcept;

    constexpr bool starts_with(CharType const* str) const;

    constexpr bool ends_with(basic_string_view<CharType, Traits> sv) const noexcept;

    constexpr bool ends_with(CharType c) const noexcept;

    constexpr bool ends_with(CharType const* str) const;

    constexpr size_type find(basic_string_view<CharType, Traits> v, etl::basic_string_view::size_type pos = 0) const noexcept;

    constexpr size_type find(CharType ch, etl::basic_string_view::size_type pos = 0) const noexcept;

    constexpr size_type find(CharType const* s, etl::basic_string_view::size_type pos, etl::basic_string_view::size_type count) const;

    constexpr size_type find(CharType const* s, etl::basic_string_view::size_type pos = 0) const;

    constexpr size_type rfind(basic_string_view<CharType, Traits> v, etl::basic_string_view::size_type pos = npos) const noexcept;

    constexpr size_type rfind(CharType c, etl::basic_string_view::size_type pos = npos) const noexcept;

    constexpr size_type rfind(CharType const* s, etl::basic_string_view::size_type pos, etl::basic_string_view::size_type count) const;

    constexpr size_type rfind(CharType const* s, etl::basic_string_view::size_type pos = npos) const;

    constexpr size_type find_first_of(basic_string_view<CharType, Traits> v, etl::basic_string_view::size_type pos = 0) const noexcept;

    constexpr size_type find_first_of(CharType c, etl::basic_string_view::size_type pos = 0) const noexcept;

    constexpr size_type find_first_of(CharType const* s, etl::basic_string_view::size_type pos, etl::basic_string_view::size_type count) const;

    constexpr size_type find_first_of(CharType const* s, etl::basic_string_view::size_type pos = 0) const;

    constexpr size_type find_last_of(basic_string_view<CharType, Traits> v, etl::basic_string_view::size_type pos = npos) const noexcept;

    constexpr size_type find_last_of(CharType c, etl::basic_string_view::size_type pos = npos) const noexcept;

    constexpr size_type find_last_of(CharType const* s, etl::basic_string_view::size_type pos, etl::basic_string_view::size_type count) const;

    constexpr size_type find_last_of(CharType const* s, etl::basic_string_view::size_type pos = npos) const;

    constexpr size_type find_last_not_of(basic_string_view<CharType, Traits> v, etl::basic_string_view::size_type pos = npos) const noexcept;

    constexpr size_type find_last_not_of(CharType c, etl::basic_string_view::size_type pos = npos) const noexcept;

    constexpr size_type find_last_not_of(etl::basic_string_view::const_pointer s, etl::basic_string_view::size_type pos, etl::basic_string_view::size_type count) const;

    constexpr size_type find_last_not_of(etl::basic_string_view::const_pointer s, etl::basic_string_view::size_type pos = npos) const;

    static constexpr size_type npos = size_type(-1);
};
```

The class template basic\_string\_view describes an object that can refer to a constant contiguous sequence of char-like objects with the first element of the sequence at position zero. A typical implementation holds only two members: a pointer to constant CharType and a size.

### Type alias `etl::basic_string_view::traits_type`

``` cpp
using traits_type = Traits;
```

The character traits type used

-----

### Type alias `etl::basic_string_view::value_type`

``` cpp
using value_type = CharType;
```

The character type used

-----

### Type alias `etl::basic_string_view::pointer`

``` cpp
using pointer = CharType*;
```

Pointer to the character type

-----

### Type alias `etl::basic_string_view::const_pointer`

``` cpp
using const_pointer = CharType const*;
```

Const pointer to the character type

-----

### Type alias `etl::basic_string_view::reference`

``` cpp
using reference = CharType&;
```

Reference to the character type

-----

### Type alias `etl::basic_string_view::const_reference`

``` cpp
using const_reference = CharType const&;
```

Const reference to the character type

-----

### Type alias `etl::basic_string_view::const_iterator`

``` cpp
using const_iterator = CharType const*;
```

Const pointer to the character type

-----

### Type alias `etl::basic_string_view::iterator`

``` cpp
using iterator = const_iterator;
```

Const pointer to the character type

-----

### Type alias `etl::basic_string_view::size_type`

``` cpp
using size_type = etl::size_t;
```

The size type used

-----

### Type alias `etl::basic_string_view::difference_type`

``` cpp
using difference_type = etl::ptrdiff_t;
```

The size type used

-----

### Type alias `etl::basic_string_view::const_reverse_iterator`

``` cpp
using const_reverse_iterator = etl::reverse_iterator<const_iterator>;
```

The reverse iterator type used

-----

### Type alias `etl::basic_string_view::reverse_iterator`

``` cpp
using reverse_iterator = const_reverse_iterator;
```

The reverse iterator type used

-----

### Constructor `etl::basic_string_view::basic_string_view`

``` cpp
constexpr basic_string_view() noexcept = default;
```

Default constructor. Constructs an empty basic\_string\_view. After construction, data() is equal to nullptr, and size() is equal to 0.

-----

### Constructor `etl::basic_string_view::basic_string_view`

``` cpp
constexpr basic_string_view(const basic_string_view<CharType, Traits>& other) noexcept = default;
```

Copy constructor. Constructs a view of the same content as other. After construction, data() is equal to other.data(), and size() is equal to other.size().

-----

### Constructor `etl::basic_string_view::basic_string_view`

``` cpp
constexpr basic_string_view(CharType const* str, etl::basic_string_view::size_type size);
```

Constructs a view of the first count characters of the character array starting with the element pointed by s. s can contain null characters. The behavior is undefined if \[s, s+count) is not a valid range (even though the constructor may not access any of the elements of this range). After construction, data() is equal to s, and size() is equal to count.

-----

### Constructor `etl::basic_string_view::basic_string_view`

``` cpp
constexpr basic_string_view(CharType const* str);
```

Constructs a view of the null-terminated character string pointed to by s, not including the terminating null character. The length of the view is determined as if by Traits::length(s). The behavior is undefined if \[s, s+Traits::length(s)) is not a valid range. After construction, data() is equal to s, and size() is equal to Traits::length(s).

-----

### Constructor `etl::basic_string_view::basic_string_view`

``` cpp
template <typename Iter, int _concept_requires_110 = 42, ::etl::enable_if_t<(_concept_requires_110 == 43) || (detail::RandomAccessIterator<Iter>), int> = 0>
constexpr basic_string_view(Iter first, Iter last);
```

Constructs a basic\_string\_view over the range \[first, last). The behavior is undefined if \[first, last) is not a valid range.

\\todo Improve SFINAE protection. See C++20 standard.

-----

### Function `etl::basic_string_view::operator=`

``` cpp
constexpr basic_string_view<CharType, Traits>& operator=(const basic_string_view<CharType, Traits>& view) noexcept = default;
```

Replaces the view with that of view.

-----

### Function `etl::basic_string_view::begin`

``` cpp
constexpr const_iterator begin() const noexcept;
```

Returns an iterator to the first character of the view.

-----

### Function `etl::basic_string_view::cbegin`

``` cpp
constexpr const_iterator cbegin() const noexcept;
```

Returns an iterator to the first character of the view.

-----

### Function `etl::basic_string_view::end`

``` cpp
constexpr const_iterator end() const noexcept;
```

Returns an iterator to the character following the last character of the view. This character acts as a placeholder, attempting to access it results in undefined behavior.

-----

### Function `etl::basic_string_view::cend`

``` cpp
constexpr const_iterator cend() const noexcept;
```

Returns an iterator to the character following the last character of the view. This character acts as a placeholder, attempting to access it results in undefined behavior.

-----

### Function `etl::basic_string_view::rbegin`

``` cpp
constexpr const_reverse_iterator rbegin() const noexcept;
```

Returns a reverse iterator to the first character of the reversed view. It corresponds to the last character of the non-reversed view.

-----

### Function `etl::basic_string_view::crbegin`

``` cpp
constexpr const_reverse_iterator crbegin() const noexcept;
```

Returns a reverse iterator to the first character of the reversed view. It corresponds to the last character of the non-reversed view.

-----

### Function `etl::basic_string_view::rend`

``` cpp
constexpr const_reverse_iterator rend() const noexcept;
```

Returns a reverse iterator to the character following the last character of the reversed view.

It corresponds to the character preceding the first character of the non-reversed view. This character acts as a placeholder, attempting to access it results in undefined behavior.

-----

### Function `etl::basic_string_view::crend`

``` cpp
constexpr const_reverse_iterator crend() const noexcept;
```

Returns a reverse iterator to the character following the last character of the reversed view.

It corresponds to the character preceding the first character of the non-reversed view. This character acts as a placeholder, attempting to access it results in undefined behavior.

-----

### Function `etl::basic_string_view::operator[]`

``` cpp
constexpr const_reference operator[](etl::basic_string_view::size_type pos) const;
```

Returns a const reference to the character at specified location pos. No bounds checking is performed: the behavior is undefined if pos \>= size().

-----

### Function `etl::basic_string_view::front`

``` cpp
constexpr const_reference front() const;
```

Returns reference to the first character in the view. The behavior is undefined if empty() == true.

-----

### Function `etl::basic_string_view::back`

``` cpp
constexpr const_reference back() const;
```

Returns reference to the last character in the view. The behavior is undefined if empty() == true.

-----

### Function `etl::basic_string_view::data`

``` cpp
constexpr const_pointer data() const noexcept;
```

Returns a pointer to the underlying character array. The pointer is such that the range \[data(); data() + size()) is valid and the values in it correspond to the values of the view.

-----

### Function `etl::basic_string_view::size`

``` cpp
constexpr size_type size() const noexcept;
```

Returns the number of CharT elements in the view, i.e. etl::distance(begin(), end()).

-----

### Function `etl::basic_string_view::length`

``` cpp
constexpr size_type length() const noexcept;
```

Returns the number of CharT elements in the view, i.e. etl::distance(begin(), end()).

-----

### Function `etl::basic_string_view::max_size`

``` cpp
constexpr size_type max_size() const noexcept;
```

The largest possible number of char-like objects that can be referred to by a basic\_string\_view.

-----

### Function `etl::basic_string_view::empty`

``` cpp
constexpr bool empty() const noexcept;
```

Checks if the view has no characters, i.e. whether size() == 0.

-----

### Function `etl::basic_string_view::remove_prefix`

``` cpp
constexpr void remove_prefix(etl::basic_string_view::size_type n);
```

Moves the start of the view forward by n characters. The behavior is undefined if n \> size().

-----

### Function `etl::basic_string_view::remove_suffix`

``` cpp
constexpr void remove_suffix(etl::basic_string_view::size_type n);
```

Moves the end of the view back by n characters. The behavior is undefined if n \> size().

-----

### Function `etl::basic_string_view::swap`

``` cpp
constexpr void swap(basic_string_view<CharType, Traits>& v) noexcept;
```

Exchanges the view with that of v.

-----

### Function `etl::basic_string_view::copy`

``` cpp
constexpr size_type copy(CharType* dest, etl::basic_string_view::size_type count, etl::basic_string_view::size_type pos = 0) const;
```

Copies the substring \[pos, pos + rcount) to the character array pointed to by dest, where rcount is the smaller of count and size() - pos. Equivalent to Traits::copy(dest, data() + pos, rcount).

-----

### Function `etl::basic_string_view::substr`

``` cpp
constexpr basic_string_view<CharType, Traits> substr(etl::basic_string_view::size_type pos = 0, etl::basic_string_view::size_type count = npos) const;
```

Returns a view of the substring \[pos, pos + rcount), where rcount is the smaller of count and size() - pos.

-----

### Function `etl::basic_string_view::compare`

``` cpp
constexpr int compare(basic_string_view<CharType, Traits> v) const noexcept;
```

Compares two character sequences.

*Notes:* [cppreference.com/w/cpp/string/basic\_string\_view/compare](https://en.cppreference.com/w/cpp/string/basic_string_view/compare)

-----

### Function `etl::basic_string_view::compare`

``` cpp
constexpr int compare(etl::basic_string_view::size_type pos1, etl::basic_string_view::size_type count1, basic_string_view<CharType, Traits> v) const;
```

Compares two character sequences. Equivalent to substr(pos1, count1).compare(v).

-----

### Function `etl::basic_string_view::compare`

``` cpp
constexpr int compare(etl::basic_string_view::size_type pos1, etl::basic_string_view::size_type count1, basic_string_view<CharType, Traits> v, etl::basic_string_view::size_type pos2, etl::basic_string_view::size_type count2) const;
```

Compares two character sequences. Equivalent to substr(pos1, count1).compare(v.substr(pos2, count2))

-----

### Function `etl::basic_string_view::compare`

``` cpp
constexpr int compare(CharType const* s) const;
```

Compares two character sequences. Equivalent to compare(basic\_string\_view(s)).

-----

### Function `etl::basic_string_view::compare`

``` cpp
constexpr int compare(etl::basic_string_view::size_type pos1, etl::basic_string_view::size_type count1, CharType const* s) const;
```

Compares two character sequences. Equivalent to substr(pos1, count1).compare(basic\_string\_view(s)).

-----

### Function `etl::basic_string_view::compare`

``` cpp
constexpr int compare(etl::basic_string_view::size_type pos1, etl::basic_string_view::size_type count1, CharType const* s, etl::basic_string_view::size_type count2) const;
```

Compares two character sequences. Equivalent to substr(pos1, count1).compare(basic\_string\_view(s, count2)).

-----

### Function `etl::basic_string_view::starts_with`

``` cpp
constexpr bool starts_with(basic_string_view<CharType, Traits> sv) const noexcept;
```

Checks if the string view begins with the given prefix, where the prefix is a string view.

Effectively returns substr(0, sv.size()) == sv

-----

### Function `etl::basic_string_view::starts_with`

``` cpp
constexpr bool starts_with(CharType c) const noexcept;
```

Checks if the string view begins with the given prefix, where the prefix is a single character.

Effectively returns \!empty() && Traits::eq(front(), c)

-----

### Function `etl::basic_string_view::starts_with`

``` cpp
constexpr bool starts_with(CharType const* str) const;
```

Checks if the string view begins with the given prefix, where the the prefix is a null-terminated character string.

Effectively returns starts\_with(basic\_string\_view(s))

-----

### Function `etl::basic_string_view::ends_with`

``` cpp
constexpr bool ends_with(basic_string_view<CharType, Traits> sv) const noexcept;
```

Checks if the string view ends with the given suffix, where the prefix is a string view.

Effectively returns size() \>= sv.size() && compare(size() - sv.size(), npos, sv) == 0

-----

### Function `etl::basic_string_view::ends_with`

``` cpp
constexpr bool ends_with(CharType c) const noexcept;
```

Checks if the string view ends with the given suffix, where the prefix is a single character.

Effectively returns \!empty() && Traits::eq(back(), c)

-----

### Function `etl::basic_string_view::ends_with`

``` cpp
constexpr bool ends_with(CharType const* str) const;
```

Checks if the string view ends with the given suffix, where the the prefix is a null-terminated character string.

Effectively returns ends\_with(basic\_string\_view(s))

-----

### Function `etl::basic_string_view::find`

``` cpp
constexpr size_type find(basic_string_view<CharType, Traits> v, etl::basic_string_view::size_type pos = 0) const noexcept;
```

Finds the first substring equal to the given character sequence. Finds the first occurence of v in this view, starting at position pos.

*Return values:* Position of the first character of the found substring, or npos if no such substring is found.

-----

### Function `etl::basic_string_view::find`

``` cpp
constexpr size_type find(CharType ch, etl::basic_string_view::size_type pos = 0) const noexcept;
```

Finds the first substring equal to the given character sequence. Equivalent to find(basic\_string\_view(etl::addressof(ch), 1), pos)

*Return values:* Position of the first character of the found substring, or npos if no such substring is found.

-----

### Function `etl::basic_string_view::find`

``` cpp
constexpr size_type find(CharType const* s, etl::basic_string_view::size_type pos, etl::basic_string_view::size_type count) const;
```

Finds the first substring equal to the given character sequence. Equivalent to find(basic\_string\_view(s, count), pos)

*Return values:* Position of the first character of the found substring, or npos if no such substring is found.

-----

### Function `etl::basic_string_view::find`

``` cpp
constexpr size_type find(CharType const* s, etl::basic_string_view::size_type pos = 0) const;
```

Finds the first substring equal to the given character sequence. Equivalent to find(basic\_string\_view(s), pos)

*Return values:* Position of the first character of the found substring, or npos if no such substring is found.

-----

### Function `etl::basic_string_view::rfind`

``` cpp
constexpr size_type rfind(basic_string_view<CharType, Traits> v, etl::basic_string_view::size_type pos = npos) const noexcept;
```

Finds the last substring equal to the given character sequence. Finds the last occurence of v in this view, starting at position pos.

*Return values:* Position of the first character of the found substring or npos if no such substring is found.

-----

### Function `etl::basic_string_view::rfind`

``` cpp
constexpr size_type rfind(CharType c, etl::basic_string_view::size_type pos = npos) const noexcept;
```

Finds the last substring equal to the given character sequence. Equivalent to rfind(basic\_string\_view(etl::addressof(c), 1), pos).

*Return values:* Position of the first character of the found substring or npos if no such substring is found.

-----

### Function `etl::basic_string_view::rfind`

``` cpp
constexpr size_type rfind(CharType const* s, etl::basic_string_view::size_type pos, etl::basic_string_view::size_type count) const;
```

Finds the last substring equal to the given character sequence. Equivalent to rfind(basic\_string\_view(s, count), pos).

*Return values:* Position of the first character of the found substring or npos if no such substring is found.

-----

### Function `etl::basic_string_view::rfind`

``` cpp
constexpr size_type rfind(CharType const* s, etl::basic_string_view::size_type pos = npos) const;
```

Finds the last substring equal to the given character sequence. Equivalent to rfind(basic\_string\_view(s), pos).

*Return values:* Position of the first character of the found substring or npos if no such substring is found.

-----

### Function `etl::basic_string_view::find_first_of`

``` cpp
constexpr size_type find_first_of(basic_string_view<CharType, Traits> v, etl::basic_string_view::size_type pos = 0) const noexcept;
```

Finds the first character equal to any of the characters in the given character sequence. Finds the first occurence of any of the characters of v in this view, starting at position pos.

*Return values:* Position of the first occurrence of any character of the substring, or npos if no such character is found.

-----

### Function `etl::basic_string_view::find_first_of`

``` cpp
constexpr size_type find_first_of(CharType c, etl::basic_string_view::size_type pos = 0) const noexcept;
```

Finds the first character equal to any of the characters in the given character sequence. Equivalent to find\_first\_of(basic\_string\_view(etl::addressof(c), 1), pos)

*Return values:* Position of the first occurrence of any character of the substring, or npos if no such character is found.

-----

### Function `etl::basic_string_view::find_first_of`

``` cpp
constexpr size_type find_first_of(CharType const* s, etl::basic_string_view::size_type pos, etl::basic_string_view::size_type count) const;
```

Finds the first character equal to any of the characters in the given character sequence. Equivalent to find\_first\_of(basic\_string\_view(s, count), pos)

*Return values:* Position of the first occurrence of any character of the substring, or npos if no such character is found.

-----

### Function `etl::basic_string_view::find_first_of`

``` cpp
constexpr size_type find_first_of(CharType const* s, etl::basic_string_view::size_type pos = 0) const;
```

Finds the first character equal to any of the characters in the given character sequence. Equivalent to find\_first\_of(basic\_string\_view(s), pos)

*Return values:* Position of the first occurrence of any character of the substring, or npos if no such character is found.

-----

### Function `etl::basic_string_view::find_last_of`

``` cpp
constexpr size_type find_last_of(basic_string_view<CharType, Traits> v, etl::basic_string_view::size_type pos = npos) const noexcept;
```

Finds the last character equal to one of characters in the given character sequence. Exact search algorithm is not specified. The search considers only the interval \[0; pos\]. If the character is not present in the interval, npos will be returned. Finds the last occurence of any of the characters of v in this view, ending at position pos.

*Return values:* Position of the last occurrence of any character of the substring, or npos if no such character is found.

-----

### Function `etl::basic_string_view::find_last_of`

``` cpp
constexpr size_type find_last_of(CharType c, etl::basic_string_view::size_type pos = npos) const noexcept;
```

Finds the last character equal to one of characters in the given character sequence. Exact search algorithm is not specified. The search considers only the interval \[0; pos\]. If the character is not present in the interval, npos will be returned. Equivalent to find\_last\_of(basic\_string\_view(etl::addressof(c), 1), pos).

*Return values:* Position of the last occurrence of any character of the substring, or npos if no such character is found.

-----

### Function `etl::basic_string_view::find_last_of`

``` cpp
constexpr size_type find_last_of(CharType const* s, etl::basic_string_view::size_type pos, etl::basic_string_view::size_type count) const;
```

Finds the last character equal to one of characters in the given character sequence. Exact search algorithm is not specified. The search considers only the interval \[0; pos\]. If the character is not present in the interval, npos will be returned. Equivalent to find\_last\_of(basic\_string\_view(s, count), pos).

*Return values:* Position of the last occurrence of any character of the substring, or npos if no such character is found.

-----

### Function `etl::basic_string_view::find_last_of`

``` cpp
constexpr size_type find_last_of(CharType const* s, etl::basic_string_view::size_type pos = npos) const;
```

Finds the last character equal to one of characters in the given character sequence. Exact search algorithm is not specified. The search considers only the interval \[0; pos\]. If the character is not present in the interval, npos will be returned. Equivalent to find\_last\_of(basic\_string\_view(s), pos).

*Return values:* Position of the last occurrence of any character of the substring, or npos if no such character is found.

-----

### Function `etl::basic_string_view::find_last_not_of`

``` cpp
constexpr size_type find_last_not_of(basic_string_view<CharType, Traits> v, etl::basic_string_view::size_type pos = npos) const noexcept;
```

Finds the last character not equal to any of the characters of v in this view, starting at position pos.

*Return values:* Position of the last character not equal to any of the characters in the given string, or npos if no such character is found.

-----

### Function `etl::basic_string_view::find_last_not_of`

``` cpp
constexpr size_type find_last_not_of(CharType c, etl::basic_string_view::size_type pos = npos) const noexcept;
```

Finds the last character not equal to any of the characters in the given character sequence. Equivalent to find\_last\_not\_of(basic\_string\_view(etl::addressof(c), 1), pos).

*Return values:* Position of the last character not equal to any of the characters in the given string, or npos if no such character is found.

-----

### Function `etl::basic_string_view::find_last_not_of`

``` cpp
constexpr size_type find_last_not_of(etl::basic_string_view::const_pointer s, etl::basic_string_view::size_type pos, etl::basic_string_view::size_type count) const;
```

Finds the last character not equal to any of the characters in the given character sequence. Equivalent to find\_last\_not\_of(basic\_string\_view(s, count), pos).

*Return values:* Position of the last character not equal to any of the characters in the given string, or npos if no such character is found.

-----

### Function `etl::basic_string_view::find_last_not_of`

``` cpp
constexpr size_type find_last_not_of(etl::basic_string_view::const_pointer s, etl::basic_string_view::size_type pos = npos) const;
```

Finds the last character not equal to any of the characters in the given character sequence. Equivalent to find\_last\_not\_of(basic\_string\_view(s), pos)

*Return values:* Position of the last character not equal to any of the characters in the given string, or npos if no such character is found.

-----

### Variable `etl::basic_string_view::npos`

``` cpp
static constexpr size_type npos = size_type(-1);
```

This is a special value equal to the maximum value representable by the type size\_type.

The exact meaning depends on context, but it is generally used either as end of view indicator by the functions that expect a view index or as the error indicator by the functions that return a view index.

-----

-----

### Function `etl::operator==`

``` cpp
template <typename CharType, typename Traits>
constexpr bool operator==(basic_string_view<CharType, Traits> lhs, basic_string_view<CharType, Traits> rhs) noexcept;
```

Compares two views. All comparisons are done via the compare() member function (which itself is defined in terms of Traits::compare()):

Two views are equal if both the size of lhs and rhs are equal and each character in lhs has an equivalent character in rhs at the same position.

-----

### Function `etl::operator!=`

``` cpp
template <typename CharType, typename Traits>
constexpr bool operator!=(basic_string_view<CharType, Traits> lhs, basic_string_view<CharType, Traits> rhs) noexcept;
```

Compares two views. All comparisons are done via the compare() member function (which itself is defined in terms of Traits::compare()):

Two views are equal if both the size of lhs and rhs are equal and each character in lhs has an equivalent character in rhs at the same position.

-----

### Function `etl::operator<`

``` cpp
template <typename CharType, typename Traits>
constexpr bool operator<(basic_string_view<CharType, Traits> lhs, basic_string_view<CharType, Traits> rhs) noexcept;
```

Compares two views. All comparisons are done via the compare() member function (which itself is defined in terms of Traits::compare()):

The ordering comparisons are done lexicographically – the comparison is performed by a function equivalent to lexicographical\_compare.

-----

### Function `etl::operator<=`

``` cpp
template <typename CharType, typename Traits>
constexpr bool operator<=(basic_string_view<CharType, Traits> lhs, basic_string_view<CharType, Traits> rhs) noexcept;
```

Compares two views. All comparisons are done via the compare() member function (which itself is defined in terms of Traits::compare()):

The ordering comparisons are done lexicographically – the comparison is performed by a function equivalent to lexicographical\_compare.

-----

### Function `etl::operator>`

``` cpp
template <typename CharType, typename Traits>
constexpr bool operator>(basic_string_view<CharType, Traits> lhs, basic_string_view<CharType, Traits> rhs) noexcept;
```

Compares two views. All comparisons are done via the compare() member function (which itself is defined in terms of Traits::compare()):

The ordering comparisons are done lexicographically – the comparison is performed by a function equivalent to lexicographical\_compare.

-----

### Function `etl::operator>=`

``` cpp
template <typename CharType, typename Traits>
constexpr bool operator>=(basic_string_view<CharType, Traits> lhs, basic_string_view<CharType, Traits> rhs) noexcept;
```

Compares two views. All comparisons are done via the compare() member function (which itself is defined in terms of Traits::compare()):

The ordering comparisons are done lexicographically – the comparison is performed by a function equivalent to lexicographical\_compare.

-----

### Type alias `etl::string_view`

``` cpp
using string_view = basic_string_view<char, etl::char_traits<char>>;
```

Typedefs for common character type

-----

### Function `etl::literals::string_view_literals::operator""_sv`

``` cpp
constexpr etl::string_view operator""_sv(char const* str, etl::size_t len) noexcept;
```

Forms a string view of a character literal. Returns etl::string\_view{str, len}

-----
