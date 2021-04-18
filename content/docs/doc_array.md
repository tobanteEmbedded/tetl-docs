---
title: "array.hpp"
---

# Header file `array.hpp`

``` cpp
#include "etl/version.hpp"
#include "etl/algorithm.hpp"
#include "etl/cassert.hpp"
#include "etl/cstddef.hpp"
#include "etl/iterator.hpp"
#include "etl/type_traits.hpp"

namespace etl
{
    template <typename Type, etl::size_t Size>
    struct array;

    //=== swap ===//
    template <typename T, etl::size_t N>
    constexpr void swap(array<T, N>& lhs, array<T, N>& rhs) noexcept('hidden');

    //=== tuple_size ===//
    template <typename T, etl::size_t N>
    struct tuple_size<array<T, N>;

    //=== tuple_element ===//
    template <etl::size_t I, typename T>
    struct tuple_element;
    template <etl::size_t I, typename T, etl::size_t N>
    struct tuple_element<I, array<T, N>;

    //=== array_eqaulity ===//
    template <typename T, etl::size_t N>
    constexpr bool operator==(array<T, N> const& lhs, array<T, N> const& rhs);
    template <typename T, etl::size_t N>
    constexpr bool operator!=(array<T, N> const& lhs, array<T, N> const& rhs);

    //=== array_compare ===//
    template <typename T, etl::size_t N>
    constexpr bool operator<(array<T, N> const& lhs, array<T, N> const& rhs);
    template <typename T, etl::size_t N>
    constexpr bool operator<=(array<T, N> const& lhs, array<T, N> const& rhs);
    template <typename T, etl::size_t N>
    constexpr bool operator>(array<T, N> const& lhs, array<T, N> const& rhs);
    template <typename T, etl::size_t N>
    constexpr bool operator>=(array<T, N> const& lhs, array<T, N> const& rhs);

    //=== get ===//
    template <etl::size_t Index, typename T, etl::size_t Size>
    constexpr T& get(array<T, Size>& array) noexcept;
    template <etl::size_t Index, typename T, etl::size_t Size>
    constexpr T const& get(array<T, Size> const& array) noexcept;
    template <etl::size_t Index, typename T, etl::size_t Size>
    constexpr T&& get(array<T, Size>&& array) noexcept;
    template <etl::size_t Index, typename T, etl::size_t Size>
    constexpr T const&& get(array<T, Size> const&& array) noexcept;

    //=== to_array ===//
    template <typename T, etl::size_t N>
    constexpr array<remove_cv_t<T>, N> to_array(T(& a)[I]);
    template <typename T, etl::size_t N>
    constexpr auto to_array(T(&& a)[I]);
}
```

### Struct `etl::array` \[Containers\]

``` cpp
template <typename Type, etl::size_t Size>
struct array
{
    using value_type = Type;
    using size_type = etl::size_t;
    using difference_type = etl::ptrdiff_t;
    using pointer = Type*;
    using const_pointer = Type const*;
    using reference = Type&;
    using const_reference = Type const&;
    using iterator = Type*;
    using const_iterator = Type const*;
    using reverse_iterator = typename etl::reverse_iterator<iterator>;
    using const_reverse_iterator = typename etl::reverse_iterator<const_iterator>;

    constexpr reference at(etl::array::size_type const pos) noexcept;

    constexpr const_reference at(etl::array::size_type const pos) const noexcept;

    constexpr reference operator[](etl::array::size_type const pos) noexcept;

    constexpr const_reference operator[](etl::array::size_type const pos) const noexcept;

    constexpr reference front() noexcept;

    constexpr const_reference front() const noexcept;

    constexpr reference back() noexcept;

    constexpr const_reference back() const noexcept;

    constexpr pointer data() noexcept;

    constexpr const_pointer data() const noexcept;

    constexpr iterator begin() noexcept;

    constexpr const_iterator begin() const noexcept;

    constexpr const_iterator cbegin() const noexcept;

    constexpr iterator end() noexcept;

    constexpr const_iterator end() const noexcept;

    constexpr const_iterator cend() const noexcept;

    constexpr reverse_iterator rbegin() noexcept;

    constexpr const_reverse_iterator rbegin() const noexcept;

    constexpr const_reverse_iterator crbegin() const noexcept;

    constexpr reverse_iterator rend() noexcept;

    constexpr const_reverse_iterator rend() const noexcept;

    constexpr const_reverse_iterator crend() const noexcept;

    constexpr bool empty() const noexcept;

    constexpr size_type size() const noexcept;

    constexpr size_type max_size() const noexcept;

    constexpr void fill(etl::array::const_reference value);

    constexpr void swap(array<Type, Size>& other) noexcept('hidden');
};
```

array is a container that encapsulates fixed size arrays.

This container is an aggregate type with the same semantics as a struct holding a C-style array Type\[N\] as its only non-static data member. Unlike a C-style array, it doesn’t decay to Type\* automatically. As an aggregate type, it can be initialized with aggregate-initialization given at most N initializers that are convertible to Type: `array<int, 3> a = {1,2,3};`

