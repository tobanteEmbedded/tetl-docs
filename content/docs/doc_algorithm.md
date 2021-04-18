---
title: "algorithm.hpp"
---

# Header file `algorithm.hpp`

``` cpp
#include "etl/version.hpp"
#include "etl/cassert.hpp"
#include "etl/cstddef.hpp"
#include "etl/functional.hpp"
#include "etl/iterator.hpp"
#include "etl/type_traits.hpp"

namespace etl
{
    template <typename ForwardIt1, typename ForwardIt2>
    constexpr void iter_swap(ForwardIt1 a, ForwardIt2 b);

    template <typename ForwardIt1, typename ForwardIt2>
    constexpr ForwardIt2 swap_ranges(ForwardIt1 first1, ForwardIt1 last1, ForwardIt2 first2);

    template <typename InputIt, typename OutputIt>
    constexpr OutputIt move(InputIt first, InputIt last, OutputIt destination);

    template <typename BidirIt1, typename BidirIt2>
    constexpr BidirIt2 move_backward(BidirIt1 first, BidirIt1 last, BidirIt2 destination);

    template <typename InputIt, typename UnaryFunc>
    constexpr UnaryFunc for_each(InputIt first, InputIt last, UnaryFunc f) noexcept;

    template <typename InputIt, typename Size, typename UnaryFunc>
    constexpr InputIt for_each_n(InputIt first, Size n, UnaryFunc f) noexcept;

    //=== transform ===//
    template <typename InputIt, typename OutputIt, typename UnaryOp>
    constexpr OutputIt transform(InputIt first, InputIt last, OutputIt dest, UnaryOp op);
    template <typename InputIt1, typename InputIt2, typename OutputIt, typename BinaryOp>
    constexpr OutputIt transform(InputIt1 first1, InputIt1 last1, InputIt2 first2, OutputIt dest, BinaryOp op);

    template <typename ForwardIt, typename Generator>
    constexpr void generate(ForwardIt first, ForwardIt last, Generator g);

    template <typename OutputIt, typename SizeT, typename Generator>
    constexpr OutputIt generate_n(OutputIt first, SizeT count, Generator g);

    //=== count ===//
    template <typename InputIt, typename T>
    constexpr typename iterator_traits<InputIt>::difference_type count(InputIt first, InputIt last, T const& value);
    template <typename InputIt, typename Predicate>
    constexpr typename iterator_traits<InputIt>::difference_type count_if(InputIt first, InputIt last, Predicate p);

    //=== mismatch ===//
    template <typename InputIt1, typename InputIt2, typename Predicate>
    constexpr pair<InputIt1, InputIt2> mismatch(InputIt1 first1, InputIt1 last1, InputIt2 first2, Predicate pred);
    template <typename InputIt1, typename InputIt2>
    constexpr pair<InputIt1, InputIt2> mismatch(InputIt1 first1, InputIt1 last1, InputIt2 first2);
    template <typename InputIt1, typename InputIt2, typename Predicate>
    constexpr pair<InputIt1, InputIt2> mismatch(InputIt1 first1, InputIt1 last1, InputIt2 first2, InputIt2 last2, Predicate pred);
    template <typename InputIt1, typename InputIt2>
    constexpr pair<InputIt1, InputIt2> mismatch(InputIt1 first1, InputIt1 last1, InputIt2 first2, InputIt2 last2);

    //=== adjacent_find ===//
    template <typename ForwardIt, typename Predicate>
    constexpr ForwardIt adjacent_find(ForwardIt first, ForwardIt last, Predicate pred);
    template <typename ForwardIt>
    constexpr ForwardIt adjacent_find(ForwardIt first, ForwardIt last);

    //=== find ===//
    template <typename InputIt, typename T>
    constexpr InputIt find(InputIt first, InputIt last, T const& value) noexcept;

    //=== find_if ===//
    template <typename InputIt, typename Predicate>
    constexpr InputIt find_if(InputIt first, InputIt last, Predicate pred) noexcept;

    //=== find_if_not ===//
    template <typename InputIt, typename Predicate>
    constexpr InputIt find_if_not(InputIt first, InputIt last, Predicate pred) noexcept;

    //=== find_first_of ===//
    template <typename InputIt, typename ForwardIt, typename Predicate>
    constexpr InputIt find_first_of(InputIt first, InputIt last, ForwardIt sFirst, ForwardIt sLast, Predicate pred);
    template <typename InputIt, typename ForwardIt>
    constexpr InputIt find_first_of(InputIt first, InputIt last, ForwardIt sFirst, ForwardIt sLast);

    //=== search ===//
    template <typename ForwardIt1, typename ForwardIt2, typename Predicate>
    constexpr ForwardIt1 search(ForwardIt1 first, ForwardIt1 last, ForwardIt2 sFirst, ForwardIt2 sLast, Predicate pred);
    template <typename ForwardIt1, typename ForwardIt2>
    constexpr ForwardIt1 search(ForwardIt1 first, ForwardIt1 last, ForwardIt2 sFirst, ForwardIt2 sLast);
    template <typename ForwardIt, typename Searcher>
    constexpr ForwardIt search(ForwardIt first, ForwardIt last, Searcher const& searcher);

    //=== search_n ===//
    template <typename ForwardIt, typename Size, typename ValueT, typename Predicate>
    constexpr ForwardIt search_n(ForwardIt first, ForwardIt last, Size count, ValueT const& value, Predicate pred);
    template <typename ForwardIt, typename Size, typename ValueT>
    constexpr ForwardIt search_n(ForwardIt first, ForwardIt last, Size count, ValueT const& value);

    //=== find_end ===//
    template <typename ForwardIt1, typename ForwardIt2, typename Predicate>
    constexpr ForwardIt1 find_end(ForwardIt1 first, ForwardIt1 last, ForwardIt2 sFirst, ForwardIt2 sLast, Predicate p);
    template <typename ForwardIt1, typename ForwardIt2>
    constexpr ForwardIt1 find_end(ForwardIt1 first, ForwardIt1 last, ForwardIt2 sFirst, ForwardIt2 sLast);

    //=== remove_if ===//
    template <typename ForwardIt, typename Predicate>
    constexpr ForwardIt remove_if(ForwardIt first, ForwardIt last, Predicate pred);

    //=== remove ===//
    template <typename ForwardIt, typename T>
    constexpr ForwardIt remove(ForwardIt first, ForwardIt last, T const& value);

    //=== remove_copy ===//
    template <typename InputIt, typename OutputIt, typename Predicate>
    constexpr OutputIt remove_copy_if(InputIt first, InputIt last, OutputIt destination, Predicate p);
    template <typename InputIt, typename OutputIt, typename T>
    constexpr OutputIt remove_copy(InputIt first, InputIt last, OutputIt destination, T const& value);

    //=== replace ===//
    template <typename ForwardIt, typename Predicate, typename T>
    constexpr void replace_if(ForwardIt first, ForwardIt last, Predicate p, T const& newValue);
    template <typename ForwardIt, typename T>
    constexpr void replace(ForwardIt first, ForwardIt last, T const& oldValue, T const& newValue);

    //=== max ===//
    template <typename Type>
    constexpr Type const& max(Type const& a, Type const& b) noexcept;
    template <typename Type, typename Compare>
    constexpr Type const& max(Type const& a, Type const& b, Compare comp) noexcept;

    //=== max_element ===//
    template <typename ForwardIt>
    constexpr ForwardIt max_element(ForwardIt first, ForwardIt last) noexcept;
    template <typename ForwardIt, typename Compare>
    constexpr ForwardIt max_element(ForwardIt first, ForwardIt last, Compare comp);

    //=== min ===//
    template <typename Type>
    constexpr Type const& min(Type const& a, Type const& b) noexcept;
    template <typename Type, typename Compare>
    constexpr Type const& min(Type const& a, Type const& b, Compare comp) noexcept;

    //=== min_element ===//
    template <typename ForwardIt>
    constexpr ForwardIt min_element(ForwardIt first, ForwardIt last) noexcept;
    template <typename ForwardIt, typename Compare>
    constexpr ForwardIt min_element(ForwardIt first, ForwardIt last, Compare comp);

    //=== minmax ===//
    template <typename T, typename Compare>
    constexpr pair<const T &, const T &> minmax(T const& a, T const& b, Compare comp);
    template <typename T>
    constexpr pair<const T &, const T &> minmax(T const& a, T const& b);

    //=== minmax_element ===//
    template <typename ForwardIt, typename Compare>
    constexpr pair<ForwardIt, ForwardIt> minmax_element(ForwardIt first, ForwardIt last, Compare comp);
    template <typename ForwardIt>
    constexpr pair<ForwardIt, ForwardIt> minmax_element(ForwardIt first, ForwardIt last);

    template <typename InputIt, typename Predicate>
    constexpr bool all_of(InputIt first, InputIt last, Predicate p);

    template <typename InputIt, typename Predicate>
    constexpr bool any_of(InputIt first, InputIt last, Predicate p);

    template <typename InputIt, typename Predicate>
    constexpr bool none_of(InputIt first, InputIt last, Predicate p);

    template <typename BidirIt>
    constexpr void reverse(BidirIt first, BidirIt last);

    template <typename BidirIt, typename OutputIt>
    constexpr OutputIt reverse_copy(BidirIt first, BidirIt last, OutputIt destination);

    template <typename ForwardIt>
    constexpr ForwardIt rotate(ForwardIt first, ForwardIt nFirst, ForwardIt last);

    //=== unique ===//
    template <typename ForwardIt, typename Predicate>
    constexpr ForwardIt unique(ForwardIt first, ForwardIt last, Predicate pred);
    template <typename ForwardIt>
    constexpr ForwardIt unique(ForwardIt first, ForwardIt last);

    //=== unique_copy ===//
    template <typename InputIt, typename OutputIt, typename Predicate>
    constexpr OutputIt unique_copy(InputIt first, InputIt last, OutputIt destination, Predicate pred);
    template <typename InputIt, typename OutputIt>
    constexpr OutputIt unique_copy(InputIt first, InputIt last, OutputIt destination);

    template <typename ForwardIt, typename Predicate>
    constexpr ForwardIt partition(ForwardIt first, ForwardIt last, Predicate p);

    template <typename InputIt, typename OutputIt1, typename OutputIt2, typename Predicate>
    constexpr pair<OutputIt1, OutputIt2> partition_copy(InputIt first, InputIt last, OutputIt1 destinationTrue, OutputIt2 destinationFalse, Predicate p);

    template <typename InputIt, typename Predicate>
    constexpr bool is_partitioned(InputIt first, InputIt last, Predicate p);

    template <typename ForwardIt, typename Predicate>
    constexpr ForwardIt partition_point(ForwardIt first, ForwardIt last, Predicate p);

    template <typename BidirIt, typename Predicate>
    constexpr BidirIt stable_partition(BidirIt f, BidirIt l, Predicate p);

    //=== copy ===//
    template <typename InputIt, typename OutputIt>
    constexpr OutputIt copy(InputIt first, InputIt last, OutputIt destination);
    template <typename InputIt, typename OutputIt, typename Predicate>
    constexpr OutputIt copy_if(InputIt first, InputIt last, OutputIt dFirst, Predicate pred);

    template <typename InputIt, typename Size, typename OutputIt>
    constexpr OutputIt copy_n(InputIt first, Size count, OutputIt result);

    template <typename BidirIt1, typename BidirIt2>
    constexpr BidirIt2 copy_backward(BidirIt1 first, BidirIt1 last, BidirIt2 dLast);

    template <typename ForwardIt, typename OutputIt>
    constexpr OutputIt rotate_copy(ForwardIt first, ForwardIt nFirst, ForwardIt last, OutputIt destination);

    template <typename ForwardIt, typename T>
    constexpr void fill(ForwardIt first, ForwardIt last, T const& value);

    template <typename OutputIt, typename Size, typename T>
    constexpr OutputIt fill_n(OutputIt first, Size count, T const& value);

    //=== equal ===//
    template <typename InputIt1, typename InputIt2, typename Predicate>
    constexpr bool equal(InputIt1 first1, InputIt1 last1, InputIt2 first2, Predicate p);
    template <typename InputIt1, typename InputIt2>
    constexpr bool equal(InputIt1 first1, InputIt1 last1, InputIt2 first2);
    template <typename InputIt1, typename InputIt2, typename Predicate>
    constexpr bool equal(InputIt1 first1, InputIt1 last1, InputIt2 first2, InputIt2 last2, Predicate p);
    template <typename InputIt1, typename InputIt2>
    constexpr bool equal(InputIt1 first1, InputIt1 last1, InputIt2 first2, InputIt2 last2);

    //=== lexicographical_compare ===//
    template <typename InputIt1, typename InputIt2, typename Compare>
    constexpr bool lexicographical_compare(InputIt1 first1, InputIt1 last1, InputIt2 first2, InputIt2 last2, Compare comp);
    template <typename InputIt1, typename InputIt2>
    constexpr bool lexicographical_compare(InputIt1 first1, InputIt1 last1, InputIt2 first2, InputIt2 last2);

    //=== sort ===//
    template <typename RandomIt, typename Compare>
    constexpr void sort(RandomIt first, RandomIt last, Compare comp);
    template <typename RandomIt>
    constexpr void sort(RandomIt first, RandomIt last);

    //=== stable_sort ===//
    template <typename RandomIt, typename Compare>
    constexpr void stable_sort(RandomIt first, RandomIt last, Compare cmp);
    template <typename RandomIt>
    constexpr void stable_sort(RandomIt first, RandomIt last);

    //=== partial_sort ===//
    template <typename RandomIt, typename Compare>
    constexpr void partial_sort(RandomIt first, RandomIt middle, RandomIt last, Compare comp);
    template <typename RandomIt>
    constexpr void partial_sort(RandomIt first, RandomIt middle, RandomIt last);

    //=== nth_element ===//
    template <typename RandomIt, typename Compare>
    constexpr void nth_element(RandomIt first, RandomIt nth, RandomIt last, Compare comp);
    template <typename RandomIt>
    constexpr void nth_element(RandomIt first, RandomIt nth, RandomIt last);

    //=== is_sorted_until ===//
    template <typename ForwardIt>
    constexpr ForwardIt is_sorted_until(ForwardIt first, ForwardIt last);
    template <typename ForwardIt, typename Compare>
    constexpr ForwardIt is_sorted_until(ForwardIt first, ForwardIt last, Compare comp);

    //=== is_sorted ===//
    template <typename ForwardIt>
    constexpr bool is_sorted(ForwardIt first, ForwardIt last);
    template <typename ForwardIt, typename Compare>
    constexpr bool is_sorted(ForwardIt first, ForwardIt last, Compare comp);

    //=== lower_bound ===//
    template <typename ForwardIt, typename T, typename Compare>
    constexpr ForwardIt lower_bound(ForwardIt first, ForwardIt last, T const& value, Compare comp) noexcept;
    template <typename ForwardIt, typename T>
    constexpr ForwardIt lower_bound(ForwardIt first, ForwardIt last, T const& value) noexcept;

    //=== upper_bound ===//
    template <typename ForwardIt, typename T, typename Compare>
    constexpr ForwardIt upper_bound(ForwardIt first, ForwardIt last, T const& value, Compare comp);
    template <typename ForwardIt, typename T>
    constexpr ForwardIt upper_bound(ForwardIt first, ForwardIt last, T const& value);

    //=== equal_range ===//
    template <typename ForwardIt, typename T, typename Compare>
    constexpr pair<ForwardIt, ForwardIt> equal_range(ForwardIt first, ForwardIt last, T const& value, Compare comp);
    template <typename ForwardIt, typename T>
    constexpr pair<ForwardIt, ForwardIt> equal_range(ForwardIt first, ForwardIt last, T const& value);

    //=== binary_search ===//
    template <typename ForwardIt, typename T, typename Compare>
    constexpr bool binary_search(ForwardIt first, ForwardIt last, T const& value, Compare comp);
    template <typename ForwardIt, class T>
    constexpr bool binary_search(ForwardIt first, ForwardIt last, T const& value);

    //=== merge ===//
    template <typename InputIt1, typename InputIt2, typename OutputIt, typename Compare>
    constexpr OutputIt merge(InputIt1 first1, InputIt1 last1, InputIt2 first2, InputIt2 last2, OutputIt destination, Compare comp);
    template <typename InputIt1, typename InputIt2, typename OutputIt>
    constexpr OutputIt merge(InputIt1 first1, InputIt1 last1, InputIt2 first2, InputIt2 last2, OutputIt destination);

    //=== includes ===//
    template <typename InputIt1, typename InputIt2>
    constexpr bool includes(InputIt1 first1, InputIt1 last1, InputIt2 first2, InputIt2 last2);
    template <typename InputIt1, typename InputIt2, typename Compare>
    constexpr bool includes(InputIt1 first1, InputIt1 last1, InputIt2 first2, InputIt2 last2, Compare comp);

    //=== set_difference ===//
    template <typename InputIt1, typename InputIt2, typename OutputIt, typename Compare>
    constexpr OutputIt set_difference(InputIt1 first1, InputIt1 last1, InputIt2 first2, InputIt2 last2, OutputIt destination, Compare comp);
    template <typename InputIt1, typename InputIt2, typename OutputIt>
    constexpr OutputIt set_difference(InputIt1 first1, InputIt1 last1, InputIt2 first2, InputIt2 last2, OutputIt destination);

    //=== set_intersection ===//
    template <typename InputIt1, typename InputIt2, typename OutputIt, typename Compare>
    constexpr OutputIt set_intersection(InputIt1 first1, InputIt1 last1, InputIt2 first2, InputIt2 last2, OutputIt dest, Compare comp);
    template <typename InputIt1, typename InputIt2, typename OutputIt>
    constexpr OutputIt set_intersection(InputIt1 first1, InputIt1 last1, InputIt2 first2, InputIt2 last2, OutputIt dest);

    //=== set_symmetric_difference ===//
    template <typename InputIt1, typename InputIt2, typename OutputIt, typename Compare>
    constexpr OutputIt set_symmetric_difference(InputIt1 first1, InputIt1 last1, InputIt2 first2, InputIt2 last2, OutputIt destination, Compare comp);
    template <typename InputIt1, typename InputIt2, typename OutputIt>
    constexpr OutputIt set_symmetric_difference(InputIt1 first1, InputIt1 last1, InputIt2 first2, InputIt2 last2, OutputIt dest);

    //=== set_union ===//
    template <typename InputIt1, typename InputIt2, typename OutputIt, typename Compare>
    constexpr OutputIt set_union(InputIt1 first1, InputIt1 last1, InputIt2 first2, InputIt2 last2, OutputIt destination, Compare comp);
    template <typename InputIt1, typename InputIt2, typename OutputIt>
    constexpr OutputIt set_union(InputIt1 first1, InputIt1 last1, InputIt2 first2, InputIt2 last2, OutputIt destination);

    //=== is_permuatation ===//
    template <typename ForwardIt1, typename ForwardIt2>
    constexpr bool is_permutation(ForwardIt1 first, ForwardIt1 last, ForwardIt2 first2);
    template <typename ForwardIt1, typename ForwardIt2>
    constexpr bool is_permutation(ForwardIt1 first1, ForwardIt1 last1, ForwardIt2 first2, ForwardIt2 last2);
}
```

