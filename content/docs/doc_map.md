---
title: "map.hpp"
---

# Header file `map.hpp`

``` cpp
#include "etl/version.hpp"
#include "etl/algorithm.hpp"
#include "etl/cassert.hpp"
#include "etl/cstddef.hpp"
#include "etl/functional.hpp"
#include "etl/set.hpp"
#include "etl/type_traits.hpp"
#include "etl/utility.hpp"

namespace etl
{
    template <typename KeyType, typename ValueType, typename Compare = etl::less<KeyType>>>
    class map_view;

    template <typename KeyT, typename ValueT, etl::size_t Size, typename Compare = etl::less<KeyT>>>
    class map;

    template <typename KeyT, typename ValueT, etl::size_t Capacity, typename Compare = etl::less<KeyT>>>
    struct static_map;
}
```

### Class `etl::map_view` \[Containers\]

``` cpp
template <typename KeyType, typename ValueType, typename Compare = etl::less<KeyType>>>
class map_view
{
public:
    constexpr 'hidden'& at('hidden' const& key);

    constexpr 'hidden'& at('hidden' const& key) const;

    constexpr 'hidden'& operator[]('hidden' const& key);

    constexpr 'hidden' begin() noexcept;

    constexpr 'hidden' begin() const noexcept;

    constexpr 'hidden' cbegin() const noexcept;

    constexpr 'hidden' end() noexcept;

    constexpr 'hidden' end() const noexcept;

    constexpr 'hidden' cend() const noexcept;

    constexpr 'hidden' size() const noexcept;

    constexpr 'hidden' max_size() const noexcept;

    constexpr bool empty() const noexcept;

    constexpr 'hidden' count('hidden' const& key) const noexcept;

    constexpr bool contains('hidden' const& key) const;

    constexpr void clear() noexcept;

    constexpr etl::pair<iterator, bool> insert('hidden' const& value) noexcept;

    template <typename P, int _concept_requires_189 = 42, ::etl::enable_if_t<(_concept_requires_189 == 43) || (is_constructible_v<value_type, P &&>), int> = 0>
    constexpr etl::pair<iterator, bool> insert(P&& value);

    constexpr etl::pair<iterator, bool> insert('hidden'&& value);

    template <typename ... Args>
    constexpr etl::pair<iterator, bool> emplace(Args &&... args);

    constexpr 'hidden' find(KeyType const& key) noexcept;

    constexpr 'hidden' find(KeyType const& key) const noexcept;
};
```

Interface base class for etl::map. Use this class for function parameters. To create an instance, use etl::map.

### Function `etl::map_view::at`

``` cpp
constexpr 'hidden'& at('hidden' const& key);
```

Returns a reference to the mapped value of the element with key equivalent to key. If no such element exists, you are in UB land.

-----

### Function `etl::map_view::at`

``` cpp
constexpr 'hidden'& at('hidden' const& key) const;
```

Returns a reference to the mapped value of the element with key equivalent to key. If no such element exists, you are in UB land.

-----

### Function `etl::map_view::operator[]`

``` cpp
constexpr 'hidden'& operator[]('hidden' const& key);
```

Returns a reference to the value that is mapped to a key equivalent to key, performing an insertion if such key does not already exist.

-----

### Function `etl::map_view::begin`

``` cpp
constexpr 'hidden' begin() noexcept;
```

Returns an iterator to the beginning.

-----

### Function `etl::map_view::begin`

``` cpp
constexpr 'hidden' begin() const noexcept;
```

Returns an const iterator to the beginning.

-----

### Function `etl::map_view::cbegin`

``` cpp
constexpr 'hidden' cbegin() const noexcept;
```

Returns an const iterator to the beginning.

-----

### Function `etl::map_view::end`

``` cpp
constexpr 'hidden' end() noexcept;
```

Returns an iterator to the end.

-----

### Function `etl::map_view::end`

``` cpp
constexpr 'hidden' end() const noexcept;
```

Returns an const iterator to the end.

-----

### Function `etl::map_view::cend`

