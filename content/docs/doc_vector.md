---
title: "vector.hpp"
---

# Header file `vector.hpp`

``` cpp
#include "etl/version.hpp"
#include "etl/algorithm.hpp"
#include "etl/array.hpp"
#include "etl/cassert.hpp"
#include "etl/functional.hpp"

namespace etl
{
    template <typename T, etl::size_t Capacity>
    struct static_vector;

    template <typename T, etl::size_t Capacity>
    constexpr void swap(static_vector<T, Capacity>& lhs, static_vector<T, Capacity>& rhs) noexcept;

    //=== static_vector_equality ===//
    template <typename T, etl::size_t Capacity>
    constexpr bool operator==(static_vector<T, Capacity> const& lhs, static_vector<T, Capacity> const& rhs) noexcept;
    template <typename T, etl::size_t Capacity>
    constexpr bool operator!=(static_vector<T, Capacity> const& lhs, static_vector<T, Capacity> const& rhs) noexcept;

    //=== static_vector_lexicographical_compare ===//
    template <typename T, etl::size_t Capacity>
    constexpr bool operator<(static_vector<T, Capacity> const& lhs, static_vector<T, Capacity> const& rhs) noexcept;
    template <typename T, etl::size_t Capacity>
    constexpr bool operator<=(static_vector<T, Capacity> const& lhs, static_vector<T, Capacity> const& rhs) noexcept;
    template <typename T, etl::size_t Capacity>
    constexpr bool operator>(static_vector<T, Capacity> const& lhs, static_vector<T, Capacity> const& rhs) noexcept;
    template <typename T, etl::size_t Capacity>
    constexpr bool operator>=(static_vector<T, Capacity> const& lhs, static_vector<T, Capacity> const& rhs) noexcept;

    //=== static_vector_erase ===//
    template <typename T, etl::size_t Capacity, typename Predicate>
    constexpr typename static_vector<T, Capacity>::size_type erase_if(static_vector<T, Capacity>& c, Predicate pred);
    template <typename T, etl::size_t Capacity, typename U>
    constexpr typename static_vector<T, Capacity>::size_type erase(static_vector<T, Capacity>& c, U const& value);
}
```

### Struct `etl::static_vector` \[Containers\]