### Function `etl::iter_swap` \[Algorithm\]

``` cpp
template <typename ForwardIt1, typename ForwardIt2>
constexpr void iter_swap(ForwardIt1 a, ForwardIt2 b);
```

Swaps the values of the elements the given iterators are pointing to.

*Notes:* [cppreference.com/w/cpp/algorithm/iter\_swap](https://en.cppreference.com/w/cpp/algorithm/iter_swap)

#### Parameters

  - `a` - Iterators to the elements to swap.
  - `b` - Iterators to the elements to swap.

-----

### Function `etl::swap_ranges` \[Algorithm\]

``` cpp
template <typename ForwardIt1, typename ForwardIt2>
constexpr ForwardIt2 swap_ranges(ForwardIt1 first1, ForwardIt1 last1, ForwardIt2 first2);
```

Exchanges elements between range `[first1 ,last1)` and another range starting at `first2`.

*Return values:* Iterator to the element past the last element exchanged in the range beginning with `first2`.

*Notes:* [cppreference.com/w/cpp/algorithm/swap\_ranges](https://en.cppreference.com/w/cpp/algorithm/swap_ranges)

#### Parameters

  - `first1` - The first range of elements to swap.
  - `last1` - The first range of elements to swap.
  - `first2` - Beginning of the second range of elements to swap.

-----

### Function `etl::move` \[Algorithm\]

``` cpp
template <typename InputIt, typename OutputIt>
constexpr OutputIt move(InputIt first, InputIt last, OutputIt destination);
```

Moves the elements in the range `[first, last)`, to another range beginning at destination, starting from first and proceeding to `last - 1`. After this operation the elements in the moved-from range will still contain valid values of the appropriate type, but not necessarily the same values as before the move.

*Return values:* Output iterator to the element past the last element moved.

*Notes:* [cppreference.com/w/cpp/algorithm/move](https://en.cppreference.com/w/cpp/algorithm/move)

#### Parameters

  - `first` - The range of elements to move.
  - `last` - The range of elements to move.
  - `destination` - The beginning of the destination range.

-----

### Function `etl::move_backward` \[Algorithm\]

``` cpp
template <typename BidirIt1, typename BidirIt2>
constexpr BidirIt2 move_backward(BidirIt1 first, BidirIt1 last, BidirIt2 destination);
```

Moves the elements from the range `[first, last)`, to another range ending at destination. The elements are moved in reverse order (the last element is moved first), but their relative order is preserved.

*Return values:* Iterator in the destination range, pointing at the last element moved.

*Notes:* [cppreference.com/w/cpp/algorithm/move\_backward](https://en.cppreference.com/w/cpp/algorithm/move_backward)

#### Parameters

  - `first` - The range of elements to move.
  - `last` - The range of elements to move.
  - `destination` - End of the destination range.

-----

### Function `etl::for_each` \[Algorithm\]

``` cpp
template <typename InputIt, typename UnaryFunc>
constexpr UnaryFunc for_each(InputIt first, InputIt last, UnaryFunc f) noexcept;
```

Applies the given function object f to the result of dereferencing every iterator in the range `[first, last)` in order.

*Complexity:* Exactly `last - first` applications of f.

*Notes:* [cppreference.com/w/cpp/algorithm/for\_each](https://en.cppreference.com/w/cpp/algorithm/for_each)

#### Parameters

  - `first` - The range to apply the function to.
  - `last` - The range to apply the function to.
  - `f` - Function object, to be applied to the result of dereferencing every iterator in the range.

-----

### Function `etl::for_each_n` \[Algorithm\]

``` cpp
template <typename InputIt, typename Size, typename UnaryFunc>
constexpr InputIt for_each_n(InputIt first, Size n, UnaryFunc f) noexcept;
```

Applies the given function object f to the result of dereferencing every iterator in the range `[first, first + n]` in order.

*Complexity:* Exactly n applications of f.

*Notes:* [cppreference.com/w/cpp/algorithm/for\_each\_n](https://en.cppreference.com/w/cpp/algorithm/for_each_n)

#### Parameters

  - `first` - The beginning of the range to apply the function to.
  - `n` - The number of elements to apply the function to.
  - `f` - Function object, to be applied to the result of dereferencing every iterator in the range.

-----

### Function `etl::transform` \[Algorithm\]

``` cpp
(1) template <typename InputIt, typename OutputIt, typename UnaryOp>
constexpr OutputIt transform(InputIt first, InputIt last, OutputIt dest, UnaryOp op);

(2) template <typename InputIt1, typename InputIt2, typename OutputIt, typename BinaryOp>
constexpr OutputIt transform(InputIt1 first1, InputIt1 last1, InputIt2 first2, OutputIt dest, BinaryOp op);
```

Applies the given function to a range and stores the result in another range, beginning at dest. The unary operation op is applied to the range defined by `[first, last)`.

*Notes:* [cppreference.com/w/cpp/algorithm/transform](https://en.cppreference.com/w/cpp/algorithm/transform)

#### Parameters

  - `first` - The first range of elements to transform.
  - `last` - The first range of elements to transform.
  - `dest` - The beginning of the destination range, may be equal to first.
  - `op` - Unary operation function object that will be applied.

-----

### Function `etl::generate` \[Algorithm\]

``` cpp
template <typename ForwardIt, typename Generator>
constexpr void generate(ForwardIt first, ForwardIt last, Generator g);
```

Assigns each element in range `[first, last)` a value generated by the given function object g.

*Notes:* [cppreference.com/w/cpp/algorithm/generate](https://en.cppreference.com/w/cpp/algorithm/generate)

#### Parameters

  - `first` - The range of elements to generate.
  - `last` - The range of elements to generate.
  - `g` - Generator function object that will be called.

-----

### Function `etl::generate_n` \[Algorithm\]

``` cpp
template <typename OutputIt, typename SizeT, typename Generator>
constexpr OutputIt generate_n(OutputIt first, SizeT count, Generator g);
```

Assigns values, generated by given function object `g`, to the first count elements in the range beginning at `first`, if `count > 0`. Does nothing otherwise.

*Notes:* [cppreference.com/w/cpp/algorithm/generate\_n](https://en.cppreference.com/w/cpp/algorithm/generate_n)

#### Parameters

  - `first` - The range of elements to generate.
  - `count` - Number of the elements to generate.
  - `g` - Generator function object that will be called.

-----

### Function `etl::count` \[Algorithm\]

``` cpp
(1) template <typename InputIt, typename T>
constexpr typename iterator_traits<InputIt>::difference_type count(InputIt first, InputIt last, T const& value);

(2) template <typename InputIt, typename Predicate>
constexpr typename iterator_traits<InputIt>::difference_type count_if(InputIt first, InputIt last, Predicate p);
```

Returns the number of elements in the range `[first, last)` satisfying specific criteria. Counts the elements that are equal to value.

*Complexity:* Exactly `last - first` comparisons / applications of the predicate.

*Notes:* [cppreference.com/w/cpp/algorithm/count](https://en.cppreference.com/w/cpp/algorithm/count)

#### Parameters

  - `first` - The range of elements to examine.
  - `last` - The range of elements to examine.
  - `value` - The value to search for.

-----

### Function `etl::mismatch` \[Algorithm\]

``` cpp
(1) template <typename InputIt1, typename InputIt2, typename Predicate>
constexpr pair<InputIt1, InputIt2> mismatch(InputIt1 first1, InputIt1 last1, InputIt2 first2, Predicate pred);

(2) template <typename InputIt1, typename InputIt2>
constexpr pair<InputIt1, InputIt2> mismatch(InputIt1 first1, InputIt1 last1, InputIt2 first2);

(3) template <typename InputIt1, typename InputIt2, typename Predicate>
constexpr pair<InputIt1, InputIt2> mismatch(InputIt1 first1, InputIt1 last1, InputIt2 first2, InputIt2 last2, Predicate pred);

(4) template <typename InputIt1, typename InputIt2>
constexpr pair<InputIt1, InputIt2> mismatch(InputIt1 first1, InputIt1 last1, InputIt2 first2, InputIt2 last2);
```
Returns the first mismatching pair of elements from two ranges: one defined by `[first1, last1)` and another defined by \[first2,last2). If last2 is not provided (overloads (1-4)), it denotes first2 + (last1 - first1). Elements are compared using the given binary predicate pred.

*Notes:* [cppreference.com/w/cpp/algorithm/mismatch](https://en.cppreference.com/w/cpp/algorithm/mismatch)

#### Parameters

  - `first1` - The first range of the elements.
  - `last1` - The first range of the elements.
  - `first2` - The second range of the elements.
  - `pred` - Binary predicate which returns ​true if the elements should be treated as equal.

-----

### Function `etl::adjacent_find` \[Algorithm\]

``` cpp
(1) template <typename ForwardIt, typename Predicate>
constexpr ForwardIt adjacent_find(ForwardIt first, ForwardIt last, Predicate pred);

(2) template <typename ForwardIt>
constexpr ForwardIt adjacent_find(ForwardIt first, ForwardIt last);
```
Searches the range `[first, last)` for two consecutive equal elements. Elements are compared using the given binary predicate p.

*Notes:* [cppreference.com/w/cpp/algorithm/adjacent\_find](https://en.cppreference.com/w/cpp/algorithm/adjacent_find)

#### Parameters

  - `first` - The range of elements to examine.
  - `last` - The range of elements to examine.
  - `pred` - Binary predicate which returns ​true if the elements should be treated as equal.

-----

### Function `etl::find` \[Algorithm\]

``` cpp
(1) template <typename InputIt, typename T>
constexpr InputIt find(InputIt first, InputIt last, T const& value) noexcept;
```

Searches for an element equal to value.

*Notes:* [cppreference.com/w/cpp/algorithm/find](https://en.cppreference.com/w/cpp/algorithm/find)

#### Parameters

  - `first` - The range of elements to examine.
  - `last` - The range of elements to examine.
  - `value` - Value to compare the elements to.

-----

### Function `etl::find_if` \[Algorithm\]

``` cpp
(1) template <typename InputIt, typename Predicate>
constexpr InputIt find_if(InputIt first, InputIt last, Predicate pred) noexcept;
```

Searches for an element for which predicate p returns true

*Notes:* [cppreference.com/w/cpp/algorithm/find](https://en.cppreference.com/w/cpp/algorithm/find)

#### Parameters

  - `first` - The range of elements to examine.
  - `last` - The range of elements to examine.
  - `pred` - Unary predicate which returns ​true for the required element.

-----

### Function `etl::find_if_not` \[Algorithm\]

``` cpp
(1) template <typename InputIt, typename Predicate>
constexpr InputIt find_if_not(InputIt first, InputIt last, Predicate pred) noexcept;
```

Searches for an element for which predicate q returns false

*Notes:* [cppreference.com/w/cpp/algorithm/find](https://en.cppreference.com/w/cpp/algorithm/find)

#### Parameters

  - `first` - The range of elements to examine.
  - `last` - The range of elements to examine.
  - `pred` - Unary predicate which returns ​true for the required element.

-----

### Function `etl::find_first_of` \[Algorithm\]

``` cpp
(1) template <typename InputIt, typename ForwardIt, typename Predicate>
constexpr InputIt find_first_of(InputIt first, InputIt last, ForwardIt sFirst, ForwardIt sLast, Predicate pred);

(2) template <typename InputIt, typename ForwardIt>
constexpr InputIt find_first_of(InputIt first, InputIt last, ForwardIt sFirst, ForwardIt sLast);
```
Searches the range `[first, last)` for any of the elements in the range \[sFirst, sLast). Elements are compared using the given binary predicate pred.

*Notes:* [cppreference.com/w/cpp/algorithm/find\_first\_of](https://en.cppreference.com/w/cpp/algorithm/find_first_of)

#### Parameters

  - `first` - The range of elements to examine.
  - `last` - The range of elements to examine.
  - `sFirst` - The range of elements to search for.
  - `sLast` - The range of elements to search for.
  - `pred` - Predicate which returns ​true if the elements should be treated as equal.

-----

### Function `etl::search` \[Algorithm\]

``` cpp
(1) template <typename ForwardIt1, typename ForwardIt2, typename Predicate>
constexpr ForwardIt1 search(ForwardIt1 first, ForwardIt1 last, ForwardIt2 sFirst, ForwardIt2 sLast, Predicate pred);

(2) template <typename ForwardIt1, typename ForwardIt2>
constexpr ForwardIt1 search(ForwardIt1 first, ForwardIt1 last, ForwardIt2 sFirst, ForwardIt2 sLast);

(3) template <typename ForwardIt, typename Searcher>
constexpr ForwardIt search(ForwardIt first, ForwardIt last, Searcher const& searcher);
```

Searches for the first occurrence of the sequence of elements \[sFirst, sLast) in the range `[first, last)`.

*Notes:* [cppreference.com/w/cpp/algorithm/search](https://en.cppreference.com/w/cpp/algorithm/search)

#### Parameters

  - `first` - The range of elements to examine.
  - `last` - The range of elements to examine.
  - `sFirst` - The range of elements to search for.
  - `sLast` - The range of elements to search for.
  - `pred` - Binary predicate which returns ​true if the elements should be treated as equal.

-----

### Function `etl::search_n` \[Algorithm\]

``` cpp
(1) template <typename ForwardIt, typename Size, typename ValueT, typename Predicate>
constexpr ForwardIt search_n(ForwardIt first, ForwardIt last, Size count, ValueT const& value, Predicate pred);

(2) template <typename ForwardIt, typename Size, typename ValueT>
constexpr ForwardIt search_n(ForwardIt first, ForwardIt last, Size count, ValueT const& value);
```

Searches the range `[first, last)` for the first sequence of count identical elements, each equal to the given value.

-----

### Function `etl::find_end` \[Algorithm\]

``` cpp
(1) template <typename ForwardIt1, typename ForwardIt2, typename Predicate>
constexpr ForwardIt1 find_end(ForwardIt1 first, ForwardIt1 last, ForwardIt2 sFirst, ForwardIt2 sLast, Predicate p);

(2) template <typename ForwardIt1, typename ForwardIt2>
constexpr ForwardIt1 find_end(ForwardIt1 first, ForwardIt1 last, ForwardIt2 sFirst, ForwardIt2 sLast);
```
Searches for the last occurrence of the sequence \[sFirst, sLast) in the range `[first, last)`. Elements are compared using the given binary predicate p.

*Return values:* Iterator to the beginning of last occurrence of the sequence \[sFirst, sLast) in range `[first, last)`. If \[sFirst, sLast) is empty or if no such sequence is found, last is returned.

#### Parameters

  - `first` - The range of elements to examine
  - `last` - The range of elements to examine
  - `sFirst` - The range of elements to search for
  - `sLast` - The range of elements to search for
  - `p` - Binary predicate

-----

### Function `etl::remove_if` \[Algorithm\]

``` cpp
(1) template <typename ForwardIt, typename Predicate>
constexpr ForwardIt remove_if(ForwardIt first, ForwardIt last, Predicate pred);
```

Removes all elements satisfying specific criteria from the range `[first, last)` and returns a past-the-end iterator for the new end of the range.

-----

### Function `etl::remove` \[Algorithm\]

``` cpp
(1) template <typename ForwardIt, typename T>
constexpr ForwardIt remove(ForwardIt first, ForwardIt last, T const& value);
```

Removes all elements satisfying specific criteria from the range `[first, last)` and returns a past-the-end iterator for the new end of the range.

-----

### Function `etl::remove_copy_if` \[Algorithm\]

``` cpp
(1) template <typename InputIt, typename OutputIt, typename Predicate>
constexpr OutputIt remove_copy_if(InputIt first, InputIt last, OutputIt destination, Predicate p);

(2) template <typename InputIt, typename OutputIt, typename T>
constexpr OutputIt remove_copy(InputIt first, InputIt last, OutputIt destination, T const& value);
```

Copies elements from the range \[first, last), to another range beginning at destination, omitting the elements which satisfy specific criteria. Source and destination ranges cannot overlap. Ignores all elements for which predicate p returns true.

*Return values:* Iterator to the element past the last element copied.

-----

### Function `etl::replace_if` \[Algorithm\]

``` cpp
(1) template <typename ForwardIt, typename Predicate, typename T>
constexpr void replace_if(ForwardIt first, ForwardIt last, Predicate p, T const& newValue);

(2) template <typename ForwardIt, typename T>
constexpr void replace(ForwardIt first, ForwardIt last, T const& oldValue, T const& newValue);
```

Replaces all elements satisfying specific criteria with new\_value in the range \[first, last). Replaces all elements for which predicate p returns true.

-----

### Function `etl::max` \[Algorithm\]

``` cpp
(1) template <typename Type>
constexpr Type const& max(Type const& a, Type const& b) noexcept;

(2) template <typename Type, typename Compare>
constexpr Type const& max(Type const& a, Type const& b, Compare comp) noexcept;
```

Returns the greater of a and b.

-----

### Function `etl::max_element` \[Algorithm\]

``` cpp
(1) template <typename ForwardIt>
constexpr ForwardIt max_element(ForwardIt first, ForwardIt last) noexcept;

(2) template <typename ForwardIt, typename Compare>
constexpr ForwardIt max_element(ForwardIt first, ForwardIt last, Compare comp);
```
Finds the greatest element in the range `[first, last)`. Elements are compared using operator\<.

-----

### Function `etl::min` \[Algorithm\]

``` cpp
(1) template <typename Type>
constexpr Type const& min(Type const& a, Type const& b) noexcept;

(2) template <typename Type, typename Compare>
constexpr Type const& min(Type const& a, Type const& b, Compare comp) noexcept;
```

Returns the smaller of a and b.

-----

### Function `etl::min_element` \[Algorithm\]

``` cpp
(1) template <typename ForwardIt>
constexpr ForwardIt min_element(ForwardIt first, ForwardIt last) noexcept;

(2) template <typename ForwardIt, typename Compare>
constexpr ForwardIt min_element(ForwardIt first, ForwardIt last, Compare comp);
```
Finds the smallest element in the range `[first, last)`. Elements are compared using operator\<.

-----

### Function `etl::minmax` \[Algorithm\]

``` cpp
(1) template <typename T, typename Compare>
constexpr pair<const T &, const T &> minmax(T const& a, T const& b, Compare comp);

(2) template <typename T>
constexpr pair<const T &, const T &> minmax(T const& a, T const& b);
```

Returns the lowest and the greatest of the given values.

-----

### Function `etl::minmax_element` \[Algorithm\]

``` cpp
(1) template <typename ForwardIt, typename Compare>
constexpr pair<ForwardIt, ForwardIt> minmax_element(ForwardIt first, ForwardIt last, Compare comp);

(2) template <typename ForwardIt>
constexpr pair<ForwardIt, ForwardIt> minmax_element(ForwardIt first, ForwardIt last);
```

Finds the smallest and greatest element in the range `[first, last)`.

-----

### Function `etl::all_of`

``` cpp
template <typename InputIt, typename Predicate>
constexpr bool all_of(InputIt first, InputIt last, Predicate p);
```

Checks if unary predicate p returns true for all elements in the range `[first, last)`.

*Complexity:* At most `last - first` applications of the predicate.

-----

### Function `etl::any_of`

``` cpp
template <typename InputIt, typename Predicate>
constexpr bool any_of(InputIt first, InputIt last, Predicate p);
```

Checks if unary predicate p returns true for at least one element in the range `[first, last)`.

*Complexity:* At most `last - first` applications of the predicate.

-----

### Function `etl::none_of`

``` cpp
template <typename InputIt, typename Predicate>
constexpr bool none_of(InputIt first, InputIt last, Predicate p);
```

Checks if unary predicate p returns true for no elements in the range `[first, last)`.

*Complexity:* At most `last - first` applications of the predicate.

-----

### Function `etl::reverse`

``` cpp
template <typename BidirIt>
constexpr void reverse(BidirIt first, BidirIt last);
```

Reverses the order of the elements in the range `[first, last)`. Behaves as if applying iter\_swap to every pair of iterators first+i, (last-i) - 1 for each non-negative i \< (last-first)/2.

-----

### Function `etl::reverse_copy`

``` cpp
template <typename BidirIt, typename OutputIt>
constexpr OutputIt reverse_copy(BidirIt first, BidirIt last, OutputIt destination);
```

Copies the elements from the range `[first, last)` to another range beginning at d\_first in such a way that the elements in the new range are in reverse order.

If the source and destination ranges (that is, `[first, last)` and \[d\_first, d\_first+(last-first)) respectively) overlap, the behavior is undefined.

-----

### Function `etl::rotate`

``` cpp
template <typename ForwardIt>
constexpr ForwardIt rotate(ForwardIt first, ForwardIt nFirst, ForwardIt last);
```

Performs a left rotation on a range of elements.

Specifically, rotate swaps the elements in the range \[first, last) in such a way that the element n\_first becomes the first element of the new range and n\_first - 1 becomes the last element. A precondition of this function is that \[first, n\_first) and \[n\_first, last) are valid ranges.

-----

### Function `etl::unique` \[Algorithm\]

``` cpp
(1) template <typename ForwardIt, typename Predicate>
constexpr ForwardIt unique(ForwardIt first, ForwardIt last, Predicate pred);

(2) template <typename ForwardIt>
constexpr ForwardIt unique(ForwardIt first, ForwardIt last);
```

Eliminates all except the first element from every consecutive group of equivalent elements from the range `[first, last)` and returns a past-the-end iterator for the new logical end of the range.

-----

### Function `etl::unique_copy` \[Algorithm\]

``` cpp
(1) template <typename InputIt, typename OutputIt, typename Predicate>
constexpr OutputIt unique_copy(InputIt first, InputIt last, OutputIt destination, Predicate pred);

(2) template <typename InputIt, typename OutputIt>
constexpr OutputIt unique_copy(InputIt first, InputIt last, OutputIt destination);
```

Copies the elements from the range `[first, last)`, to another range beginning at d\_first in such a way that there are no consecutive equal elements. Only the first element of each group of equal elements is copied.
Elements are compared using the given binary predicate pred. The behavior is undefined if it is not an equivalence relation.

-----

### Function `etl::partition`

``` cpp
template <typename ForwardIt, typename Predicate>
constexpr ForwardIt partition(ForwardIt first, ForwardIt last, Predicate p);
```

Reorders the elements in the range `[first, last)` in such a way that all elements for which the predicate p returns true precede the elements for which predicate p returns false. Relative order of the elements is not preserved.

-----

### Function `etl::partition_copy`

``` cpp
template <typename InputIt, typename OutputIt1, typename OutputIt2, typename Predicate>
constexpr pair<OutputIt1, OutputIt2> partition_copy(InputIt first, InputIt last, OutputIt1 destinationTrue, OutputIt2 destinationFalse, Predicate p);
```

Copies the elements from the range `[first, last)` to two different ranges depending on the value returned by the predicate p. The elements that satisfy the predicate p are copied to the range beginning at destination\_true. The rest of the elements are copied to the range beginning at destination\_false.

The behavior is undefined if the input range overlaps either of the output ranges.

-----

### Function `etl::is_partitioned`

``` cpp
template <typename InputIt, typename Predicate>
constexpr bool is_partitioned(InputIt first, InputIt last, Predicate p);
```

Returns true if all elements in the range `[first, last)` that satisfy the predicate p appear before all elements that don’t. Also returns true if the range is empty.

*Notes:* [cppreference.com/w/cpp/algorithm/is\_partitioned](https://en.cppreference.com/w/cpp/algorithm/is_partitioned)

-----

### Function `etl::partition_point`

``` cpp
template <typename ForwardIt, typename Predicate>
constexpr ForwardIt partition_point(ForwardIt first, ForwardIt last, Predicate p);
```

Examines the partitioned (as if by partition) range \[first, last) and locates the end of the first partition, that is, the first element that does not satisfy p or last if all elements satisfy p.

-----

### Function `etl::stable_partition`

``` cpp
template <typename BidirIt, typename Predicate>
constexpr BidirIt stable_partition(BidirIt f, BidirIt l, Predicate p);
```

Reorders the elements in the range `[first, last)` in such a way that all elements for which the predicate p returns true precede the elements for which predicate p returns false. Relative order of the elements is preserved.

-----

### Function `etl::copy` \[Algorithm\]

``` cpp
(1) template <typename InputIt, typename OutputIt>
constexpr OutputIt copy(InputIt first, InputIt last, OutputIt destination);

(2) template <typename InputIt, typename OutputIt, typename Predicate>
constexpr OutputIt copy_if(InputIt first, InputIt last, OutputIt dFirst, Predicate pred);
```

Copies the elements in the range, defined by `[first, last)`, to another range beginning at destination.

*Return values:* Output iterator to the element in the destination range, one past the last element copied.

Copies all elements in the range `[first, last)` starting from first and proceeding to `last - 1`. The behavior is undefined if destination is within the range `[first, last)`. In this case, copy\_backward may be used instead.

-----

### Function `etl::copy_n`

``` cpp
template <typename InputIt, typename Size, typename OutputIt>
constexpr OutputIt copy_n(InputIt first, Size count, OutputIt result);
```

Copies exactly count values from the range beginning at first to the range beginning at result. Formally, for each integer 0 ≤ i \< count, performs \*(result + i) = \*(first + i). Overlap of ranges is formally permitted, but leads to unpredictable ordering of the results.

*Return values:* Iterator in the destination range, pointing past the last element copied if count\>0 or result otherwise.

-----

### Function `etl::copy_backward`

``` cpp
template <typename BidirIt1, typename BidirIt2>
constexpr BidirIt2 copy_backward(BidirIt1 first, BidirIt1 last, BidirIt2 dLast);
```

Copies the elements from the range, defined by `[first, last)`, to another range ending at d\_last. The elements are copied in reverse order (the last element is copied first), but their relative order is preserved.

*Return values:* Iterator to the last element copied.

The behavior is undefined if d\_last is within (first, last\]. copy must be used instead of copy\_backward in that case.

-----

### Function `etl::rotate_copy`

``` cpp
template <typename ForwardIt, typename OutputIt>
constexpr OutputIt rotate_copy(ForwardIt first, ForwardIt nFirst, ForwardIt last, OutputIt destination);
```

Copies the elements from the range \[first, last), to another range beginning at destination in such a way, that the element n\_first becomes the first element of the new range and n\_first - 1 becomes the last element.

-----

### Function `etl::fill`

``` cpp
template <typename ForwardIt, typename T>
constexpr void fill(ForwardIt first, ForwardIt last, T const& value);
```

Assigns the given value to the elements in the range `[first, last)`.

-----

### Function `etl::fill_n`

``` cpp
template <typename OutputIt, typename Size, typename T>
constexpr OutputIt fill_n(OutputIt first, Size count, T const& value);
```

Assigns the given value to the first count elements in the range beginning at first if count \> 0. Does nothing otherwise.

*Return values:* Iterator one past the last element assigned if count \> 0, first otherwise.

-----

### Function `etl::equal` \[Algorithm\]

``` cpp
(1) template <typename InputIt1, typename InputIt2, typename Predicate>
constexpr bool equal(InputIt1 first1, InputIt1 last1, InputIt2 first2, Predicate p);

(2) template <typename InputIt1, typename InputIt2>
constexpr bool equal(InputIt1 first1, InputIt1 last1, InputIt2 first2);

(3) template <typename InputIt1, typename InputIt2, typename Predicate>
constexpr bool equal(InputIt1 first1, InputIt1 last1, InputIt2 first2, InputIt2 last2, Predicate p);

(4) template <typename InputIt1, typename InputIt2>
constexpr bool equal(InputIt1 first1, InputIt1 last1, InputIt2 first2, InputIt2 last2);
```

Returns true if the range `[first1, last1)` is equal to the range \[first2, first2 + (last1 - first1)), and false otherwise.

-----

### Function `etl::lexicographical_compare` \[Algorithm\]

``` cpp
(1) template <typename InputIt1, typename InputIt2, typename Compare>
constexpr bool lexicographical_compare(InputIt1 first1, InputIt1 last1, InputIt2 first2, InputIt2 last2, Compare comp);

(2) template <typename InputIt1, typename InputIt2>
constexpr bool lexicographical_compare(InputIt1 first1, InputIt1 last1, InputIt2 first2, InputIt2 last2);
```

Checks if the first range `[first1, last1)` is lexicographically less than the second range `[first2, last2)`.

*Notes:* [cppreference.com/w/cpp/algorithm/lexicographical\_compare](https://en.cppreference.com/w/cpp/algorithm/lexicographical_compare)

-----

### Function `etl::sort` \[Algorithm\]

``` cpp
(1) template <typename RandomIt, typename Compare>
constexpr void sort(RandomIt first, RandomIt last, Compare comp);

(2) template <typename RandomIt>
constexpr void sort(RandomIt first, RandomIt last);
```

Sorts the elements in the range `[first, last)` in non-descending order. The order of equal elements is not guaranteed to be preserved.

*Notes:* [cppreference.com/w/cpp/algorithm/sort](https://en.cppreference.com/w/cpp/algorithm/sort)

-----

### Function `etl::stable_sort` \[Algorithm\]

``` cpp
(1) template <typename RandomIt, typename Compare>
constexpr void stable_sort(RandomIt first, RandomIt last, Compare cmp);

(2) template <typename RandomIt>
constexpr void stable_sort(RandomIt first, RandomIt last);
```
Sorts the elements in the range `[first, last)` in non-descending order. The order of equivalent elements is guaranteed to be preserved. Elements are compared using the given comparison function comp.

*Notes:* [cppreference.com/w/cpp/algorithm/stable\_sort](https://en.cppreference.com/w/cpp/algorithm/stable_sort)

-----

### Function `etl::partial_sort` \[Algorithm\]

``` cpp
(1) template <typename RandomIt, typename Compare>
constexpr void partial_sort(RandomIt first, RandomIt middle, RandomIt last, Compare comp);

(2) template <typename RandomIt>
constexpr void partial_sort(RandomIt first, RandomIt middle, RandomIt last);
```

Rearranges elements such that the range `[first, middle)` contains the sorted `middle - first` smallest elements in the range `[first, last)`. The order of equal elements is not guaranteed to be preserved. The order of the remaining elements in the range `[middle, last)` is unspecified.

*Notes:* [cppreference.com/w/cpp/algorithm/partial\_sort](https://en.cppreference.com/w/cpp/algorithm/partial_sort)

-----

### Function `etl::nth_element` \[Algorithm\]

``` cpp
(1) template <typename RandomIt, typename Compare>
constexpr void nth_element(RandomIt first, RandomIt nth, RandomIt last, Compare comp);

(2) template <typename RandomIt>
constexpr void nth_element(RandomIt first, RandomIt nth, RandomIt last);
```

nth\_element is a partial sorting algorithm that rearranges elements in `[first, last)` such that:

*Notes:* [cppreference.com/w/cpp/algorithm/nth\_element](https://en.cppreference.com/w/cpp/algorithm/nth_element)

  - The element pointed at by nth is changed to whatever element would occur in that position if `[first, last)` were sorted.

  - All of the elements before this new nth element are less than or equal to the elements after the new nth element.

-----

### Function `etl::is_sorted_until` \[Algorithm\]

``` cpp
(1) template <typename ForwardIt>
constexpr ForwardIt is_sorted_until(ForwardIt first, ForwardIt last);

(2) template <typename ForwardIt, typename Compare>
constexpr ForwardIt is_sorted_until(ForwardIt first, ForwardIt last, Compare comp);
```

Examines the range `[first, last)` and finds the largest range beginning at `first` in which the elements are sorted in non-descending order.

-----

### Function `etl::is_sorted` \[Algorithm\]

``` cpp
(1) template <typename ForwardIt>
constexpr bool is_sorted(ForwardIt first, ForwardIt last);

(2) template <typename ForwardIt, typename Compare>
constexpr bool is_sorted(ForwardIt first, ForwardIt last, Compare comp);
```

Checks if the elements in range `[first, last)` are sorted in non-descending order.

-----

### Function `etl::lower_bound` \[Algorithm\]

``` cpp
(1) template <typename ForwardIt, typename T, typename Compare>
constexpr ForwardIt lower_bound(ForwardIt first, ForwardIt last, T const& value, Compare comp) noexcept;

(2) template <typename ForwardIt, typename T>
constexpr ForwardIt lower_bound(ForwardIt first, ForwardIt last, T const& value) noexcept;
```

Returns an iterator pointing to the first element in the range `[first, last)` that is not less than (i.e. greater or equal to) value, or last if no such element is found.

*Notes:* [cppreference.com/w/cpp/algorithm/lower\_bound](https://en.cppreference.com/w/cpp/algorithm/lower_bound)

-----

### Function `etl::upper_bound` \[Algorithm\]

``` cpp
(1) template <typename ForwardIt, typename T, typename Compare>
constexpr ForwardIt upper_bound(ForwardIt first, ForwardIt last, T const& value, Compare comp);

(2) template <typename ForwardIt, typename T>
constexpr ForwardIt upper_bound(ForwardIt first, ForwardIt last, T const& value);
```

Returns an iterator pointing to the first element in the range `[first, last)` that is greater than `value`, or last if no such element is found.

The range `[first, last)` must be partitioned with respect to the expression `!(value < element)` or `!comp(value, element)`, i.e., all elements for which the expression is true must precede all elements for which the expression is false. A fully-sorted range meets this criterion.

-----

### Function `etl::equal_range` \[Algorithm\]

``` cpp
(1) template <typename ForwardIt, typename T, typename Compare>
constexpr pair<ForwardIt, ForwardIt> equal_range(ForwardIt first, ForwardIt last, T const& value, Compare comp);

(2) template <typename ForwardIt, typename T>
constexpr pair<ForwardIt, ForwardIt> equal_range(ForwardIt first, ForwardIt last, T const& value);
```

Returns a range containing all elements equivalent to value in the range `[first, last)`.

*Notes:* [cppreference.com/w/cpp/algorithm/equal\_range](https://en.cppreference.com/w/cpp/algorithm/equal_range)

-----

### Function `etl::binary_search` \[Algorithm\]

``` cpp
(1) template <typename ForwardIt, typename T, typename Compare>
constexpr bool binary_search(ForwardIt first, ForwardIt last, T const& value, Compare comp);

(2) template <typename ForwardIt, class T>
constexpr bool binary_search(ForwardIt first, ForwardIt last, T const& value);
```

Checks if an element equivalent to value appears within the range `[first, last)`. For binary\_search to succeed, the range `[first, last)` must be at least partially ordered with respect to `value`.

*Notes:* [cppreference.com/w/cpp/algorithm/binary\_search](https://en.cppreference.com/w/cpp/algorithm/binary_search)

-----

### Function `etl::merge` \[Algorithm\]

``` cpp
(1) template <typename InputIt1, typename InputIt2, typename OutputIt, typename Compare>
constexpr OutputIt merge(InputIt1 first1, InputIt1 last1, InputIt2 first2, InputIt2 last2, OutputIt destination, Compare comp);

(2) template <typename InputIt1, typename InputIt2, typename OutputIt>
constexpr OutputIt merge(InputIt1 first1, InputIt1 last1, InputIt2 first2, InputIt2 last2, OutputIt destination);
```

Merges two sorted ranges `[first1, last1)` and `[first2, last2)` into one sorted range beginning at `destination`.

-----

### Function `etl::includes` \[Algorithm\]

``` cpp
(1) template <typename InputIt1, typename InputIt2>
constexpr bool includes(InputIt1 first1, InputIt1 last1, InputIt2 first2, InputIt2 last2);

(2) template <typename InputIt1, typename InputIt2, typename Compare>
constexpr bool includes(InputIt1 first1, InputIt1 last1, InputIt2 first2, InputIt2 last2, Compare comp);
```

Returns true if the sorted range `[first2, last2)` is a subsequence of the sorted range `[first1, last1)`. Both ranges must be sorted.

-----

### Function `etl::set_difference` \[Algorithm\]

``` cpp
(1) template <typename InputIt1, typename InputIt2, typename OutputIt, typename Compare>
constexpr OutputIt set_difference(InputIt1 first1, InputIt1 last1, InputIt2 first2, InputIt2 last2, OutputIt destination, Compare comp);

(2) template <typename InputIt1, typename InputIt2, typename OutputIt>
constexpr OutputIt set_difference(InputIt1 first1, InputIt1 last1, InputIt2 first2, InputIt2 last2, OutputIt destination);
```
Copies the elements from the sorted range `[first1, last1)` which are not found in the sorted range `[first2, last2)` to the range beginning at destination. Elements are compared using the given binary comparison function `comp` and the ranges must be sorted with respect to the same.

-----

### Function `etl::set_intersection` \[Algorithm\]

``` cpp
(1) template <typename InputIt1, typename InputIt2, typename OutputIt, typename Compare>
constexpr OutputIt set_intersection(InputIt1 first1, InputIt1 last1, InputIt2 first2, InputIt2 last2, OutputIt dest, Compare comp);

(2) template <typename InputIt1, typename InputIt2, typename OutputIt>
constexpr OutputIt set_intersection(InputIt1 first1, InputIt1 last1, InputIt2 first2, InputIt2 last2, OutputIt dest);
```

Constructs a sorted range beginning at `dest` consisting of elements that are found in both sorted ranges `[first1, last1)` and `[first2, last2)`. If some element is found `m` times in `[first1, last1)` and n times in `[first2, last2)`, the first `min(m, n)` elements will be copied from the first range to the destination range. The order of equivalent elements is preserved. The resulting range cannot overlap with either of the input ranges.

-----

### Function `etl::set_symmetric_difference` \[Algorithm\]

``` cpp
(1) template <typename InputIt1, typename InputIt2, typename OutputIt, typename Compare>
constexpr OutputIt set_symmetric_difference(InputIt1 first1, InputIt1 last1, InputIt2 first2, InputIt2 last2, OutputIt destination, Compare comp);

(2) template <typename InputIt1, typename InputIt2, typename OutputIt>
constexpr OutputIt set_symmetric_difference(InputIt1 first1, InputIt1 last1, InputIt2 first2, InputIt2 last2, OutputIt dest);
```

Computes symmetric difference of two sorted ranges: the elements that are found in either of the ranges, but not in both of them are copied to the range beginning at destination. The resulting range is also sorted.

-----

### Function `etl::set_union` \[Algorithm\]

``` cpp
(1) template <typename InputIt1, typename InputIt2, typename OutputIt, typename Compare>
constexpr OutputIt set_union(InputIt1 first1, InputIt1 last1, InputIt2 first2, InputIt2 last2, OutputIt destination, Compare comp);

(2) template <typename InputIt1, typename InputIt2, typename OutputIt>
constexpr OutputIt set_union(InputIt1 first1, InputIt1 last1, InputIt2 first2, InputIt2 last2, OutputIt destination);
```

Constructs a sorted union beginning at destination consisting of the set of elements present in one or both sorted ranges `[first1, last1)` and `[first2, last2)`. The resulting range cannot overlap with either of the input ranges.

-----

### Function `etl::is_permutation` \[Algorithm\]

``` cpp
(1) template <typename ForwardIt1, typename ForwardIt2>
constexpr bool is_permutation(ForwardIt1 first, ForwardIt1 last, ForwardIt2 first2);

(2) template <typename ForwardIt1, typename ForwardIt2>
constexpr bool is_permutation(ForwardIt1 first1, ForwardIt1 last1, ForwardIt2 first2, ForwardIt2 last2);
```

Returns true if there exists a permutation of the elements in the range `[first1, last1)` that makes that range equal to the range `[first2, last2)`, where `last2` denotes `first2 + (last1 - first1)` if it was not given.

-----