``` cpp
constexpr 'hidden' cend() const noexcept;
```

Returns an const iterator to the end.

-----

### Function `etl::map_view::size`

``` cpp
constexpr 'hidden' size() const noexcept;
```

Returns the current element count.

-----

### Function `etl::map_view::max_size`

``` cpp
constexpr 'hidden' max_size() const noexcept;
```

Returns the capacity.

-----

### Function `etl::map_view::empty`

``` cpp
constexpr bool empty() const noexcept;
```

Returns true if the size == 0.

-----

### Function `etl::map_view::count`

``` cpp
constexpr 'hidden' count('hidden' const& key) const noexcept;
```

Returns 1 if the key is present, otherwise 0.

-----

### Function `etl::map_view::contains`

``` cpp
constexpr bool contains('hidden' const& key) const;
```

Checks if there is an element with key equivalent to key in the container.

-----

### Function `etl::map_view::clear`

``` cpp
constexpr void clear() noexcept;
```

Erases all elements from the container. After this call, size() returns zero.

-----

### Function `etl::map_view::insert`

``` cpp
constexpr etl::pair<iterator, bool> insert('hidden' const& value) noexcept;
```

Inserts a value pair into the map.

Returns a pair consisting of an iterator to the inserted element (or to the element that prevented the insertion) and a bool denoting whether the insertion took place.

-----

### Function `etl::map_view::insert`

``` cpp
template <typename P, int _concept_requires_189 = 42, ::etl::enable_if_t<(_concept_requires_189 == 43) || (is_constructible_v<value_type, P &&>), int> = 0>
constexpr etl::pair<iterator, bool> insert(P&& value);
```

Inserts a value pair into the map.

Returns a pair consisting of an iterator to the inserted element (or to the element that prevented the insertion) and a bool denoting whether the insertion took place.

-----

### Function `etl::map_view::insert`

``` cpp
constexpr etl::pair<iterator, bool> insert('hidden'&& value);
```

Inserts a value pair into the map.

Returns a pair consisting of an iterator to the inserted element (or to the element that prevented the insertion) and a bool denoting whether the insertion took place.

-----

### Function `etl::map_view::emplace`

``` cpp
template <typename ... Args>
constexpr etl::pair<iterator, bool> emplace(Args &&... args);
```

Inserts a new element into the container constructed in-place with the given args if there is no element with the key in the container.

Careful use of emplace allows the new element to be constructed while avoiding unnecessary copy or move operations. The constructor of the new element (i.e. etl::pair\<Key const, T\>) is called with exactly the same arguments as supplied to emplace, forwarded via etl::forward\<Args\>(args)….

-----

### Function `etl::map_view::find`

``` cpp
constexpr 'hidden' find(KeyType const& key) noexcept;
```

Returns an element with key equivalent to key. Nullptr if not found.

-----

### Function `etl::map_view::find`

``` cpp
constexpr 'hidden' find(KeyType const& key) const noexcept;
```

Returns an element with key equivalent to key. Nullptr if not found.

-----

-----

### Class `etl::map` \[Containers\]

``` cpp
template <typename KeyT, typename ValueT, etl::size_t Size, typename Compare = etl::less<KeyT>>>
class map
: public map_view<KeyT,ValueT,Compare>
{
public:
    constexpr map() noexcept;

    constexpr map(const map<KeyT, ValueT, Size, Compare>& other);

    constexpr map(map<KeyT, ValueT, Size, Compare>&& other) noexcept;

    constexpr map<KeyT, ValueT, Size, Compare>& operator=(const map<KeyT, ValueT, Size, Compare>& other);

    constexpr map<KeyT, ValueT, Size, Compare>& operator=(map<KeyT, ValueT, Size, Compare>&& other) noexcept;

    ~map() noexcept;
};
```
etl::map is a sorted associative container that contains key-value pairs with unique keys. Keys are sorted by using the comparison function Compare. Uses an inline key-value pair array as storage.
Everywhere the standard library uses the Compare requirements, uniqueness is determined by using the equivalence relation. In imprecise terms, two objects a and b are considered equivalent (not unique) if neither compares less than the other: \!comp(a, b) && \!comp(b, a).

