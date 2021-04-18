---
title: "set.hpp"
---

# Header file `set.hpp`

``` cpp
#include "etl/version.hpp"
#include "etl/algorithm.hpp"
#include "etl/functional.hpp"
#include "etl/iterator.hpp"
#include "etl/utility.hpp"
#include "etl/vector.hpp"

namespace etl
{
    template <typename Key, etl::size_t Capacity, typename Compare = less<Key>>>
    struct static_set;

    template <typename Key, etl::size_t Capacity, typename Comp>
    constexpr bool operator==(static_set<Key, Capacity, Comp> const& lhs, static_set<Key, Capacity, Comp> const& rhs);

    template <typename Key, etl::size_t Capacity, typename Comp>
    constexpr bool operator!=(static_set<Key, Capacity, Comp> const& lhs, static_set<Key, Capacity, Comp> const& rhs);

    template <typename Key, etl::size_t Capacity, typename Comp>
    constexpr bool operator<(static_set<Key, Capacity, Comp> const& lhs, static_set<Key, Capacity, Comp> const& rhs);

    template <typename Key, etl::size_t Capacity, typename Comp>
    constexpr bool operator<=(static_set<Key, Capacity, Comp> const& lhs, static_set<Key, Capacity, Comp> const& rhs);

    template <typename Key, etl::size_t Capacity, typename Comp>
    constexpr bool operator>(static_set<Key, Capacity, Comp> const& lhs, static_set<Key, Capacity, Comp> const& rhs);

    template <typename Key, etl::size_t Capacity, typename Comp>
    constexpr bool operator>=(static_set<Key, Capacity, Comp> const& lhs, static_set<Key, Capacity, Comp> const& rhs);

    template <typename Key, etl::size_t Capacity, typename Compare>
    constexpr void swap(static_set<Key, Capacity, Compare>& lhs, static_set<Key, Capacity, Compare>& rhs) noexcept('hidden');
}
```

### Struct `etl::static_set` \[Containers\]

