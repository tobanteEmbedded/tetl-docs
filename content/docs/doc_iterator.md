---
title: "iterator.hpp"
---

# Header file `iterator.hpp`

``` cpp
#include "etl/version.hpp"
#include "etl/cstddef.hpp"
#include "etl/memory.hpp"
#include "etl/type_traits.hpp"
#include "etl/utility.hpp"
#include "etl/warning.hpp"

namespace etl
{
    struct input_iterator_tag;

    struct output_iterator_tag;

    struct forward_iterator_tag;

    struct bidirectional_iterator_tag;

    struct random_access_iterator_tag;

    struct contiguous_iterator_tag;

    //=== iterator_traits ===//
    template <typename Iter>
    struct iterator_traits;
    template <typename T>
    struct iterator_traits<T*>;

    template <typename It, typename Distance>
    constexpr void advance(It& it, Distance n);

    template <typename It>
    constexpr typename iterator_traits<It>::difference_type distance(It first, It last);

    template <typename InputIt>
    constexpr InputIt next(InputIt it, typename iterator_traits<InputIt>::difference_type n = 1);

    template <typename BidirIt>
    constexpr BidirIt prev(BidirIt it, typename iterator_traits<BidirIt>::difference_type n = 1);

    template <typename C>
    constexpr decltype(c.begin()) begin(C& c);

    template <typename C>
    constexpr decltype(c.end()) end(C& c);

    //=== rbegin ===//
    template <typename Container>
    constexpr decltype(c.rbegin()) rbegin(Container& c);
    template <typename Container>
    constexpr decltype(c.rbegin()) rbegin(Container const& c);
    template <typename T, etl::size_t N>
    constexpr reverse_iterator<T *> rbegin(T(& array)[I]);
    template <typename Container>
    constexpr decltype(rbegin(c)) crbegin(Container const& c);

    //=== rend ===//
    template <typename Container>
    constexpr decltype(c.rend()) rend(Container& c);
    template <typename Container>
    constexpr decltype(c.rend()) rend(Container const& c);
    template <typename T, etl::size_t N>
    constexpr reverse_iterator<T *> rend(T(& array)[I]);
    template <typename Container>
    constexpr decltype(rend(c)) crend(Container const& c);

    //=== size ===//
    template <typename C>
    constexpr decltype(c.size()) size(C const& c) noexcept('hidden');
    template <typename T, etl::size_t N>
    constexpr etl::size_t size(T const(& array)[I]) noexcept;

    //=== empty ===//
    template <typename C>
    constexpr decltype(c.empty()) empty(C const& c) noexcept('hidden');
    template <typename T, etl::size_t N>
    constexpr bool empty(T(& array)[I]) noexcept;

    //=== data ===//
    template <typename C>
    constexpr decltype(c.data()) data(C& c) noexcept('hidden');
    template <typename C>
    constexpr decltype(c.data()) data(C const& c) noexcept('hidden');
    template <typename T, etl::size_t N>
    constexpr T* data(T(& array)[I]) noexcept;

    template <typename Iter>
    struct reverse_iterator;

    template <typename Iter>
    constexpr etl::reverse_iterator<Iter> make_reverse_iterator(Iter i) noexcept;

    template <typename Iter1, typename Iter2>
    constexpr bool operator==(etl::reverse_iterator<Iter1> const& lhs, etl::reverse_iterator<Iter2> const& rhs);

    template <typename Iter1, typename Iter2>
    constexpr bool operator!=(etl::reverse_iterator<Iter1> const& lhs, etl::reverse_iterator<Iter2> const& rhs);

    template <typename Iter1, typename Iter2>
    constexpr bool operator<(etl::reverse_iterator<Iter1> const& lhs, etl::reverse_iterator<Iter2> const& rhs);

    template <typename Iter1, typename Iter2>
    constexpr bool operator<=(etl::reverse_iterator<Iter1> const& lhs, etl::reverse_iterator<Iter2> const& rhs);

    template <typename Iter1, typename Iter2>
    constexpr bool operator>(etl::reverse_iterator<Iter1> const& lhs, etl::reverse_iterator<Iter2> const& rhs);

    template <typename Iter1, typename Iter2>
    constexpr bool operator>=(etl::reverse_iterator<Iter1> const& lhs, etl::reverse_iterator<Iter2> const& rhs);

    template <typename Container>
    class back_insert_iterator;

    template <typename Container>
    constexpr back_insert_iterator<Container> back_inserter(Container& container);

    template <typename Container>
    class front_insert_iterator;

    template <typename Container>
    constexpr front_insert_iterator<Container> front_inserter(Container& c);
}
```