### Constructor `etl::map::map`

``` cpp
constexpr map() noexcept;
```

Default constructor.

-----

### Constructor `etl::map::map`

``` cpp
constexpr map(const map<KeyT, ValueT, Size, Compare>& other);
```

Copy constructor. Constructs the container with the copy of the contents of other.

-----

### Constructor `etl::map::map`

``` cpp
constexpr map(map<KeyT, ValueT, Size, Compare>&& other) noexcept;
```
Move constructor. Constructs the container with the contents of other using move semantics. Allocator is obtained by move-construction from the allocator belonging to other. After the move, other is guaranteed to be empty().

-----

### Function `etl::map::operator=`

``` cpp
constexpr map<KeyT, ValueT, Size, Compare>& operator=(const map<KeyT, ValueT, Size, Compare>& other);
```

Replaces the contents of the container. Copy assignment operator. Replaces the contents with a copy of the contents of other.

-----

### Function `etl::map::operator=`

``` cpp
constexpr map<KeyT, ValueT, Size, Compare>& operator=(map<KeyT, ValueT, Size, Compare>&& other) noexcept;
```
Replaces the contents of the container. Move assignment operator. Replaces the contents with those of other using move semantics (i.e. the data in other is moved from other into this container). other is in a valid but unspecified state afterwards.

-----

### Destructor `etl::map::~map`

``` cpp
~map() noexcept;
```

Destructor. Deletes all elements.

-----

-----

### Struct `etl::static_map` \[Containers\]

``` cpp
template <typename KeyT, typename ValueT, etl::size_t Capacity, typename Compare = etl::less<KeyT>>>
struct static_map
{
    struct value_compare;

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

    constexpr 'hidden' size() const noexcept;

    constexpr bool full() const noexcept;

    constexpr 'hidden' max_size() const noexcept;

    constexpr void clear() noexcept;

    template <typename ... Args>
    constexpr pair<etl::static_map::iterator, bool> emplace(Args &&... args);

    constexpr pair<etl::static_map::iterator, bool> insert('hidden' const& value);

    template <typename P, int _concept_requires_538 = 42, ::etl::enable_if_t<(_concept_requires_538 == 43) || (is_convertible_v<value_type, P &&>), int> = 0>
    constexpr pair<etl::static_map::iterator, bool> insert(P&& value);

    constexpr pair<etl::static_map::iterator, bool> insert('hidden'&& value);

    constexpr 'hidden' insert('hidden' hint, 'hidden' const& value);

    constexpr 'hidden' insert('hidden' hint, 'hidden'&& value);

    template <typename InputIter>
    constexpr void insert(InputIter first, InputIter last);
};
```

### Function `etl::static_map::begin`

``` cpp
constexpr 'hidden' begin() noexcept;
```

Returns an iterator to the beginning.

-----

### Function `etl::static_map::begin`

``` cpp
constexpr 'hidden' begin() const noexcept;
```

Returns an const iterator to the beginning.

-----

### Function `etl::static_map::cbegin`

``` cpp
constexpr 'hidden' cbegin() const noexcept;
```

Returns an const iterator to the beginning.

-----

### Function `etl::static_map::end`

``` cpp
constexpr 'hidden' end() noexcept;
```

Returns an iterator to the end.

-----

### Function `etl::static_map::end`

``` cpp
constexpr 'hidden' end() const noexcept;
```

Returns an const iterator to the end.

-----

### Function `etl::static_map::cend`

``` cpp
constexpr 'hidden' cend() const noexcept;
```

Returns an const iterator to the end.

-----

### Function `etl::static_map::rbegin`

``` cpp
constexpr 'hidden' rbegin() noexcept;
```

Returns a reverse iterator to the first element of the reversed map. It corresponds to the last element of the non-reversed map. If the map is empty, the returned iterator is equal to rend().

-----

### Function `etl::static_map::rbegin`

``` cpp
constexpr 'hidden' rbegin() const noexcept;
```