``` cpp
template <typename Key, etl::size_t Capacity, typename Compare = less<Key>>>
struct static_set
{
    static_set() = default;

    template <typename InputIt, int _concept_requires_82 = 42, ::etl::enable_if_t<(_concept_requires_82 == 43) || (detail::InputIterator<InputIt>), int> = 0>
    static_set(InputIt first, InputIt last);

    constexpr static_set(const static_set<Key, Capacity, Compare>& other) = default;

    constexpr static_set(static_set<Key, Capacity, Compare>&& other) noexcept('hidden') = default;

    constexpr static_set<Key, Capacity, Compare>& operator=(const static_set<Key, Capacity, Compare>& other) = default;

    constexpr static_set<Key, Capacity, Compare>& operator=(static_set<Key, Capacity, Compare>&& other) noexcept('hidden') = default;

    constexpr 'hidden' begin() noexcept;

    constexpr 'hidden' begin() const noexcept;

    constexpr 'hidden' cbegin() const noexcept;

    constexpr 'hidden' end() noexcept;

    constexpr 'hidden' end() const noexcept;

    constexpr 'hidden' cend() const noexcept;

    constexpr 'hidden' rbegin() noexcept;

    constexpr 'hidden' rbegin() const noexcept;

    constexpr 'hidden' crbegin() const noexcept;

    constexpr 'hidden' rend() noexcept;

    constexpr 'hidden' rend() const noexcept;

    constexpr 'hidden' crend() const noexcept;

    constexpr bool empty() const noexcept;

    constexpr bool full() const noexcept;

    constexpr 'hidden' size() const noexcept;

    constexpr 'hidden' max_size() const noexcept;

    constexpr void clear() noexcept;

    constexpr enable_if_t<is_move_constructible_v<etl::static_set::value_type>, pair<etl::static_set::iterator, bool>> insert('hidden'&& value);

    constexpr enable_if_t<is_copy_constructible_v<etl::static_set::value_type>, pair<etl::static_set::iterator, bool>> insert('hidden' const& value);

    template <typename InputIter, int _concept_requires_261 = 42, ::etl::enable_if_t<(_concept_requires_261 == 43) || (detail::InputIterator<InputIter>), int> = 0>
    constexpr void insert(InputIter first, InputIter last) noexcept('hidden');

    template <typename ... Args, int _concept_requires_271 = 42, ::etl::enable_if_t<(_concept_requires_271 == 43) || (is_copy_constructible_v<key_type>), int> = 0>
    constexpr pair<etl::static_set::iterator, bool> emplace(Args &&... args) noexcept('hidden');

    constexpr 'hidden' erase('hidden' pos) noexcept;

    constexpr 'hidden' erase('hidden' first, 'hidden' last);

    constexpr 'hidden' erase('hidden' const& key) noexcept;

    constexpr enable_if_t<is_assignable_v<etl::static_set::key_type &, etl::static_set::key_type &&>, void> swap(static_set<Key, Capacity, Compare>& other) noexcept('hidden');

    constexpr 'hidden' count('hidden' const& key) const noexcept;

    template <typename K, int _concept_requires_343 = 42, ::etl::enable_if_t<(_concept_requires_343 == 43) || (detail::transparent_v<key_compare, K>), int> = 0>
    constexpr 'hidden' count(K const& x) const;

    constexpr 'hidden' find('hidden' const& key) noexcept;

    constexpr 'hidden' find('hidden' const& key) const noexcept;

    template <typename K, int _concept_requires_369 = 42, ::etl::enable_if_t<(_concept_requires_369 == 43) || (detail::transparent_v<key_compare, K>), int> = 0>
    constexpr 'hidden' find(K const& x);

    template <typename K, int _concept_requires_379 = 42, ::etl::enable_if_t<(_concept_requires_379 == 43) || (detail::transparent_v<key_compare, K>), int> = 0>
    constexpr 'hidden' find(K const& x) const;

    constexpr bool contains('hidden' const& key) const noexcept;

    template <typename K, int _concept_requires_398 = 42, ::etl::enable_if_t<(_concept_requires_398 == 43) || (detail::transparent_v<key_compare, K>), int> = 0>
    constexpr bool contains(K const& x) const;

    constexpr 'hidden' lower_bound('hidden' const& key);

    constexpr 'hidden' lower_bound('hidden' const& key) const;

    template <typename K, int _concept_requires_421 = 42, ::etl::enable_if_t<(_concept_requires_421 == 43) || (detail::transparent_v<key_compare, K>), int> = 0>
    constexpr 'hidden' lower_bound(K const& key);

    template <typename K, int _concept_requires_429 = 42, ::etl::enable_if_t<(_concept_requires_429 == 43) || (detail::transparent_v<key_compare, K>), int> = 0>
    constexpr 'hidden' lower_bound(K const& key) const;

    constexpr 'hidden' upper_bound('hidden' const& key);

    constexpr 'hidden' upper_bound('hidden' const& key) const;

    template <typename K, int _concept_requires_452 = 42, ::etl::enable_if_t<(_concept_requires_452 == 43) || (detail::transparent_v<key_compare, K>), int> = 0>
    constexpr 'hidden' upper_bound(K const& key);

    template <typename K, int _concept_requires_460 = 42, ::etl::enable_if_t<(_concept_requires_460 == 43) || (detail::transparent_v<key_compare, K>), int> = 0>
    constexpr 'hidden' upper_bound(K const& key) const;

    constexpr 'hidden' equal_range('hidden' const& key);

    constexpr 'hidden' equal_range('hidden' const& key) const;

    template <typename K, int _concept_requires_492 = 42, ::etl::enable_if_t<(_concept_requires_492 == 43) || (detail::transparent_v<key_compare, K>), int> = 0>
    constexpr 'hidden' equal_range(K const& key);

    template <typename K, int _concept_requires_503 = 42, ::etl::enable_if_t<(_concept_requires_503 == 43) || (detail::transparent_v<key_compare, K>), int> = 0>
    constexpr 'hidden' equal_range(K const& key) const;

    'hidden' key_comp() const noexcept;

    'hidden' value_comp() const noexcept;
};
```
static\_set is an associative container that contains a sorted set of unique objects of type Key. Sorting is done using the key comparison function Compare.

### Constructor `etl::static_set::static_set`

``` cpp
static_set() = default;
```

Constructs empty container.

-----

### Constructor `etl::static_set::static_set`

``` cpp
template <typename InputIt, int _concept_requires_82 = 42, ::etl::enable_if_t<(_concept_requires_82 == 43) || (detail::InputIterator<InputIt>), int> = 0>
static_set(InputIt first, InputIt last);
```