### Struct `etl::input_iterator_tag` \[Iterator\]

``` cpp
struct input_iterator_tag
{
};
```

Defines the category of an iterator. Each tag is an empty type and corresponds to one of the five (until C++20) six (since C++20) iterator categories.

-----

### Struct `etl::output_iterator_tag` \[Iterator\]

``` cpp
struct output_iterator_tag
{
};
```

Defines the category of an iterator. Each tag is an empty type and corresponds to one of the five (until C++20) six (since C++20) iterator categories.

-----

### Struct `etl::forward_iterator_tag` \[Iterator\]

``` cpp
struct forward_iterator_tag
: input_iterator_tag
{
};
```

Defines the category of an iterator. Each tag is an empty type and corresponds to one of the five (until C++20) six (since C++20) iterator categories.

-----

### Struct `etl::bidirectional_iterator_tag` \[Iterator\]

``` cpp
struct bidirectional_iterator_tag
: forward_iterator_tag
{
};
```

Defines the category of an iterator. Each tag is an empty type and corresponds to one of the five (until C++20) six (since C++20) iterator categories.

-----

### Struct `etl::random_access_iterator_tag` \[Iterator\]

``` cpp
struct random_access_iterator_tag
: bidirectional_iterator_tag
{
};
```

Defines the category of an iterator. Each tag is an empty type and corresponds to one of the five (until C++20) six (since C++20) iterator categories.

-----

### Struct `etl::contiguous_iterator_tag` \[Iterator\]

``` cpp
struct contiguous_iterator_tag
: random_access_iterator_tag
{
};
```

Defines the category of an iterator. Each tag is an empty type and corresponds to one of the five (until C++20) six (since C++20) iterator categories.

-----

### Struct `etl::iterator_traits` \[Iterator\]

``` cpp
(1) template <typename Iter>
struct iterator_traits;

(2) template <typename T>
struct iterator_traits<T*>
{
};
```

iterator\_traits is the type trait class that provides uniform interface to the properties of LegacyIterator types. This makes it possible to implement algorithms only in terms of iterators.