``` cpp
template <typename T, etl::size_t Capacity>
struct static_vector
{
    using value_type = typename base_type::value_type;
    using difference_type = etl::ptrdiff_t;
    using reference = value_type&;
    using const_reference = value_type&;
    using pointer = typename base_type::pointer;
    using const_pointer = typename base_type::const_pointer;
    using iterator = typename base_type::pointer;
    using const_iterator = typename base_type::const_pointer;
    using size_type = etl::size_t;
    using reverse_iterator = ::etl::reverse_iterator<iterator>;
    using const_reverse_iterator = ::etl::reverse_iterator<const_iterator>;

    template <typename U>
    constexpr enable_if_t<is_constructible_v<T, U> && is_assignable_v<etl::static_vector::reference, U &&>, void> push_back(U&& value) noexcept(false);

    constexpr void clear() noexcept;

    constexpr static_vector() = default;

    constexpr static_vector(const static_vector<T, Capacity>& other) noexcept('hidden');

    constexpr static_vector(static_vector<T, Capacity>&& other) noexcept('hidden');

    constexpr enable_if_t<is_assignable_v<etl::static_vector::reference, etl::static_vector::const_reference>, static_vector<T, Capacity> &> operator=(const static_vector<T, Capacity>& other) noexcept('hidden');

    constexpr enable_if_t<is_assignable_v<etl::static_vector::reference, etl::static_vector::reference>, static_vector<T, Capacity> &> operator=(static_vector<T, Capacity>&& other) noexcept('hidden');

    template <int _concept_requires_656 = 42, ::etl::enable_if_t<(_concept_requires_656 == 43) || (is_copy_constructible_v<T> || is_move_constructible_v<T>), int> = 0>
    constexpr static_vector(etl::static_vector::size_type n) noexcept('hidden');

    template <int _concept_requires_664 = 42, ::etl::enable_if_t<(_concept_requires_664 == 43) || (is_copy_constructible_v<T>), int> = 0>
    constexpr static_vector(etl::static_vector::size_type n, T const& value) noexcept('hidden');

    template <typename InputIter, int _concept_requires_675 = 42, ::etl::enable_if_t<(_concept_requires_675 == 43) || (detail::InputIterator<InputIter>), int> = 0>
    constexpr static_vector(InputIter first, InputIter last);

    //=== size ===//
    constexpr size_type size() const noexcept;

    //=== capacity ===//
    constexpr size_type capacity() const noexcept;
    constexpr size_type max_size() const noexcept;

    //=== assign ===//
    template <typename InputIter>
    constexpr enable_if_t<detail::InputIterator<InputIter>, void> assign(InputIter first, InputIter last) noexcept('hidden');
    constexpr enable_if_t<is_copy_constructible_v<T>, void> assign(etl::static_vector::size_type n, T const& u);

    //=== operator[] ===//
    constexpr reference operator[](etl::static_vector::size_type pos) noexcept;
    constexpr const_reference operator[](etl::static_vector::size_type pos) const noexcept;

    //=== front ===//
    constexpr reference front() noexcept;
    constexpr const_reference front() const noexcept;

    //=== back ===//
    constexpr reference back() noexcept;
    constexpr const_reference back() const noexcept;

    //=== erase ===//
    constexpr enable_if_t<detail::is_movable_v<etl::static_vector::value_type>, etl::static_vector::iterator> erase(etl::static_vector::const_iterator position) noexcept;
    constexpr enable_if_t<detail::is_movable_v<etl::static_vector::value_type>, etl::static_vector::iterator> erase(etl::static_vector::const_iterator first, etl::static_vector::const_iterator last) noexcept;

    //=== swap ===//
    constexpr enable_if_t<is_assignable_v<T &, T &&>, void> swap(static_vector<T, Capacity>& other) noexcept('hidden');

    //=== resize ===//
    constexpr enable_if_t<detail::is_movable_v<etl::static_vector::value_type>, void> resize(etl::static_vector::size_type sz) noexcept('hidden');
    constexpr enable_if_t<is_copy_constructible_v<T>, void> resize(etl::static_vector::size_type sz, T const& value) noexcept('hidden');
};
```

Dynamically-resizable fixed-capacity vector.

### Type alias `etl::static_vector::value_type`

``` cpp
using value_type = typename base_type::value_type;
```

The type being used

-----

### Type alias `etl::static_vector::difference_type`

``` cpp
using difference_type = etl::ptrdiff_t;
```

The type being used

-----

### Type alias `etl::static_vector::reference`

``` cpp
using reference = value_type&;
```

The type being used

-----

### Type alias `etl::static_vector::const_reference`

``` cpp
using const_reference = value_type&;
```

The type being used

-----

### Type alias `etl::static_vector::pointer`

``` cpp
using pointer = typename base_type::pointer;
```

The type being used

-----

### Type alias `etl::static_vector::const_pointer`

``` cpp
using const_pointer = typename base_type::const_pointer;
```

The type being used

-----

### Type alias `etl::static_vector::iterator`

``` cpp
using iterator = typename base_type::pointer;
```

The type being used

-----

### Type alias `etl::static_vector::const_iterator`

``` cpp
using const_iterator = typename base_type::const_pointer;
```

The type being used

-----

### Type alias `etl::static_vector::size_type`

``` cpp
using size_type = etl::size_t;
```

The type being used

-----

### Type alias `etl::static_vector::reverse_iterator`

``` cpp
using reverse_iterator = ::etl::reverse_iterator<iterator>;
```

The type being used

-----

### Type alias `etl::static_vector::const_reverse_iterator`

``` cpp
using const_reverse_iterator = ::etl::reverse_iterator<const_iterator>;
```

The type being used

-----