### Type alias `etl::array::value_type`

``` cpp
using value_type = Type;
```

The …

-----

### Type alias `etl::array::size_type`

``` cpp
using size_type = etl::size_t;
```

The …

-----

### Type alias `etl::array::difference_type`

``` cpp
using difference_type = etl::ptrdiff_t;
```

The …

-----

### Type alias `etl::array::pointer`

``` cpp
using pointer = Type*;
```

The …

-----

### Type alias `etl::array::const_pointer`

``` cpp
using const_pointer = Type const*;
```

The …

-----

### Type alias `etl::array::reference`

``` cpp
using reference = Type&;
```

The …

-----

### Type alias `etl::array::const_reference`

``` cpp
using const_reference = Type const&;
```

The …

-----

### Type alias `etl::array::iterator`

``` cpp
using iterator = Type*;
```

The …

-----

### Type alias `etl::array::const_iterator`

``` cpp
using const_iterator = Type const*;
```

The …

-----

### Type alias `etl::array::reverse_iterator`

``` cpp
using reverse_iterator = typename etl::reverse_iterator<iterator>;
```

The …

-----

### Type alias `etl::array::const_reverse_iterator`

``` cpp
using const_reverse_iterator = typename etl::reverse_iterator<const_iterator>;
```

The …

-----

### Function `etl::array::at`

``` cpp
constexpr reference at(etl::array::size_type const pos) noexcept;
```

Accesses the specified item with range checking.

-----

### Function `etl::array::at`

``` cpp
constexpr const_reference at(etl::array::size_type const pos) const noexcept;
```

Accesses the specified const item with range checking.

-----

### Function `etl::array::operator[]`

``` cpp
constexpr reference operator[](etl::array::size_type const pos) noexcept;
```

Accesses the specified item with range checking.

-----

### Function `etl::array::operator[]`

``` cpp
constexpr const_reference operator[](etl::array::size_type const pos) const noexcept;
```

Accesses the specified item with range checking.

-----

### Function `etl::array::front`

``` cpp
constexpr reference front() noexcept;
```

Accesses the first item.

-----

### Function `etl::array::front`

``` cpp
constexpr const_reference front() const noexcept;
```

Accesses the first item.

-----

### Function `etl::array::back`

``` cpp
constexpr reference back() noexcept;
```

Accesses the last item.

-----

### Function `etl::array::back`

``` cpp
constexpr const_reference back() const noexcept;
```

Accesses the last item.

-----

### Function `etl::array::data`

``` cpp
constexpr pointer data() noexcept;
```

Returns pointer to the underlying array serving as element storage. The pointer is such that range \[data(); data() + size()) is always a valid range, even if the container is empty (data() is not dereferenceable in that case).

-----

### Function `etl::array::data`

``` cpp
constexpr const_pointer data() const noexcept;
```

Returns pointer to the underlying array serving as element storage. The pointer is such that range \[data(); data() + size()) is always a valid range, even if the container is empty (data() is not dereferenceable in that case).

-----

### Function `etl::array::begin`

``` cpp
constexpr iterator begin() noexcept;
```

Returns an iterator to the beginning.

-----

### Function `etl::array::begin`

``` cpp
constexpr const_iterator begin() const noexcept;
```

Returns an iterator to the beginning.

-----

### Function `etl::array::cbegin`

``` cpp
constexpr const_iterator cbegin() const noexcept;
```

Returns an const iterator to the beginning.

-----

### Function `etl::array::end`

``` cpp
constexpr iterator end() noexcept;
```

Returns an iterator to the end.

-----

### Function `etl::array::end`

``` cpp
constexpr const_iterator end() const noexcept;
```

Returns an iterator to the end.

-----

### Function `etl::array::cend`

``` cpp
constexpr const_iterator cend() const noexcept;
```

Returns an const iterator to the end.

-----

### Function `etl::array::rbegin`

``` cpp
constexpr reverse_iterator rbegin() noexcept;
```

Returns a reverse iterator to the first element of the reversed array. It corresponds to the last element of the non-reversed array. If the array is empty, the returned iterator is equal to rend().

-----

### Function `etl::array::rbegin`

``` cpp
constexpr const_reverse_iterator rbegin() const noexcept;
```

Returns a reverse iterator to the first element of the reversed array. It corresponds to the last element of the non-reversed array. If the array is empty, the returned iterator is equal to rend().

-----

### Function `etl::array::crbegin`

``` cpp
constexpr const_reverse_iterator crbegin() const noexcept;
```

Returns a reverse iterator to the first element of the reversed array. It corresponds to the last element of the non-reversed array. If the array is empty, the returned iterator is equal to rend().

-----

### Function `etl::array::rend`

``` cpp
constexpr reverse_iterator rend() noexcept;
```

Returns a reverse iterator to the element following the last element of the reversed array. It corresponds to the element preceding the first element of the non-reversed array. This element acts as a placeholder, attempting to access it results in undefined behavior.