*Notes:* [cppreference.com/w/cpp/iterator/iterator\_traits](https://en.cppreference.com/w/cpp/iterator/iterator_traits)

The template can be specialized for user-defined iterators so that the information about the iterator can be retrieved even if the type does not provide the usual typedefs.

-----

### Function `etl::advance` \[Iterator\]

``` cpp
template <typename It, typename Distance>
constexpr void advance(It& it, Distance n);
```

Increments given iterator it by n elements. If n is negative, the iterator is decremented. In this case, InputIt must meet the requirements of LegacyBidirectionalIterator, otherwise the behavior is undefined.

*Notes:* [cppreference.com/w/cpp/iterator/advance](https://en.cppreference.com/w/cpp/iterator/advance)

-----

### Function `etl::distance` \[Iterator\]

``` cpp
template <typename It>
constexpr typename iterator_traits<It>::difference_type distance(It first, It last);
```

Returns the number of hops from first to last.

*Notes:* [cppreference.com/w/cpp/iterator/distance](https://en.cppreference.com/w/cpp/iterator/distance)

-----

### Function `etl::next` \[Iterator\]

``` cpp
template <typename InputIt>
constexpr InputIt next(InputIt it, typename iterator_traits<InputIt>::difference_type n = 1);
```

Return the nth successor of iterator it.

-----

### Function `etl::prev` \[Iterator\]

``` cpp
template <typename BidirIt>
constexpr BidirIt prev(BidirIt it, typename iterator_traits<BidirIt>::difference_type n = 1);
```

Return the nth predecessor of iterator it.

-----

### Function `etl::begin`

``` cpp
template <typename C>
constexpr decltype(c.begin()) begin(C& c);
```

Returns an iterator to the beginning of the given container c or array array. These templates rely on `C::begin()` having a reasonable implementation. Returns exactly c.begin(), which is typically an iterator to the beginning of the sequence represented by c. If C is a standard Container, this returns `C::iterator` when c is not const-qualified, and `C::const_iterator` otherwise. Custom overloads of begin may be provided for classes that do not expose a suitable begin() member function, yet can be iterated. \\group begin \\module Iterator

-----

### Function `etl::end`

``` cpp
template <typename C>
constexpr decltype(c.end()) end(C& c);
```

Returns an iterator to the end (i.e. the element after the last element) of the given container c or array array. These templates rely on `C::end()` having a reasonable implementation. \\group end \\module Iterator

-----

### Function `etl::rbegin` \[Iterator\]

``` cpp
(1) template <typename Container>
constexpr decltype(c.rbegin()) rbegin(Container& c);

(2) template <typename Container>
constexpr decltype(c.rbegin()) rbegin(Container const& c);

(3) template <typename T, etl::size_t N>
constexpr reverse_iterator<T *> rbegin(T(& array)[I]);

(4) template <typename Container>
constexpr decltype(rbegin(c)) crbegin(Container const& c);
```

Returns an iterator to the reverse-beginning of the given container.

-----

### Function `etl::rend` \[Iterator\]

``` cpp
(1) template <typename Container>
constexpr decltype(c.rend()) rend(Container& c);

(2) template <typename Container>
constexpr decltype(c.rend()) rend(Container const& c);

(3) template <typename T, etl::size_t N>
constexpr reverse_iterator<T *> rend(T(& array)[I]);

(4) template <typename Container>
constexpr decltype(rend(c)) crend(Container const& c);
```

Returns an iterator to the reverse-end of the given container.

-----

### Function `etl::size` \[Iterator\]

``` cpp
(1) template <typename C>
constexpr decltype(c.size()) size(C const& c) noexcept('hidden');

(2) template <typename T, etl::size_t N>
constexpr etl::size_t size(T const(& array)[I]) noexcept;
```

Returns the size of the given container c or array array. Returns c.size(), converted to the return type if necessary.

-----

### Function `etl::empty` \[Iterator\]

``` cpp
(1) template <typename C>
constexpr decltype(c.empty()) empty(C const& c) noexcept('hidden');

(2) template <typename T, etl::size_t N>
constexpr bool empty(T(& array)[I]) noexcept;
```

Returns whether the given container is empty.

-----

### Function `etl::data` \[Iterator\]

``` cpp
(1) template <typename C>
constexpr decltype(c.data()) data(C& c) noexcept('hidden');

(2) template <typename C>
constexpr decltype(c.data()) data(C const& c) noexcept('hidden');

(3) template <typename T, etl::size_t N>
constexpr T* data(T(& array)[I]) noexcept;
```

Returns a pointer to the block of memory containing the elements of the container.

-----

### Struct `etl::reverse_iterator` \[Iterator\]

``` cpp
template <typename Iter>
struct reverse_iterator
{
    using iterator_type = Iter;
    using value_type = typename iterator_traits<Iter>::value_type;
    using difference_type = typename etl::iterator_traits<Iter>::difference_type;
    using reference = typename etl::iterator_traits<Iter>::reference;
    using pointer = typename etl::iterator_traits<Iter>::pointer;

    constexpr reverse_iterator();

    constexpr reverse_iterator(Iter x);

    template <typename Other>
    constexpr reverse_iterator(reverse_iterator<Other> const& other);

    template <typename Other>
    constexpr reverse_iterator<Iter>& operator=(reverse_iterator<Other> const& other);

    constexpr Iter base() const;

    constexpr reference operator*() const;

    constexpr pointer operator->() const;

    constexpr reverse_iterator<Iter>& operator++();

    constexpr reverse_iterator<Iter> operator++(int);

    constexpr reverse_iterator<Iter>& operator--();

    constexpr reverse_iterator<Iter> operator--(int);

    constexpr reverse_iterator<Iter> operator+(etl::reverse_iterator::difference_type n) const;

    constexpr reverse_iterator<Iter>& operator+=(etl::reverse_iterator::difference_type n);

    constexpr reverse_iterator<Iter> operator-(etl::reverse_iterator::difference_type n) const;

    constexpr reverse_iterator<Iter>& operator-=(etl::reverse_iterator::difference_type n);

    constexpr reference operator[](etl::reverse_iterator::difference_type n) const;
};
```

reverse\_iterator is an iterator adaptor that reverses the direction of a given iterator. In other words, when provided with a bidirectional iterator, `reverse_iterator` produces a new iterator that moves from the end to the beginning of the sequence defined by the underlying bidirectional iterator. This is the iterator returned by member functions `rbegin()` and `rend()` of the standard library containers. \\notes [cppreference.com/w/cpp/iterator/reverse\_iterator](https://en.cppreference.com/w/cpp/iterator/reverse_iterator)

### Type alias `etl::reverse_iterator::iterator_type`

``` cpp
using iterator_type = Iter;
```

The underlying iterator type

-----

### Type alias `etl::reverse_iterator::value_type`

``` cpp
using value_type = typename iterator_traits<Iter>::value_type;
```

The underlying value type

-----

### Type alias `etl::reverse_iterator::difference_type`

``` cpp
using difference_type = typename etl::iterator_traits<Iter>::difference_type;
```

The type of subtracting to iterators

-----

### Type alias `etl::reverse_iterator::reference`

``` cpp
using reference = typename etl::iterator_traits<Iter>::reference;
```

The underlying reference type

-----

### Type alias `etl::reverse_iterator::pointer`

``` cpp
using pointer = typename etl::iterator_traits<Iter>::pointer;
```

The underlying pointer type

-----

### Constructor `etl::reverse_iterator::reverse_iterator`

``` cpp
constexpr reverse_iterator();
```

Constructs a new iterator adaptor.

Default constructor. The underlying iterator is value-initialized. Operations on the resulting iterator have defined behavior if and only if the corresponding operations on a value-initialized Iterator also have defined behavior.

-----

### Constructor `etl::reverse_iterator::reverse_iterator`

``` cpp
constexpr reverse_iterator(Iter x);
```

Constructs a new iterator adaptor.

The underlying iterator is initialized with x.

-----

### Constructor `etl::reverse_iterator::reverse_iterator`

``` cpp
template <typename Other>
constexpr reverse_iterator(reverse_iterator<Other> const& other);
```

Constructs a new iterator adaptor.

The underlying iterator is initialized with that of other.

-----

### Function `etl::reverse_iterator::operator=`

``` cpp
template <typename Other>
constexpr reverse_iterator<Iter>& operator=(reverse_iterator<Other> const& other);
```

The underlying iterator is assigned the value of the underlying iterator of other, i.e. other.base().

-----

### Function `etl::reverse_iterator::base`

``` cpp
constexpr Iter base() const;
```

Returns the underlying base iterator.

-----

### Function `etl::reverse_iterator::operator*`

``` cpp
constexpr reference operator*() const;
```

Returns a reference to the element previous to current.

-----

### Function `etl::reverse_iterator::operator->`

``` cpp
constexpr pointer operator->() const;
```

Returns a pointer to the element previous to current.

-----

### Function `etl::reverse_iterator::operator++`

``` cpp
constexpr reverse_iterator<Iter>& operator++();
```

Pre-increments by one respectively.

-----

### Function `etl::reverse_iterator::operator++`

``` cpp
constexpr reverse_iterator<Iter> operator++(int);
```

Pre-increments by one respectively.

-----

### Function `etl::reverse_iterator::operator--`

``` cpp
constexpr reverse_iterator<Iter>& operator--();
```

Pre-decrements by one respectively.

-----

### Function `etl::reverse_iterator::operator--`

``` cpp
constexpr reverse_iterator<Iter> operator--(int);
```

Pre-decrements by one respectively.

-----

### Function `etl::reverse_iterator::operator+`

``` cpp
constexpr reverse_iterator<Iter> operator+(etl::reverse_iterator::difference_type n) const;
```

Returns an iterator which is advanced by n positions.

-----

### Function `etl::reverse_iterator::operator+=`

``` cpp
constexpr reverse_iterator<Iter>& operator+=(etl::reverse_iterator::difference_type n);
```

Advances the iterator by n or -n positions respectively.

-----

### Function `etl::reverse_iterator::operator-`

``` cpp
constexpr reverse_iterator<Iter> operator-(etl::reverse_iterator::difference_type n) const;
```

Returns an iterator which is advanced by -n positions.

-----

### Function `etl::reverse_iterator::operator-=`

``` cpp
constexpr reverse_iterator<Iter>& operator-=(etl::reverse_iterator::difference_type n);
```

Advances the iterator by n or -n positions respectively.

-----

### Function `etl::reverse_iterator::operator[]`

``` cpp
constexpr reference operator[](etl::reverse_iterator::difference_type n) const;
```

Returns a reference to the element at specified relative location.

-----

-----

### Function `etl::make_reverse_iterator`

``` cpp
template <typename Iter>
constexpr etl::reverse_iterator<Iter> make_reverse_iterator(Iter i) noexcept;
```

Convenience function template that constructs a etl::reverse\_iterator for the given iterator i (which must be a LegacyBidirectionalIterator) with the type deduced from the type of the argument.

-----

### Function `etl::operator==`

``` cpp
template <typename Iter1, typename Iter2>
constexpr bool operator==(etl::reverse_iterator<Iter1> const& lhs, etl::reverse_iterator<Iter2> const& rhs);
```

Compares the underlying iterators. Inverse comparisons are applied in order to take into account that the iterator order is reversed.

-----

### Function `etl::operator!=`

``` cpp
template <typename Iter1, typename Iter2>
constexpr bool operator!=(etl::reverse_iterator<Iter1> const& lhs, etl::reverse_iterator<Iter2> const& rhs);
```

Compares the underlying iterators. Inverse comparisons are applied in order to take into account that the iterator order is reversed.

-----

### Function `etl::operator<`

``` cpp
template <typename Iter1, typename Iter2>
constexpr bool operator<(etl::reverse_iterator<Iter1> const& lhs, etl::reverse_iterator<Iter2> const& rhs);
```

Compares the underlying iterators. Inverse comparisons are applied in order to take into account that the iterator order is reversed.

-----

### Function `etl::operator<=`

``` cpp
template <typename Iter1, typename Iter2>
constexpr bool operator<=(etl::reverse_iterator<Iter1> const& lhs, etl::reverse_iterator<Iter2> const& rhs);
```

Compares the underlying iterators. Inverse comparisons are applied in order to take into account that the iterator order is reversed.

-----

### Function `etl::operator>`

``` cpp
template <typename Iter1, typename Iter2>
constexpr bool operator>(etl::reverse_iterator<Iter1> const& lhs, etl::reverse_iterator<Iter2> const& rhs);
```

Compares the underlying iterators. Inverse comparisons are applied in order to take into account that the iterator order is reversed.

-----

### Function `etl::operator>=`

``` cpp
template <typename Iter1, typename Iter2>
constexpr bool operator>=(etl::reverse_iterator<Iter1> const& lhs, etl::reverse_iterator<Iter2> const& rhs);
```

Compares the underlying iterators. Inverse comparisons are applied in order to take into account that the iterator order is reversed.

-----

### Class `etl::back_insert_iterator` \[Iterator\]

``` cpp
template <typename Container>
class back_insert_iterator
{
public:
    constexpr back_insert_iterator() noexcept = default;

    constexpr back_insert_iterator(Container& container);

    constexpr back_insert_iterator<Container>& operator=(const typename Container::value_type& value);

    constexpr back_insert_iterator<Container>& operator=(typename Container::value_type&& value);

    constexpr back_insert_iterator<Container>& operator*();

    constexpr back_insert_iterator<Container>& operator++();

    constexpr back_insert_iterator<Container> operator++(int);
};
```

etl::back\_insert\_iterator is a LegacyOutputIterator that appends to a container for which it was constructed. The container’s push\_back() member function is called whenever the iterator (whether dereferenced or not) is assigned to. Incrementing the etl::back\_insert\_iterator is a no-op.

### Constructor `etl::back_insert_iterator::back_insert_iterator`

``` cpp
constexpr back_insert_iterator() noexcept = default;
```

Initializes the underlying pointer to container with nullptr.

-----

### Constructor `etl::back_insert_iterator::back_insert_iterator`

``` cpp
constexpr back_insert_iterator(Container& container);
```

Initializes the underlying pointer to the container to etl::addressof(c).

-----

### Function `etl::back_insert_iterator::operator=`

``` cpp
constexpr back_insert_iterator<Container>& operator=(const typename Container::value_type& value);
```

Inserts the given value value to the container.

-----

### Function `etl::back_insert_iterator::operator=`

``` cpp
constexpr back_insert_iterator<Container>& operator=(typename Container::value_type&& value);
```

Inserts the given value value to the container.

-----

### Function `etl::back_insert_iterator::operator*`

``` cpp
constexpr back_insert_iterator<Container>& operator*();
```

Does nothing, this member function is provided to satisfy the requirements of LegacyOutputIterator. It returns the iterator itself, which makes it possible to use code such as \*iter = value to output (insert) the value into the underlying container.

-----

### Function `etl::back_insert_iterator::operator++`

``` cpp
constexpr back_insert_iterator<Container>& operator++();
```

Does nothing. These operator overloads are provided to satisfy the requirements of LegacyOutputIterator. They make it possible for the expressions \*iter++=value and \*++iter=value to be used to output (insert) a value into the underlying container.

-----

### Function `etl::back_insert_iterator::operator++`

``` cpp
constexpr back_insert_iterator<Container> operator++(int);
```

Does nothing. These operator overloads are provided to satisfy the requirements of LegacyOutputIterator. They make it possible for the expressions \*iter++=value and \*++iter=value to be used to output (insert) a value into the underlying container.

-----

-----

### Function `etl::back_inserter` \[Iterator\]

``` cpp
template <typename Container>
constexpr back_insert_iterator<Container> back_inserter(Container& container);
```

back\_inserter is a convenience function template that constructs a back\_insert\_iterator for the container c with the type deduced from the type of the argument.

-----

### Class `etl::front_insert_iterator` \[Iterator\]

``` cpp
template <typename Container>
class front_insert_iterator
{
public:
    constexpr front_insert_iterator() noexcept = default;

    constexpr front_insert_iterator(Container& container);

    constexpr front_insert_iterator<Container>& operator=(const typename Container::value_type& value);

    constexpr front_insert_iterator<Container>& operator=(typename Container::value_type&& value);

    constexpr front_insert_iterator<Container>& operator*();

    constexpr front_insert_iterator<Container>& operator++();

    constexpr front_insert_iterator<Container> operator++(int);
};
```

front\_insert\_iterator is an LegacyOutputIterator that prepends elements to a container for which it was constructed. The container’s push\_front() member function is called whenever the iterator (whether dereferenced or not) is assigned to. Incrementing the front\_insert\_iterator is a no-op.

\\todo Add tests when a container with push\_front has been implemented.

### Constructor `etl::front_insert_iterator::front_insert_iterator`

``` cpp
constexpr front_insert_iterator() noexcept = default;
```

Initializes the underlying pointer to container with nullptr.

-----

### Constructor `etl::front_insert_iterator::front_insert_iterator`

``` cpp
constexpr front_insert_iterator(Container& container);
```

Initializes the underlying pointer to the container to addressof(c).

-----

### Function `etl::front_insert_iterator::operator=`

``` cpp
constexpr front_insert_iterator<Container>& operator=(const typename Container::value_type& value);
```

Inserts the given value value to the container.

-----

### Function `etl::front_insert_iterator::operator=`

``` cpp
constexpr front_insert_iterator<Container>& operator=(typename Container::value_type&& value);
```

Inserts the given value value to the container.

-----

### Function `etl::front_insert_iterator::operator*`

``` cpp
constexpr front_insert_iterator<Container>& operator*();
```

Does nothing, this member function is provided to satisfy the requirements of LegacyOutputIterator. It returns the iterator itself, which makes it possible to use code such as \*iter = value to output (insert) the value into the underlying container.

-----

### Function `etl::front_insert_iterator::operator++`

``` cpp
constexpr front_insert_iterator<Container>& operator++();
```

Does nothing. These operator overloads are provided to satisfy the requirements of LegacyOutputIterator. They make it possible for the expressions \*iter++=value and \*++iter=value to be used to output (insert) a value into the underlying container.

-----

### Function `etl::front_insert_iterator::operator++`

``` cpp
constexpr front_insert_iterator<Container> operator++(int);
```

Does nothing. These operator overloads are provided to satisfy the requirements of LegacyOutputIterator. They make it possible for the expressions \*iter++=value and \*++iter=value to be used to output (insert) a value into the underlying container.

-----

-----

### Function `etl::front_inserter` \[Iterator\]

``` cpp
template <typename Container>
constexpr front_insert_iterator<Container> front_inserter(Container& c);
```

front\_inserter is a convenience function template that constructs a front\_insert\_iterator for the container c with the type deduced from the type of the argument.

-----