### Function `etl::static_vector::push_back`

``` cpp
template <typename U>
constexpr enable_if_t<is_constructible_v<T, U> && is_assignable_v<etl::static_vector::reference, U &&>, void> push_back(U&& value) noexcept(false);
```

Appends value at the end of the vector.

\\todo Add noexcept(noexcept(emplace\_back(forward\<U\>(value)))) breaks AVR build GCC8.2 currently.

-----

### Function `etl::static_vector::clear`

``` cpp
constexpr void clear() noexcept;
```

Clears the vector.

-----

### Constructor `etl::static_vector::static_vector`

``` cpp
constexpr static_vector() = default;
```

Default constructor.

-----

### Constructor `etl::static_vector::static_vector`

``` cpp
constexpr static_vector(const static_vector<T, Capacity>& other) noexcept('hidden');
```

Copy constructor.

-----

### Constructor `etl::static_vector::static_vector`

``` cpp
constexpr static_vector(static_vector<T, Capacity>&& other) noexcept('hidden');
```

Move constructor.

-----

### Function `etl::static_vector::operator=`

``` cpp
constexpr enable_if_t<is_assignable_v<etl::static_vector::reference, etl::static_vector::const_reference>, static_vector<T, Capacity> &> operator=(const static_vector<T, Capacity>& other) noexcept('hidden');
```

Copy assignment.

-----

### Function `etl::static_vector::operator=`

``` cpp
constexpr enable_if_t<is_assignable_v<etl::static_vector::reference, etl::static_vector::reference>, static_vector<T, Capacity> &> operator=(static_vector<T, Capacity>&& other) noexcept('hidden');
```

Move assignment.

-----

### Constructor `etl::static_vector::static_vector`

``` cpp
template <int _concept_requires_656 = 42, ::etl::enable_if_t<(_concept_requires_656 == 43) || (is_copy_constructible_v<T> || is_move_constructible_v<T>), int> = 0>
constexpr static_vector(etl::static_vector::size_type n) noexcept('hidden');
```

Initializes vector with n default-constructed elements.

-----

### Constructor `etl::static_vector::static_vector`

``` cpp
template <int _concept_requires_664 = 42, ::etl::enable_if_t<(_concept_requires_664 == 43) || (is_copy_constructible_v<T>), int> = 0>
constexpr static_vector(etl::static_vector::size_type n, T const& value) noexcept('hidden');
```

Initializes vector with n with value.

-----

### Constructor `etl::static_vector::static_vector`

``` cpp
template <typename InputIter, int _concept_requires_675 = 42, ::etl::enable_if_t<(_concept_requires_675 == 43) || (detail::InputIterator<InputIter>), int> = 0>
constexpr static_vector(InputIter first, InputIter last);
```

Initialize vector from range \[first, last).

-----

### Function `etl::static_vector::size`

``` cpp
(1) constexpr size_type size() const noexcept;
```

Number of elements in the vector

-----

### Function `etl::static_vector::capacity`

``` cpp
(1) constexpr size_type capacity() const noexcept;

(2) constexpr size_type max_size() const noexcept;
```

Maximum number of elements that can be allocated in the vector

-----

### Function `etl::static_vector::assign`

``` cpp
(1) template <typename InputIter>
constexpr enable_if_t<detail::InputIterator<InputIter>, void> assign(InputIter first, InputIter last) noexcept('hidden');

(2) constexpr enable_if_t<is_copy_constructible_v<T>, void> assign(etl::static_vector::size_type n, T const& u);
```

assign

-----

### Function `etl::static_vector::operator[]`

``` cpp
(1) constexpr reference operator[](etl::static_vector::size_type pos) noexcept;

(2) constexpr const_reference operator[](etl::static_vector::size_type pos) const noexcept;
```

Unchecked access to element at index pos (UB if index not in range)

-----

### Function `etl::static_vector::front`

``` cpp
(1) constexpr reference front() noexcept;

(2) constexpr const_reference front() const noexcept;
```

front

-----