Constructs with the contents of the range \[first, last). If multiple elements in the range have keys that compare equivalent, all but the first will be discarded.

\\todo Fix noexcept. Maybe: noexcept(noexcept(insert(first, last)))

-----

### Constructor `etl::static_set::static_set`

``` cpp
constexpr static_set(const static_set<Key, Capacity, Compare>& other) = default;
```

-----

### Constructor `etl::static_set::static_set`

``` cpp
constexpr static_set(static_set<Key, Capacity, Compare>&& other) noexcept('hidden') = default;
```

-----

### Function `etl::static_set::operator=`

``` cpp
constexpr static_set<Key, Capacity, Compare>& operator=(const static_set<Key, Capacity, Compare>& other) = default;
```

-----

### Function `etl::static_set::operator=`

``` cpp
constexpr static_set<Key, Capacity, Compare>& operator=(static_set<Key, Capacity, Compare>&& other) noexcept('hidden') = default;
```

-----

### Function `etl::static_set::begin`

``` cpp
constexpr 'hidden' begin() noexcept;
```

Returns an iterator to the first element of the set.

-----

### Function `etl::static_set::begin`

``` cpp
constexpr 'hidden' begin() const noexcept;
```

Returns an iterator to the first element of the set.

-----

### Function `etl::static_set::cbegin`

``` cpp
constexpr 'hidden' cbegin() const noexcept;
```

Returns an iterator to the first element of the set.

-----

### Function `etl::static_set::end`

``` cpp
constexpr 'hidden' end() noexcept;
```

Returns an iterator to the element following the last element of the set.

-----

### Function `etl::static_set::end`

``` cpp
constexpr 'hidden' end() const noexcept;
```

Returns an iterator to the element following the last element of the set.

-----

### Function `etl::static_set::cend`

``` cpp
constexpr 'hidden' cend() const noexcept;
```

Returns an iterator to the element following the last element of the set.

-----

### Function `etl::static_set::rbegin`

``` cpp
constexpr 'hidden' rbegin() noexcept;
```

Returns a reverse iterator to the first element of the reversed set. It corresponds to the last element of the non-reversed set.

-----

### Function `etl::static_set::rbegin`

``` cpp
constexpr 'hidden' rbegin() const noexcept;
```

Returns a reverse iterator to the first element of the reversed set. It corresponds to the last element of the non-reversed set.

-----

### Function `etl::static_set::crbegin`

``` cpp
constexpr 'hidden' crbegin() const noexcept;
```

Returns a reverse iterator to the first element of the reversed set. It corresponds to the last element of the non-reversed set.

-----

### Function `etl::static_set::rend`

``` cpp
constexpr 'hidden' rend() noexcept;
```

Returns a reverse iterator to the element following the last element of the reversed set. It corresponds to the element preceding the first element of the non-reversed set.

-----

### Function `etl::static_set::rend`

``` cpp
constexpr 'hidden' rend() const noexcept;
```

Returns a reverse iterator to the element following the last element of the reversed set. It corresponds to the element preceding the first element of the non-reversed set.

-----

### Function `etl::static_set::crend`

``` cpp
constexpr 'hidden' crend() const noexcept;
```

Returns a reverse iterator to the element following the last element of the reversed set. It corresponds to the element preceding the first element of the non-reversed set.

-----

### Function `etl::static_set::empty`

``` cpp
constexpr bool empty() const noexcept;
```

Checks if the container has no elements, i.e. whether begin() == end().

-----

### Function `etl::static_set::full`

``` cpp
constexpr bool full() const noexcept;
```

Checks if the container full, i.e. whether size() == Capacity.

-----

### Function `etl::static_set::size`

``` cpp
constexpr 'hidden' size() const noexcept;
```

Returns the number of elements in the container, i.e. distance(begin(), end()).

-----

### Function `etl::static_set::max_size`

``` cpp
constexpr 'hidden' max_size() const noexcept;
```

Returns the maximum number of elements the container is able to hold.

-----

### Function `etl::static_set::clear`

``` cpp
constexpr void clear() noexcept;
```

Erases all elements from the container. After this call, size() returns zero.

-----

### Function `etl::static_set::insert`

``` cpp
constexpr enable_if_t<is_move_constructible_v<etl::static_set::value_type>, pair<etl::static_set::iterator, bool>> insert('hidden'&& value);
```

