---
title: "span.hpp"
---

# Header file `span.hpp`

``` cpp
#include "etl/version.hpp"
#include "etl/array.hpp"
#include "etl/limits.hpp"
#include "etl/type_traits.hpp"

namespace etl
{
    constexpr auto const dynamic_extent = size_t(-1);

    template <typename ElementType, etl::size_t Extent = etl::dynamic_extent>
    class span;
}
```

### Variable `etl::dynamic_extent`

``` cpp
constexpr auto const dynamic_extent = size_t(-1);
```

etl::dynamic\_extent is a constant of type etl::size\_t that is used to differentiate etl::span of static and dynamic extent.

-----

### Class `etl::span` \[Containers\]

``` cpp
template <typename ElementType, etl::size_t Extent = etl::dynamic_extent>
class span
{
public:
    static constexpr 'hidden' extent = Extent;

    constexpr span() noexcept = default;

    template <typename It>
    constexpr span(It first, 'hidden' count);

    template <etl::size_t N>
    constexpr span('hidden'(& arr)[N]) noexcept;

    template <typename U, etl::size_t N>
    constexpr span(etl::array<U, N>& arr) noexcept;

    template <typename U, etl::size_t N>
    constexpr span(etl::array<U, N> const& arr) noexcept;

    template <typename R>
    constexpr span(R&& r);

    constexpr span(const span<ElementType, Extent>& other) noexcept = default;

    constexpr 'hidden' begin() const noexcept;

    constexpr 'hidden' end() const noexcept;

    constexpr 'hidden' front() const;

    constexpr 'hidden' back() const;

    constexpr 'hidden' operator[]('hidden' idx) const;

    constexpr 'hidden' data() const noexcept;

    constexpr 'hidden' size() const noexcept;

    constexpr 'hidden' size_bytes() const noexcept;

    constexpr bool empty() const noexcept;
};
```

A non-owning view over a contiguous sequence of objects.

The class template span describes an object that can refer to a contiguous sequence of objects with the first element of the sequence at position zero. A span can either have a static extent, in which case the number of elements in the sequence is known and encoded in the type, or a dynamic extent.

If a span has dynamic extent a typical implementation holds two members: a pointer to T and a size. A span with static extent may have only one member: a pointer to T.

### Variable `etl::span::extent`

``` cpp
static constexpr 'hidden' extent = Extent;
```

The number of elements in the sequence, or etl::dynamic\_extent if dynamic.

-----

### Constructor `etl::span::span`

``` cpp
constexpr span() noexcept = default;
```

Constructs a span. Constructs an empty span whose data() == nullptr and size() == 0.

This overload only participates in overload resolution if extent == 0 || extent == etl::dynamic\_extent.

\\todo Remove from overload with concepts once available.

-----

### Constructor `etl::span::span`

``` cpp
template <typename It>
constexpr span(It first, 'hidden' count);
```

Constructs a span.

Constructs a span that is a view over the range \[first, first + count); the resulting span has data() == etl::to\_address(first) and size() == count. The behavior is undefined if \[first, first + count) is not a valid range, if It does not actually model contiguous\_iterator, or if extent \!= etl::dynamic\_extent && count \!= extent. This overload only participates in overload resolution if, It satisfies contiguous\_iterator and the conversion from etl::iter\_reference\_t\<It\> to element\_type is at most a qualification conversion.

\\todo Add explicit(extent \!= etl::dynamic\_extent).

-----

### Constructor `etl::span::span`

``` cpp
template <etl::size_t N>
constexpr span('hidden'(& arr)[N]) noexcept;
```

Constructs a span. From a c style array.

-----

### Constructor `etl::span::span`

``` cpp
template <typename U, etl::size_t N>
constexpr span(etl::array<U, N>& arr) noexcept;
```

Constructs a span. From a etl::array\<Type,Size\>.

-----

### Constructor `etl::span::span`

``` cpp
template <typename U, etl::size_t N>
constexpr span(etl::array<U, N> const& arr) noexcept;
```

Constructs a span. From a etl::array\<Type,Size\> const.

-----

### Constructor `etl::span::span`

``` cpp
template <typename R>
constexpr span(R&& r);
```

Constructs a span.

\\todo Add explicit(extent \!= etl::dynamic\_extent)

-----

### Constructor `etl::span::span`

``` cpp
constexpr span(const span<ElementType, Extent>& other) noexcept = default;
```

Constructs a span.

-----

### Function `etl::span::begin`

``` cpp
constexpr 'hidden' begin() const noexcept;
```

Returns an iterator to the first element of the span. If the span is empty, the returned iterator will be equal to end().

-----

### Function `etl::span::end`

``` cpp
constexpr 'hidden' end() const noexcept;
```

Returns an iterator to the element following the last element of the span. This element acts as a placeholder; attempting to access it results in undefined behavior

-----

### Function `etl::span::front`

``` cpp
constexpr 'hidden' front() const;
```

Returns a reference to the first element in the span. Calling front on an empty span results in undefined behavior.

-----

### Function `etl::span::back`

``` cpp
constexpr 'hidden' back() const;
```

Returns a reference to the last element in the span. Calling front on an empty span results in undefined behavior.

-----

### Function `etl::span::operator[]`

``` cpp
constexpr 'hidden' operator[]('hidden' idx) const;
```

Returns a reference to the idx-th element of the sequence. The behavior is undefined if idx is out of range (i.e., if it is greater than or equal to size()).

-----

### Function `etl::span::data`

``` cpp
constexpr 'hidden' data() const noexcept;
```

Returns a pointer to the beginning of the sequence.

-----

### Function `etl::span::size`

``` cpp
constexpr 'hidden' size() const noexcept;
```

Returns the number of elements in the span.

-----

### Function `etl::span::size_bytes`

``` cpp
constexpr 'hidden' size_bytes() const noexcept;
```

Returns the number of elements in the span.

-----

### Function `etl::span::empty`

``` cpp
constexpr bool empty() const noexcept;
```

Checks if the span is empty.

-----

-----