### Function `etl::static_vector::back`

``` cpp
(1) constexpr reference back() noexcept;

(2) constexpr const_reference back() const noexcept;
```

back

-----

### Function `etl::static_vector::erase`

``` cpp
(1) constexpr enable_if_t<detail::is_movable_v<etl::static_vector::value_type>, etl::static_vector::iterator> erase(etl::static_vector::const_iterator position) noexcept;

(2) constexpr enable_if_t<detail::is_movable_v<etl::static_vector::value_type>, etl::static_vector::iterator> erase(etl::static_vector::const_iterator first, etl::static_vector::const_iterator last) noexcept;
```

erase

-----

### Function `etl::static_vector::swap`

``` cpp
(1) constexpr enable_if_t<is_assignable_v<T &, T &&>, void> swap(static_vector<T, Capacity>& other) noexcept('hidden');
```

Exchanges the contents of the container with those of other.

-----

### Function `etl::static_vector::resize`

``` cpp
(1) constexpr enable_if_t<detail::is_movable_v<etl::static_vector::value_type>, void> resize(etl::static_vector::size_type sz) noexcept('hidden');

(2) constexpr enable_if_t<is_copy_constructible_v<T>, void> resize(etl::static_vector::size_type sz, T const& value) noexcept('hidden');
```

Resizes the container to contain sz elements. If elements need to be appended, these are move-constructed from `T{}` (or copy-constructed if `T` is not `is_move_constructible_v`).

-----

-----

### Function `etl::swap`

``` cpp
template <typename T, etl::size_t Capacity>
constexpr void swap(static_vector<T, Capacity>& lhs, static_vector<T, Capacity>& rhs) noexcept;
```

Specializes the swap algorithm for static\_vector. Swaps the contents of lhs and rhs.

-----

### Function `etl::operator==`

``` cpp
(1) template <typename T, etl::size_t Capacity>
constexpr bool operator==(static_vector<T, Capacity> const& lhs, static_vector<T, Capacity> const& rhs) noexcept;

(2) template <typename T, etl::size_t Capacity>
constexpr bool operator!=(static_vector<T, Capacity> const& lhs, static_vector<T, Capacity> const& rhs) noexcept;
```

Compares the contents of two vectors.

Checks if the contents of lhs and rhs are equal, that is, they have the same number of elements and each element in lhs compares equal with the element in rhs at the same position.

-----

### Function `etl::operator<`

``` cpp
(1) template <typename T, etl::size_t Capacity>
constexpr bool operator<(static_vector<T, Capacity> const& lhs, static_vector<T, Capacity> const& rhs) noexcept;

(2) template <typename T, etl::size_t Capacity>
constexpr bool operator<=(static_vector<T, Capacity> const& lhs, static_vector<T, Capacity> const& rhs) noexcept;

(3) template <typename T, etl::size_t Capacity>
constexpr bool operator>(static_vector<T, Capacity> const& lhs, static_vector<T, Capacity> const& rhs) noexcept;

(4) template <typename T, etl::size_t Capacity>
constexpr bool operator>=(static_vector<T, Capacity> const& lhs, static_vector<T, Capacity> const& rhs) noexcept;
```

Compares the contents of two vectors.

Compares the contents of lhs and rhs lexicographically. The comparison is performed by a function equivalent to lexicographical\_compare.

-----

### Function `etl::erase_if`

``` cpp
(1) template <typename T, etl::size_t Capacity, typename Predicate>
constexpr typename static_vector<T, Capacity>::size_type erase_if(static_vector<T, Capacity>& c, Predicate pred);

(2) template <typename T, etl::size_t Capacity, typename U>
constexpr typename static_vector<T, Capacity>::size_type erase(static_vector<T, Capacity>& c, U const& value);
```

Erases all elements that satisfy the predicate pred from the container.

*Return values:* The number of erased elements.

*Notes:* [cppreference.com/w/cpp/container/vector/erase2](https://en.cppreference.com/w/cpp/container/vector/erase2)

-----