Inserts element into the container, if the container doesn’t already contain an element with an equivalent key.

-----

### Function `etl::static_set::insert`

``` cpp
constexpr enable_if_t<is_copy_constructible_v<etl::static_set::value_type>, pair<etl::static_set::iterator, bool>> insert('hidden' const& value);
```

Inserts element into the container, if the container doesn’t already contain an element with an equivalent key.

\\todo noexcept(noexcept(base\_type::insert(move(declval\<key\_type\>())))) breaks GCC 9.3 Ubuntu Focal build

-----

### Function `etl::static_set::insert`

``` cpp
template <typename InputIter, int _concept_requires_261 = 42, ::etl::enable_if_t<(_concept_requires_261 == 43) || (detail::InputIterator<InputIter>), int> = 0>
constexpr void insert(InputIter first, InputIter last) noexcept('hidden');
```

Inserts elements from range \[first, last). If multiple elements in the range have keys that compare equivalent, it is unspecified which element is inserted (pending LWG2844).

-----

### Function `etl::static_set::emplace`

``` cpp
template <typename ... Args, int _concept_requires_271 = 42, ::etl::enable_if_t<(_concept_requires_271 == 43) || (is_copy_constructible_v<key_type>), int> = 0>
constexpr pair<etl::static_set::iterator, bool> emplace(Args &&... args) noexcept('hidden');
```

Inserts a new element into the container constructed in-place with the given args if there is no element with the key in the container.

-----

### Function `etl::static_set::erase`

``` cpp
constexpr 'hidden' erase('hidden' pos) noexcept;
```

Removes the element at pos.