Returns a reverse iterator to the first element of the reversed map. It corresponds to the last element of the non-reversed map. If the map is empty, the returned iterator is equal to rend().

-----

### Function `etl::static_map::crbegin`

``` cpp
constexpr 'hidden' crbegin() const noexcept;
```

Returns a reverse iterator to the first element of the reversed map. It corresponds to the last element of the non-reversed map. If the map is empty, the returned iterator is equal to rend().

-----

### Function `etl::static_map::rend`

``` cpp
constexpr 'hidden' rend() noexcept;
```

Returns a reverse iterator to the element following the last element of the reversed map. It corresponds to the element preceding the first element of the non-reversed map. This element acts as a placeholder, attempting to access it results in undefined behavior.

-----

### Function `etl::static_map::rend`

``` cpp
constexpr 'hidden' rend() const noexcept;
```

Returns a reverse iterator to the element following the last element of the reversed map. It corresponds to the element preceding the first element of the non-reversed map. This element acts as a placeholder, attempting to access it results in undefined behavior.

-----

### Function `etl::static_map::crend`

``` cpp
constexpr 'hidden' crend() const noexcept;
```

Returns a reverse iterator to the element following the last element of the reversed map. It corresponds to the element preceding the first element of the non-reversed map. This element acts as a placeholder, attempting to access it results in undefined behavior.

-----

### Function `etl::static_map::empty`

``` cpp
constexpr bool empty() const noexcept;
```

Checks if the container has no elements.

-----

### Function `etl::static_map::size`

``` cpp
constexpr 'hidden' size() const noexcept;
```

Returns the number of elements in the container.

-----

### Function `etl::static_map::full`

``` cpp
constexpr bool full() const noexcept;
```

Checks if the container full, i.e. whether size() == Capacity.

-----

### Function `etl::static_map::max_size`

``` cpp
constexpr 'hidden' max_size() const noexcept;
```

Returns the maximum number of elements the container is able to hold, i.e. max\_size() == Capacity.

-----

### Function `etl::static_map::clear`

``` cpp
constexpr void clear() noexcept;
```

Erases all elements from the container. After this call, size() returns zero. Invalidates any references, pointers, or iterators referring to contained elements. Any past-the-end iterator remains valid.

-----

### Function `etl::static_map::emplace`

``` cpp
template <typename ... Args>
constexpr pair<etl::static_map::iterator, bool> emplace(Args &&... args);
```

Inserts a new element into the container constructed in-place with the given args if there is no element with the key in the container.

-----

### Function `etl::static_map::insert`

``` cpp
constexpr pair<etl::static_map::iterator, bool> insert('hidden' const& value);
```

Inserts element(s) into the container, if the container doesn’t already contain an element with an equivalent key.

-----

### Function `etl::static_map::insert`

``` cpp
template <typename P, int _concept_requires_538 = 42, ::etl::enable_if_t<(_concept_requires_538 == 43) || (is_convertible_v<value_type, P &&>), int> = 0>
constexpr pair<etl::static_map::iterator, bool> insert(P&& value);
```

Inserts element(s) into the container, if the container doesn’t already contain an element with an equivalent key.

-----

### Function `etl::static_map::insert`

``` cpp
constexpr pair<etl::static_map::iterator, bool> insert('hidden'&& value);
```

Inserts element(s) into the container, if the container doesn’t already contain an element with an equivalent key.

-----

### Function `etl::static_map::insert`

``` cpp
constexpr 'hidden' insert('hidden' hint, 'hidden' const& value);
```

Inserts element(s) into the container, if the container doesn’t already contain an element with an equivalent key.

-----

### Function `etl::static_map::insert`

``` cpp
constexpr 'hidden' insert('hidden' hint, 'hidden'&& value);
```

Inserts element(s) into the container, if the container doesn’t already contain an element with an equivalent key.

-----

### Function `etl::static_map::insert`

``` cpp
template <typename InputIter>
constexpr void insert(InputIter first, InputIter last);
```

Inserts element(s) into the container, if the container doesn’t already contain an element with an equivalent key.

-----

-----