-----

### Function `etl::array::rend`

``` cpp
constexpr const_reverse_iterator rend() const noexcept;
```

Returns a reverse iterator to the element following the last element of the reversed array. It corresponds to the element preceding the first element of the non-reversed array. This element acts as a placeholder, attempting to access it results in undefined behavior.

-----

### Function `etl::array::crend`

``` cpp
constexpr const_reverse_iterator crend() const noexcept;
```

Returns a reverse iterator to the element following the last element of the reversed array. It corresponds to the element preceding the first element of the non-reversed array. This element acts as a placeholder, attempting to access it results in undefined behavior.

-----

### Function `etl::array::empty`

``` cpp
constexpr bool empty() const noexcept;
```

Checks if the container has no elements, i.e. whether begin() == end().

-----

### Function `etl::array::size`

``` cpp
constexpr size_type size() const noexcept;
```

Returns the number of elements in the container, i.e. distance(begin(), end()).

-----

### Function `etl::array::max_size`

``` cpp
constexpr size_type max_size() const noexcept;
```

Returns the maximum number of elements the container is able to hold due to system or library implementation limitations, i.e. distance(begin(), end()) for the largest container.

Because each array\<T, N\> is a fixed-size container, the value returned by max\_size equals N (which is also the value returned by size)

-----

### Function `etl::array::fill`

``` cpp
constexpr void fill(etl::array::const_reference value);
```

Assigns the given value value to all elements in the container.

-----

### Function `etl::array::swap`

``` cpp
constexpr void swap(array<Type, Size>& other) noexcept('hidden');
```

Exchanges the contents of the container with those of other. Does not cause iterators and references to associate with the other container.

-----

-----

### Function `etl::swap`

``` cpp
(1) template <typename T, etl::size_t N>
constexpr void swap(array<T, N>& lhs, array<T, N>& rhs) noexcept('hidden');
```

Specializes the swap algorithm for array. Swaps the contents of lhs and rhs.

-----

### Struct `etl::tuple_size`

``` cpp
(1) template <typename T, etl::size_t N>
struct tuple_size<array<T, N>
: integral_constant<size_t,N>
{
};
```

Provides access to the number of elements in an array as a compile-time constant expression.

-----

### Struct `etl::tuple_element`

``` cpp
(1) template <etl::size_t I, typename T>
struct tuple_element;

(2) template <etl::size_t I, typename T, etl::size_t N>
struct tuple_element<I, array<T, N>
{
};
```
Provides compile-time indexed access to the type of the elements of the array using tuple-like interface.

-----

### Function `etl::operator==`

``` cpp
(1) template <typename T, etl::size_t N>
constexpr bool operator==(array<T, N> const& lhs, array<T, N> const& rhs);

(2) template <typename T, etl::size_t N>
constexpr bool operator!=(array<T, N> const& lhs, array<T, N> const& rhs);
```

Checks if the contents of lhs and rhs are equal, that is, they have the same number of elements and each element in lhs compares equal with the element in rhs at the same position.

-----

### Function `etl::operator<`

``` cpp
(1) template <typename T, etl::size_t N>
constexpr bool operator<(array<T, N> const& lhs, array<T, N> const& rhs);

(2) template <typename T, etl::size_t N>
constexpr bool operator<=(array<T, N> const& lhs, array<T, N> const& rhs);

(3) template <typename T, etl::size_t N>
constexpr bool operator>(array<T, N> const& lhs, array<T, N> const& rhs);

(4) template <typename T, etl::size_t N>
constexpr bool operator>=(array<T, N> const& lhs, array<T, N> const& rhs);
```

Compares the contents of lhs and rhs lexicographically. The comparison is performed by a function equivalent to lexicographical\_compare.

-----

### Function `etl::get`

``` cpp
(1) template <etl::size_t Index, typename T, etl::size_t Size>
constexpr T& get(array<T, Size>& array) noexcept;

(2) template <etl::size_t Index, typename T, etl::size_t Size>
constexpr T const& get(array<T, Size> const& array) noexcept;

(3) template <etl::size_t Index, typename T, etl::size_t Size>
constexpr T&& get(array<T, Size>&& array) noexcept;

(4) template <etl::size_t Index, typename T, etl::size_t Size>
constexpr T const&& get(array<T, Size> const&& array) noexcept;
```

Extracts the Ith element element from the array. I must be an integer value in range \[0, N). This is enforced at compile time as opposed to at() or operator\[\].

-----

### Function `etl::to_array`

``` cpp
(1) template <typename T, etl::size_t N>
constexpr array<remove_cv_t<T>, N> to_array(T(& a)[I]);

(2) template <typename T, etl::size_t N>
constexpr auto to_array(T(&& a)[I]);
```

Creates a array from the one dimensional built-in array a. The elements of the array are copy-initialized from the corresponding element of a. Copying or moving multidimensional built-in array is not supported.

-----