*Notes:* [cppreference.com/w/cpp/container/set/erase](https://en.cppreference.com/w/cpp/container/set/erase)

*Return values:* Iterator following the last removed element.

-----

### Function `etl::static_set::erase`

``` cpp
constexpr 'hidden' erase('hidden' first, 'hidden' last);
```

Removes the elements in the range \[first; last), which must be a valid range in \*this.

*Notes:* [cppreference.com/w/cpp/container/set/erase](https://en.cppreference.com/w/cpp/container/set/erase)

*Return values:* Iterator following the last removed element.

-----

### Function `etl::static_set::erase`

``` cpp
constexpr 'hidden' erase('hidden' const& key) noexcept;
```

Removes the element (if one exists) with the key equivalent to key.

*Notes:* [cppreference.com/w/cpp/container/set/erase](https://en.cppreference.com/w/cpp/container/set/erase)

*Return values:* Number of elements removed.

-----

### Function `etl::static_set::swap`

``` cpp
constexpr enable_if_t<is_assignable_v<etl::static_set::key_type &, etl::static_set::key_type &&>, void> swap(static_set<Key, Capacity, Compare>& other) noexcept('hidden');
```

Exchanges the contents of the container with those of other.

-----

### Function `etl::static_set::count`

``` cpp
constexpr 'hidden' count('hidden' const& key) const noexcept;
```

Returns the number of elements with key that compares equivalent to the specified argument, which is either 1 or 0 since this container does not allow duplicates.

-----

### Function `etl::static_set::count`

``` cpp
template <typename K, int _concept_requires_343 = 42, ::etl::enable_if_t<(_concept_requires_343 == 43) || (detail::transparent_v<key_compare, K>), int> = 0>
constexpr 'hidden' count(K const& x) const;
```

Returns the number of elements with key that compares equivalent to the value x.

-----

### Function `etl::static_set::find`

``` cpp
constexpr 'hidden' find('hidden' const& key) noexcept;
```

Finds an element with key equivalent to key.

*Return values:* Iterator to an element with key equivalent to key. If no such element is found, past-the-end (see end()) iterator is returned.

-----

### Function `etl::static_set::find`

``` cpp
constexpr 'hidden' find('hidden' const& key) const noexcept;
```

Finds an element with key equivalent to key.

*Return values:* Iterator to an element with key equivalent to key. If no such element is found, past-the-end (see end()) iterator is returned.

-----

### Function `etl::static_set::find`

``` cpp
template <typename K, int _concept_requires_369 = 42, ::etl::enable_if_t<(_concept_requires_369 == 43) || (detail::transparent_v<key_compare, K>), int> = 0>
constexpr 'hidden' find(K const& x);
```

Finds an element with key that compares equivalent to the value x.

-----

### Function `etl::static_set::find`

``` cpp
template <typename K, int _concept_requires_379 = 42, ::etl::enable_if_t<(_concept_requires_379 == 43) || (detail::transparent_v<key_compare, K>), int> = 0>
constexpr 'hidden' find(K const& x) const;
```

Finds an element with key that compares equivalent to the value x.

-----

### Function `etl::static_set::contains`

``` cpp
constexpr bool contains('hidden' const& key) const noexcept;
```

Checks if there is an element with key equivalent to key in the container.

-----

### Function `etl::static_set::contains`

``` cpp
template <typename K, int _concept_requires_398 = 42, ::etl::enable_if_t<(_concept_requires_398 == 43) || (detail::transparent_v<key_compare, K>), int> = 0>
constexpr bool contains(K const& x) const;
```

Checks if there is an element with key that compares equivalent to the value x.

-----

### Function `etl::static_set::lower_bound`

``` cpp
constexpr 'hidden' lower_bound('hidden' const& key);
```

Returns an iterator pointing to the first element that is not less than (i.e. greater or equal to) key.

-----

### Function `etl::static_set::lower_bound`

``` cpp
constexpr 'hidden' lower_bound('hidden' const& key) const;
```

Returns an iterator pointing to the first element that is not less than (i.e. greater or equal to) key.

-----

### Function `etl::static_set::lower_bound`

``` cpp
template <typename K, int _concept_requires_421 = 42, ::etl::enable_if_t<(_concept_requires_421 == 43) || (detail::transparent_v<key_compare, K>), int> = 0>
constexpr 'hidden' lower_bound(K const& key);
```

Returns an iterator pointing to the first element that is not less than (i.e. greater or equal to) key.

-----

### Function `etl::static_set::lower_bound`

``` cpp
template <typename K, int _concept_requires_429 = 42, ::etl::enable_if_t<(_concept_requires_429 == 43) || (detail::transparent_v<key_compare, K>), int> = 0>
constexpr 'hidden' lower_bound(K const& key) const;
```

Returns an iterator pointing to the first element that is not less than (i.e. greater or equal to) key.

-----

### Function `etl::static_set::upper_bound`

``` cpp
constexpr 'hidden' upper_bound('hidden' const& key);
```

Returns an iterator pointing to the first element that is greater than key.

-----

### Function `etl::static_set::upper_bound`

``` cpp
constexpr 'hidden' upper_bound('hidden' const& key) const;
```

Returns an iterator pointing to the first element that is greater than key.

-----

### Function `etl::static_set::upper_bound`

``` cpp
template <typename K, int _concept_requires_452 = 42, ::etl::enable_if_t<(_concept_requires_452 == 43) || (detail::transparent_v<key_compare, K>), int> = 0>
constexpr 'hidden' upper_bound(K const& key);
```

Returns an iterator pointing to the first element that is greater than key.

-----

### Function `etl::static_set::upper_bound`

``` cpp
template <typename K, int _concept_requires_460 = 42, ::etl::enable_if_t<(_concept_requires_460 == 43) || (detail::transparent_v<key_compare, K>), int> = 0>
constexpr 'hidden' upper_bound(K const& key) const;
```

Returns an iterator pointing to the first element that is greater than key.

-----

### Function `etl::static_set::equal_range`

``` cpp
constexpr 'hidden' equal_range('hidden' const& key);
```

Returns a range containing all elements with the given key in the container. The range is defined by two iterators, one pointing to the first element that is not less than key and another pointing to the first element greater than key. Alternatively, the first iterator may be obtained with lower\_bound(), and the second with upper\_bound().

-----

### Function `etl::static_set::equal_range`

``` cpp
constexpr 'hidden' equal_range('hidden' const& key) const;
```

Returns a range containing all elements with the given key in the container. The range is defined by two iterators, one pointing to the first element that is not less than key and another pointing to the first element greater than key. Alternatively, the first iterator may be obtained with lower\_bound(), and the second with upper\_bound().

-----

### Function `etl::static_set::equal_range`

``` cpp
template <typename K, int _concept_requires_492 = 42, ::etl::enable_if_t<(_concept_requires_492 == 43) || (detail::transparent_v<key_compare, K>), int> = 0>
constexpr 'hidden' equal_range(K const& key);
```

Returns a range containing all elements with the given key in the container. The range is defined by two iterators, one pointing to the first element that is not less than key and another pointing to the first element greater than key. Alternatively, the first iterator may be obtained with lower\_bound(), and the second with upper\_bound().

-----

### Function `etl::static_set::equal_range`

``` cpp
template <typename K, int _concept_requires_503 = 42, ::etl::enable_if_t<(_concept_requires_503 == 43) || (detail::transparent_v<key_compare, K>), int> = 0>
constexpr 'hidden' equal_range(K const& key) const;
```

Returns a range containing all elements with the given key in the container. The range is defined by two iterators, one pointing to the first element that is not less than key and another pointing to the first element greater than key. Alternatively, the first iterator may be obtained with lower\_bound(), and the second with upper\_bound().

-----

### Function `etl::static_set::key_comp`

``` cpp
'hidden' key_comp() const noexcept;
```

Returns the function object that compares the keys, which is a copy of this container’s constructor argument comp. It is the same as value\_comp.

*Return values:* The key comparison function object.

-----

### Function `etl::static_set::value_comp`

``` cpp
'hidden' value_comp() const noexcept;
```

Returns the function object that compares the values. It is the same as key\_comp.

*Return values:* The value comparison function object.

-----

-----

### Function `etl::operator==`

``` cpp
template <typename Key, etl::size_t Capacity, typename Comp>
constexpr bool operator==(static_set<Key, Capacity, Comp> const& lhs, static_set<Key, Capacity, Comp> const& rhs);
```

Compares the contents of two sets.

Checks if the contents of lhs and rhs are equal, that is, they have the same number of elements and each element in lhs compares equal with the element in rhs at the same position.

-----

### Function `etl::operator!=`

``` cpp
template <typename Key, etl::size_t Capacity, typename Comp>
constexpr bool operator!=(static_set<Key, Capacity, Comp> const& lhs, static_set<Key, Capacity, Comp> const& rhs);
```

Compares the contents of two sets.

Checks if the contents of lhs and rhs are equal, that is, they have the same number of elements and each element in lhs compares equal with the element in rhs at the same position.

-----

### Function `etl::operator<`

``` cpp
template <typename Key, etl::size_t Capacity, typename Comp>
constexpr bool operator<(static_set<Key, Capacity, Comp> const& lhs, static_set<Key, Capacity, Comp> const& rhs);
```

Compares the contents of two sets.

Compares the contents of lhs and rhs lexicographically. The comparison is performed by a function equivalent to lexicographical\_compare. This comparison ignores the set’s ordering Compare.

-----

### Function `etl::operator<=`

``` cpp
template <typename Key, etl::size_t Capacity, typename Comp>
constexpr bool operator<=(static_set<Key, Capacity, Comp> const& lhs, static_set<Key, Capacity, Comp> const& rhs);
```

Compares the contents of two sets.

Compares the contents of lhs and rhs lexicographically. The comparison is performed by a function equivalent to lexicographical\_compare. This comparison ignores the set’s ordering Compare.

-----

### Function `etl::operator>`

``` cpp
template <typename Key, etl::size_t Capacity, typename Comp>
constexpr bool operator>(static_set<Key, Capacity, Comp> const& lhs, static_set<Key, Capacity, Comp> const& rhs);
```

Compares the contents of two sets.

Compares the contents of lhs and rhs lexicographically. The comparison is performed by a function equivalent to lexicographical\_compare. This comparison ignores the set’s ordering Compare.

-----

### Function `etl::operator>=`

``` cpp
template <typename Key, etl::size_t Capacity, typename Comp>
constexpr bool operator>=(static_set<Key, Capacity, Comp> const& lhs, static_set<Key, Capacity, Comp> const& rhs);
```

Compares the contents of two sets.

Compares the contents of lhs and rhs lexicographically. The comparison is performed by a function equivalent to lexicographical\_compare. This comparison ignores the set’s ordering Compare.

-----

### Function `etl::swap`

``` cpp
template <typename Key, etl::size_t Capacity, typename Compare>
constexpr void swap(static_set<Key, Capacity, Compare>& lhs, static_set<Key, Capacity, Compare>& rhs) noexcept('hidden');
```

Specializes the swap algorithm for set. Swaps the contents of lhs and rhs. Calls lhs.swap(rhs).

-----
