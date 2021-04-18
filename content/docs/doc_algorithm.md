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

    template <typename ForwardIter1, typename ForwardIter2>
    constexpr ForwardIter2 swap_ranges(ForwardIter1 first1, ForwardIter1 last1, ForwardIter2 first2);

    template <typename InputIter, typename OutputIter>
    constexpr OutputIter move(InputIter first, InputIter last, OutputIter destination);

    template <typename BidirIter1, typename BidirIter2>
    constexpr BidirIter2 move_backward(BidirIter1 first, BidirIter1 last, BidirIter2 destination);

    template <typename InputIter, typename UnaryFunction>
    constexpr UnaryFunction for_each(InputIter first, InputIter last, UnaryFunction f) noexcept;

    template <typename InputIter, typename Size, typename UnaryFunction>
    constexpr InputIter for_each_n(InputIter first, Size n, UnaryFunction f) noexcept;

    //=== transform ===//
    template <typename InputIter, typename OutputIter, typename UnaryOperation>
    constexpr OutputIter transform(InputIter first, InputIter last, OutputIter dest, UnaryOperation op);
    template <typename InputIter1, typename InputIter2, typename OutputIter, typename BinaryOperation>
    constexpr OutputIter transform(InputIter1 first1, InputIter1 last1, InputIter2 first2, OutputIter dest, BinaryOperation op);

    template <typename ForwardIter, typename Generator>
    constexpr void generate(ForwardIter first, ForwardIter last, Generator g);

    template <typename OutputIter, typename SizeT, typename Generator>
    constexpr OutputIter generate_n(OutputIter first, SizeT count, Generator g);

    //=== count ===//
    template <typename InputIter, typename T>
    constexpr typename iterator_traits<InputIter>::difference_type count(InputIter first, InputIter last, T const& value);
    template <typename InputIter, typename UnaryPredicate>
    constexpr typename iterator_traits<InputIter>::difference_type count_if(InputIter first, InputIter last, UnaryPredicate p);

    //=== mismatch ===//
    template <typename InputIter1, typename InputIter2, typename BinaryPredicate>
    constexpr pair<InputIter1, InputIter2> mismatch(InputIter1 first1, InputIter1 last1, InputIter2 first2, BinaryPredicate pred);
    template <typename InputIter1, typename InputIter2>
    constexpr pair<InputIter1, InputIter2> mismatch(InputIter1 first1, InputIter1 last1, InputIter2 first2);
    template <typename InputIter1, typename InputIter2, typename BinaryPredicate>
    constexpr pair<InputIter1, InputIter2> mismatch(InputIter1 first1, InputIter1 last1, InputIter2 first2, InputIter2 last2, BinaryPredicate pred);
    template <typename InputIter1, typename InputIter2>
    constexpr pair<InputIter1, InputIter2> mismatch(InputIter1 first1, InputIter1 last1, InputIter2 first2, InputIter2 last2);

    //=== adjacent_find ===//
    template <typename ForwardIter, typename BinaryPredicate>
    constexpr ForwardIter adjacent_find(ForwardIter first, ForwardIter last, BinaryPredicate pred);
    template <typename ForwardIt>
    constexpr ForwardIt adjacent_find(ForwardIt first, ForwardIt last);

    //=== find ===//
    template <typename InputIter, typename T>
    constexpr InputIter find(InputIter first, InputIter last, T const& value) noexcept;
    template <typename InputIter, typename UnaryPredicate>
    constexpr InputIter find_if(InputIter first, InputIter last, UnaryPredicate pred) noexcept;
    template <typename InputIter, typename UnaryPredicate>
    constexpr InputIter find_if_not(InputIter first, InputIter last, UnaryPredicate pred) noexcept;

    //=== find_first_of ===//
    template <typename InputIter, typename ForwardIter, typename BinaryPredicate>
    constexpr InputIter find_first_of(InputIter first, InputIter last, ForwardIter sFirst, ForwardIter sLast, BinaryPredicate pred);
    template <typename InputIter, typename ForwardIter>
    constexpr InputIter find_first_of(InputIter first, InputIter last, ForwardIter sFirst, ForwardIter sLast);

    //=== search ===//
    template <typename ForwardIter1, typename ForwardIter2, typename BinaryPredicate>
    constexpr ForwardIter1 search(ForwardIter1 first, ForwardIter1 last, ForwardIter2 sFirst, ForwardIter2 sLast, BinaryPredicate pred);
    template <typename ForwardIter1, typename ForwardIter2>
    constexpr ForwardIter1 search(ForwardIter1 first, ForwardIter1 last, ForwardIter2 sFirst, ForwardIter2 sLast);
    template <typename ForwardIter, typename Searcher>
    constexpr ForwardIter search(ForwardIter first, ForwardIter last, Searcher const& searcher);

    //=== search_n ===//
    template <typename ForwardIter, typename Size, typename ValueT, typename BinaryPredicate>
    constexpr ForwardIter search_n(ForwardIter first, ForwardIter last, Size count, ValueT const& value, BinaryPredicate pred);
    template <typename ForwardIter, typename Size, typename ValueT>
    constexpr ForwardIter search_n(ForwardIter first, ForwardIter last, Size count, ValueT const& value);

    //=== find_end ===//
    template <typename ForwardIter1, typename ForwardIter2, typename BinaryPredicate>
    constexpr ForwardIter1 find_end(ForwardIter1 first, ForwardIter1 last, ForwardIter2 sFirst, ForwardIter2 sLast, BinaryPredicate p);
    template <typename ForwardIter1, typename ForwardIter2>
    constexpr ForwardIter1 find_end(ForwardIter1 first, ForwardIter1 last, ForwardIter2 sFirst, ForwardIter2 sLast);

    //=== remove ===//
    template <typename ForwardIter, typename UnaryPredicate>
    constexpr ForwardIter remove_if(ForwardIter first, ForwardIter last, UnaryPredicate pred);
    template <typename ForwardIter, typename T>
    constexpr ForwardIter remove(ForwardIter first, ForwardIter last, T const& value);

    //=== remove_copy ===//
    template <typename InputIter, typename OutputIter, typename UnaryPredicate>
    constexpr OutputIter remove_copy_if(InputIter first, InputIter last, OutputIter destination, UnaryPredicate p);
    template <typename InputIter, typename OutputIter, typename T>
    constexpr OutputIter remove_copy(InputIter first, InputIter last, OutputIter destination, T const& value);

    //=== replace ===//
    template <typename ForwardIt, typename UnaryPredicate, typename T>
    constexpr void replace_if(ForwardIt first, ForwardIt last, UnaryPredicate p, T const& newValue);
    template <typename ForwardIt, typename T>
    constexpr void replace(ForwardIt first, ForwardIt last, T const& oldValue, T const& newValue);

    //=== max ===//
    template <typename Type>
    constexpr Type const& max(Type const& a, Type const& b) noexcept;
    template <typename Type, typename Compare>
    constexpr Type const& max(Type const& a, Type const& b, Compare comp) noexcept;

    //=== max_element ===//
    template <typename ForwardIterator>
    constexpr ForwardIterator max_element(ForwardIterator first, ForwardIterator last) noexcept;
    template <typename ForwardIterator, typename Compare>
    constexpr ForwardIterator max_element(ForwardIterator first, ForwardIterator last, Compare comp);

    //=== min ===//
    template <typename Type>
    constexpr Type const& min(Type const& a, Type const& b) noexcept;
    template <typename Type, typename Compare>
    constexpr Type const& min(Type const& a, Type const& b, Compare comp) noexcept;

    //=== min_element ===//
    template <typename ForwardIterator>
    constexpr ForwardIterator min_element(ForwardIterator first, ForwardIterator last) noexcept;
    template <typename ForwardIterator, typename Compare>
    constexpr ForwardIterator min_element(ForwardIterator first, ForwardIterator last, Compare comp);

    //=== minmax ===//
    template <typename T, typename Compare>
    constexpr pair<const T &, const T &> minmax(T const& a, T const& b, Compare comp);
    template <typename T>
    constexpr pair<const T &, const T &> minmax(T const& a, T const& b);

    //=== minmax_element ===//
    template <typename ForwardIter, typename Compare>
    constexpr pair<ForwardIter, ForwardIter> minmax_element(ForwardIter first, ForwardIter last, Compare comp);
    template <typename ForwardIter>
    constexpr pair<ForwardIter, ForwardIter> minmax_element(ForwardIter first, ForwardIter last);

    template <typename InputIter, typename UnaryPredicate>
    constexpr bool all_of(InputIter first, InputIter last, UnaryPredicate p);

    template <typename InputIter, typename UnaryPredicate>
    constexpr bool any_of(InputIter first, InputIter last, UnaryPredicate p);

    template <typename InputIter, typename UnaryPredicate>
    constexpr bool none_of(InputIter first, InputIter last, UnaryPredicate p);

    template <typename BidirIter>
    constexpr void reverse(BidirIter first, BidirIter last);

    template <typename BidirIter, typename OutputIter>
    constexpr OutputIter reverse_copy(BidirIter first, BidirIter last, OutputIter destination);

    template <typename ForwardIter>
    constexpr ForwardIter rotate(ForwardIter first, ForwardIter nFirst, ForwardIter last);

    //=== unique ===//
    template <typename ForwardIter, typename BinaryPredicate>
    constexpr ForwardIter unique(ForwardIter first, ForwardIter last, BinaryPredicate pred);
    template <typename ForwardIter>
    constexpr ForwardIter unique(ForwardIter first, ForwardIter last);

    //=== unique_copy ===//
    template <typename InputIter, typename OutputIter, typename BinaryPredicate>
    constexpr OutputIter unique_copy(InputIter first, InputIter last, OutputIter destination, BinaryPredicate pred);
    template <typename InputIter, typename OutputIter>
    constexpr OutputIter unique_copy(InputIter first, InputIter last, OutputIter destination);

    template <typename ForwardIter, typename UnaryPredicate>
    constexpr ForwardIter partition(ForwardIter first, ForwardIter last, UnaryPredicate p);

    template <typename InputIter, typename OutputIter1, typename OutputIter2, typename UnaryPredicate>
    constexpr pair<OutputIter1, OutputIter2> partition_copy(InputIter first, InputIter last, OutputIter1 destinationTrue, OutputIter2 destinationFalse, UnaryPredicate p);

    template <typename InputIter, typename UnaryPredicate>
    constexpr bool is_partitioned(InputIter first, InputIter last, UnaryPredicate p);

    template <typename ForwardIter, typename UnaryPredicate>
    constexpr ForwardIter partition_point(ForwardIter first, ForwardIter last, UnaryPredicate p);

    template <typename BidirIter, typename UnaryPredicate>
    constexpr BidirIter stable_partition(BidirIter f, BidirIter l, UnaryPredicate p);

    //=== copy ===//
    template <typename InputIter, typename OutputIter>
    constexpr OutputIter copy(InputIter first, InputIter last, OutputIter destination);
    template <typename InputIter, typename OutputIter, typename UnaryPredicate>
    constexpr OutputIter copy_if(InputIter first, InputIter last, OutputIter dFirst, UnaryPredicate pred);

    template <typename InputIter, typename Size, typename OutputIter>
    constexpr OutputIter copy_n(InputIter first, Size count, OutputIter result);

    template <typename BidirIter1, typename BidirIter2>
    constexpr BidirIter2 copy_backward(BidirIter1 first, BidirIter1 last, BidirIter2 dLast);

    template <typename ForwardIter, typename OutputIter>
    constexpr OutputIter rotate_copy(ForwardIter first, ForwardIter nFirst, ForwardIter last, OutputIter destination);

    template <typename ForwardIter, typename T>
    constexpr void fill(ForwardIter first, ForwardIter last, T const& value);

    template <typename OutputIter, typename Size, typename T>
    constexpr OutputIter fill_n(OutputIter first, Size count, T const& value);

    //=== equal ===//
    template <typename InputIter1, typename InputIter2, typename BinaryPredicate>
    constexpr bool equal(InputIter1 first1, InputIter1 last1, InputIter2 first2, BinaryPredicate p);
    template <typename InputIter1, typename InputIter2>
    constexpr bool equal(InputIter1 first1, InputIter1 last1, InputIter2 first2);
    template <typename InputIter1, typename InputIter2, typename BinaryPredicate>
    constexpr bool equal(InputIter1 first1, InputIter1 last1, InputIter2 first2, InputIter2 last2, BinaryPredicate p);
    template <typename InputIter1, typename InputIter2>
    constexpr bool equal(InputIter1 first1, InputIter1 last1, InputIter2 first2, InputIter2 last2);

    //=== lexicographical_compare ===//
    template <typename InputIter1, typename InputIter2, typename Compare>
    constexpr bool lexicographical_compare(InputIter1 first1, InputIter1 last1, InputIter2 first2, InputIter2 last2, Compare comp);
    template <typename InputIter1, typename InputIter2>
    constexpr bool lexicographical_compare(InputIter1 first1, InputIter1 last1, InputIter2 first2, InputIter2 last2);

    //=== sort ===//
    template <typename RandomIter, typename Compare>
    constexpr void sort(RandomIter first, RandomIter last, Compare comp);
    template <typename RandomIter>
    constexpr void sort(RandomIter first, RandomIter last);

    //=== stable_sort ===//
    template <typename RandomIter, typename Compare>
    constexpr void stable_sort(RandomIter first, RandomIter last, Compare cmp);
    template <typename RandomIter>
    constexpr void stable_sort(RandomIter first, RandomIter last);

    //=== partial_sort ===//
    template <typename RandomIter, typename Compare>
    constexpr void partial_sort(RandomIter first, RandomIter middle, RandomIter last, Compare comp);
    template <typename RandomIter>
    constexpr void partial_sort(RandomIter first, RandomIter middle, RandomIter last);

    //=== nth_element ===//
    template <typename RandomIter, typename Compare>
    constexpr void nth_element(RandomIter first, RandomIter nth, RandomIter last, Compare comp);
    template <typename RandomIter>
    constexpr void nth_element(RandomIter first, RandomIter nth, RandomIter last);

    //=== is_sorted_until ===//
    template <typename ForwardIter>
    constexpr ForwardIter is_sorted_until(ForwardIter first, ForwardIter last);
    template <typename ForwardIter, typename Compare>
    constexpr ForwardIter is_sorted_until(ForwardIter first, ForwardIter last, Compare comp);

    //=== is_sorted ===//
    template <typename ForwardIter>
    constexpr bool is_sorted(ForwardIter first, ForwardIter last);
    template <typename ForwardIter, typename Compare>
    constexpr bool is_sorted(ForwardIter first, ForwardIter last, Compare comp);

    //=== lower_bound ===//
    template <typename ForwardIter, typename T, typename Compare>
    constexpr ForwardIter lower_bound(ForwardIter first, ForwardIter last, T const& value, Compare comp) noexcept;
    template <typename ForwardIter, typename T>
    constexpr ForwardIter lower_bound(ForwardIter first, ForwardIter last, T const& value) noexcept;

    //=== upper_bound ===//
    template <typename ForwardIter, typename T, typename Compare>
    constexpr ForwardIter upper_bound(ForwardIter first, ForwardIter last, T const& value, Compare comp);
    template <typename ForwardIter, typename T>
    constexpr ForwardIter upper_bound(ForwardIter first, ForwardIter last, T const& value);

    //=== equal_range ===//
    template <typename ForwardIt, typename T, typename Compare>
    constexpr pair<ForwardIt, ForwardIt> equal_range(ForwardIt first, ForwardIt last, T const& value, Compare comp);
    template <typename ForwardIt, typename T>
    constexpr pair<ForwardIt, ForwardIt> equal_range(ForwardIt first, ForwardIt last, T const& value);

    //=== binary_search ===//
    template <typename ForwardIter, typename T, typename Compare>
    constexpr bool binary_search(ForwardIter first, ForwardIter last, T const& value, Compare comp);
    template <typename ForwardIter, class T>
    constexpr bool binary_search(ForwardIter first, ForwardIter last, T const& value);

    //=== merge ===//
    template <typename InputIt1, typename InputIt2, typename OutputIt, typename Compare>
    constexpr OutputIt merge(InputIt1 first1, InputIt1 last1, InputIt2 first2, InputIt2 last2, OutputIt destination, Compare comp);
    template <typename InputIt1, typename InputIt2, typename OutputIt>
    constexpr OutputIt merge(InputIt1 first1, InputIt1 last1, InputIt2 first2, InputIt2 last2, OutputIt destination);

    //=== includes ===//
    template <typename InputIter1, typename InputIter2>
    constexpr bool includes(InputIter1 first1, InputIter1 last1, InputIter2 first2, InputIter2 last2);
    template <typename InputIter1, typename InputIter2, typename Compare>
    constexpr bool includes(InputIter1 first1, InputIter1 last1, InputIter2 first2, InputIter2 last2, Compare comp);

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
    template <typename InputIter1, typename InputIter2, typename OutputIter, typename Compare>
    constexpr OutputIter set_symmetric_difference(InputIter1 first1, InputIter1 last1, InputIter2 first2, InputIter2 last2, OutputIter destination, Compare comp);
    template <typename InputIter1, typename InputIter2, typename OutputIter>
    constexpr OutputIter set_symmetric_difference(InputIter1 first1, InputIter1 last1, InputIter2 first2, InputIter2 last2, OutputIter dest);

    //=== set_union ===//
    template <typename InputIter1, typename InputIter2, typename OutputIter, typename Compare>
    constexpr OutputIter set_union(InputIter1 first1, InputIter1 last1, InputIter2 first2, InputIter2 last2, OutputIter destination, Compare comp);
    template <typename InputIter1, typename InputIter2, typename OutputIter>
    constexpr OutputIter set_union(InputIter1 first1, InputIter1 last1, InputIter2 first2, InputIter2 last2, OutputIter destination);

    //=== is_permuatation ===//
    template <typename ForwardIter1, typename ForwardIter2>
    constexpr bool is_permutation(ForwardIter1 first, ForwardIter1 last, ForwardIter2 first2);
    template <typename ForwardIter1, typename ForwardIter2>
    constexpr bool is_permutation(ForwardIter1 first1, ForwardIter1 last1, ForwardIter2 first2, ForwardIter2 last2);
}
```

### Function `etl::iter_swap` \[Algorithm\]

``` cpp
template <typename ForwardIt1, typename ForwardIt2>
constexpr void iter_swap(ForwardIt1 a, ForwardIt2 b);
```

Swaps the values of the elements the given iterators are pointing to.

*Notes:* [cppreference.com](https://en.cppreference.com/w/cpp/algorithm/iter_swap)

-----

### Function `etl::swap_ranges` \[Algorithm\]

``` cpp
template <typename ForwardIter1, typename ForwardIter2>
constexpr ForwardIter2 swap_ranges(ForwardIter1 first1, ForwardIter1 last1, ForwardIter2 first2);
```

Exchanges elements between range \[first1 ,last1) and another range starting at first2.

*Notes:* [cppreference.com](https://en.cppreference.com/w/cpp/algorithm/swap_ranges)

#### Parameters

  - `first1` - the first range of elements to swap
  - `last1` - the first range of elements to swap
  - `first2` - beginning of the second range of elements to swap

-----

### Function `etl::move` \[Algorithm\]

``` cpp
template <typename InputIter, typename OutputIter>
constexpr OutputIter move(InputIter first, InputIter last, OutputIter destination);
```

Moves the elements in the range \[first, last), to another range beginning at destination, starting from first and proceeding to last - 1. After this operation the elements in the moved-from range will still contain valid values of the appropriate type, but not necessarily the same values as before the move.

*Notes:* [cppreference.com](https://en.cppreference.com/w/cpp/algorithm/move)

*Return values:* Output iterator to the element past the last element moved.

#### Parameters

  - `first` - The range of elements to move.
  - `last` - The range of elements to move.
  - `destination` - The beginning of the destination range.

-----

### Function `etl::move_backward` \[Algorithm\]

``` cpp
template <typename BidirIter1, typename BidirIter2>
constexpr BidirIter2 move_backward(BidirIter1 first, BidirIter1 last, BidirIter2 destination);
```

Moves the elements from the range \[first, last), to another range ending at destination. The elements are moved in reverse order (the last element is moved first), but their relative order is preserved.

*Notes:* [cppreference.com](https://en.cppreference.com/w/cpp/algorithm/move_backward)

*Return values:* Iterator in the destination range, pointing at the last element moved.

#### Parameters

  - `first` - The range of elements to move.
  - `last` - The range of elements to move.
  - `destination` - End of the destination range.

-----

### Function `etl::for_each` \[Algorithm\]

``` cpp
template <typename InputIter, typename UnaryFunction>
constexpr UnaryFunction for_each(InputIter first, InputIter last, UnaryFunction f) noexcept;
```

Applies the given function object f to the result of dereferencing every iterator in the range \[first, last) in order.

*Notes:* [cppreference.com](https://en.cppreference.com/w/cpp/algorithm/for_each)

*Complexity:* Exactly last - first applications of f.

#### Parameters

  - `first` - The range to apply the function to.
  - `last` - The range to apply the function to.
  - `f` - Function object, to be applied to the result of dereferencing every iterator in the range.

-----

### Function `etl::for_each_n` \[Algorithm\]

``` cpp
template <typename InputIter, typename Size, typename UnaryFunction>
constexpr InputIter for_each_n(InputIter first, Size n, UnaryFunction f) noexcept;
```

Applies the given function object f to the result of dereferencing every iterator in the range \[first, first + n\] in order.

*Notes:* [cppreference.com](https://en.cppreference.com/w/cpp/algorithm/for_each_n)

*Complexity:* Exactly n applications of f.

#### Parameters

  - `first` - The beginning of the range to apply the function to.
  - `n` - The number of elements to apply the function to.
  - `f` - Function object, to be applied to the result of dereferencing every iterator in the range.

-----

### Function `etl::transform` \[Algorithm\]

``` cpp
(1) template <typename InputIter, typename OutputIter, typename UnaryOperation>
constexpr OutputIter transform(InputIter first, InputIter last, OutputIter dest, UnaryOperation op);

(2) template <typename InputIter1, typename InputIter2, typename OutputIter, typename BinaryOperation>
constexpr OutputIter transform(InputIter1 first1, InputIter1 last1, InputIter2 first2, OutputIter dest, BinaryOperation op);
```

Applies the given function to a range and stores the result in another range, beginning at dest. The unary operation op is applied to the range defined by \[first, last).

*Notes:* [cppreference.com](https://en.cppreference.com/w/cpp/algorithm/transform)

#### Parameters

  - `first` - The first range of elements to transform.
  - `last` - The first range of elements to transform.
  - `dest` - The beginning of the destination range, may be equal to first.
  - `op` - Unary operation function object that will be applied.

-----

### Function `etl::generate`

``` cpp
template <typename ForwardIter, typename Generator>
constexpr void generate(ForwardIter first, ForwardIter last, Generator g);
```

Assigns each element in range \[first, last) a value generated by the given function object g.

*Notes:* [cppreference.com](https://en.cppreference.com/w/cpp/algorithm/generate)

#### Parameters

  - `first` - The range of elements to generate.
  - `last` - The range of elements to generate.
  - `g` - Generator function object that will be called.

-----

### Function `etl::generate_n`

``` cpp
template <typename OutputIter, typename SizeT, typename Generator>
constexpr OutputIter generate_n(OutputIter first, SizeT count, Generator g);
```

Assigns values, generated by given function object g, to the first count elements in the range beginning at first, if count \> 0. Does nothing otherwise.

*Notes:* [cppreference.com](https://en.cppreference.com/w/cpp/algorithm/generate_n)

#### Parameters

  - `first` - The range of elements to generate.
  - `count` - Number of the elements to generate.
  - `g` - Generator function object that will be called.

-----

### Function `etl::count` \[Algorithm\]

``` cpp
(1) template <typename InputIter, typename T>
constexpr typename iterator_traits<InputIter>::difference_type count(InputIter first, InputIter last, T const& value);

(2) template <typename InputIter, typename UnaryPredicate>
constexpr typename iterator_traits<InputIter>::difference_type count_if(InputIter first, InputIter last, UnaryPredicate p);
```

Returns the number of elements in the range \[first, last) satisfying specific criteria. Counts the elements that are equal to value.

*Notes:* [cppreference.com](https://en.cppreference.com/w/cpp/algorithm/count)

*Complexity:* Exactly last - first comparisons / applications of the predicate.

#### Parameters

  - `first` - The range of elements to examine.
  - `last` - The range of elements to examine.
  - `value` - The value to search for.

-----

### Function `etl::mismatch` \[Algorithm\]

``` cpp
(1) template <typename InputIter1, typename InputIter2, typename BinaryPredicate>
constexpr pair<InputIter1, InputIter2> mismatch(InputIter1 first1, InputIter1 last1, InputIter2 first2, BinaryPredicate pred);

(2) template <typename InputIter1, typename InputIter2>
constexpr pair<InputIter1, InputIter2> mismatch(InputIter1 first1, InputIter1 last1, InputIter2 first2);

(3) template <typename InputIter1, typename InputIter2, typename BinaryPredicate>
constexpr pair<InputIter1, InputIter2> mismatch(InputIter1 first1, InputIter1 last1, InputIter2 first2, InputIter2 last2, BinaryPredicate pred);

(4) template <typename InputIter1, typename InputIter2>
constexpr pair<InputIter1, InputIter2> mismatch(InputIter1 first1, InputIter1 last1, InputIter2 first2, InputIter2 last2);
```
Returns the first mismatching pair of elements from two ranges: one defined by \[first1, last1) and another defined by \[first2,last2). If last2 is not provided (overloads (1-4)), it denotes first2 + (last1 - first1). Elements are compared using the given binary predicate pred.

*Notes:* [cppreference.com](https://en.cppreference.com/w/cpp/algorithm/mismatch)

#### Parameters

  - `first1` - The first range of the elements.
  - `last1` - The first range of the elements.
  - `first2` - The second range of the elements.
  - `pred` - Binary predicate which returns ​true if the elements should be treated as equal.

-----

### Function `etl::adjacent_find` \[Algorithm\]

``` cpp
(1) template <typename ForwardIter, typename BinaryPredicate>
constexpr ForwardIter adjacent_find(ForwardIter first, ForwardIter last, BinaryPredicate pred);

(2) template <typename ForwardIt>
constexpr ForwardIt adjacent_find(ForwardIt first, ForwardIt last);
```
Searches the range \[first, last) for two consecutive equal elements. Elements are compared using the given binary predicate p.

*Notes:* [cppreference.com](https://en.cppreference.com/w/cpp/algorithm/adjacent_find)

#### Parameters

  - `first` - The range of elements to examine.
  - `last` - The range of elements to examine.
  - `pred` - Binary predicate which returns ​true if the elements should be treated as equal.

-----

### Function `etl::find` \[Algorithm\]

``` cpp
(1) template <typename InputIter, typename T>
constexpr InputIter find(InputIter first, InputIter last, T const& value) noexcept;

(2) template <typename InputIter, typename UnaryPredicate>
constexpr InputIter find_if(InputIter first, InputIter last, UnaryPredicate pred) noexcept;

(3) template <typename InputIter, typename UnaryPredicate>
constexpr InputIter find_if_not(InputIter first, InputIter last, UnaryPredicate pred) noexcept;
```

Searches for an element equal to value.

*Notes:* [cppreference.com](https://en.cppreference.com/w/cpp/algorithm/find)

#### Parameters

  - `first` - The range of elements to examine.
  - `last` - The range of elements to examine.
  - `value` - Value to compare the elements to.

-----

### Function `etl::find_first_of` \[Algorithm\]

``` cpp
(1) template <typename InputIter, typename ForwardIter, typename BinaryPredicate>
constexpr InputIter find_first_of(InputIter first, InputIter last, ForwardIter sFirst, ForwardIter sLast, BinaryPredicate pred);

(2) template <typename InputIter, typename ForwardIter>
constexpr InputIter find_first_of(InputIter first, InputIter last, ForwardIter sFirst, ForwardIter sLast);
```
Searches the range \[first, last) for any of the elements in the range \[sFirst, sLast). Elements are compared using the given binary predicate pred.

*Notes:* [cppreference.com](https://en.cppreference.com/w/cpp/algorithm/find_first_of)

#### Parameters

  - `first` - The range of elements to examine.
  - `last` - The range of elements to examine.
  - `sFirst` - The range of elements to search for.
  - `sLast` - The range of elements to search for.
  - `pred` - Binary predicate which returns ​true if the elements should be treated as equal.

-----

### Function `etl::search` \[Algorithm\]

``` cpp
(1) template <typename ForwardIter1, typename ForwardIter2, typename BinaryPredicate>
constexpr ForwardIter1 search(ForwardIter1 first, ForwardIter1 last, ForwardIter2 sFirst, ForwardIter2 sLast, BinaryPredicate pred);

(2) template <typename ForwardIter1, typename ForwardIter2>
constexpr ForwardIter1 search(ForwardIter1 first, ForwardIter1 last, ForwardIter2 sFirst, ForwardIter2 sLast);

(3) template <typename ForwardIter, typename Searcher>
constexpr ForwardIter search(ForwardIter first, ForwardIter last, Searcher const& searcher);
```
Searches for the first occurrence of the sequence of elements \[sFirst, sLast) in the range \[first, last). Elements are compared using the given binary predicate pred.

*Notes:* [cppreference.com](https://en.cppreference.com/w/cpp/algorithm/search)

#### Parameters

  - `first` - The range of elements to examine.
  - `last` - The range of elements to examine.
  - `sFirst` - The range of elements to search for.
  - `sLast` - The range of elements to search for.
  - `pred` - Binary predicate which returns ​true if the elements should be treated as equal.

-----

### Function `etl::search_n` \[Algorithm\]

``` cpp
(1) template <typename ForwardIter, typename Size, typename ValueT, typename BinaryPredicate>
constexpr ForwardIter search_n(ForwardIter first, ForwardIter last, Size count, ValueT const& value, BinaryPredicate pred);

(2) template <typename ForwardIter, typename Size, typename ValueT>
constexpr ForwardIter search_n(ForwardIter first, ForwardIter last, Size count, ValueT const& value);
```

Searches the range \[first, last) for the first sequence of count identical elements, each equal to the given value.

-----

### Function `etl::find_end` \[Algorithm\]

``` cpp
(1) template <typename ForwardIter1, typename ForwardIter2, typename BinaryPredicate>
constexpr ForwardIter1 find_end(ForwardIter1 first, ForwardIter1 last, ForwardIter2 sFirst, ForwardIter2 sLast, BinaryPredicate p);

(2) template <typename ForwardIter1, typename ForwardIter2>
constexpr ForwardIter1 find_end(ForwardIter1 first, ForwardIter1 last, ForwardIter2 sFirst, ForwardIter2 sLast);
```
Searches for the last occurrence of the sequence \[sFirst, sLast) in the range \[first, last). Elements are compared using the given binary predicate p.

*Return values:* Iterator to the beginning of last occurrence of the sequence \[sFirst, sLast) in range \[first, last). If \[sFirst, sLast) is empty or if no such sequence is found, last is returned.

#### Parameters

  - `first` - The range of elements to examine
  - `last` - The range of elements to examine
  - `sFirst` - The range of elements to search for
  - `sLast` - The range of elements to search for
  - `p` - Binary predicate

-----

### Function `etl::remove_if` \[Algorithm\]

``` cpp
(1) template <typename ForwardIter, typename UnaryPredicate>
constexpr ForwardIter remove_if(ForwardIter first, ForwardIter last, UnaryPredicate pred);

(2) template <typename ForwardIter, typename T>
constexpr ForwardIter remove(ForwardIter first, ForwardIter last, T const& value);
```

Removes all elements satisfying specific criteria from the range \[first, last) and returns a past-the-end iterator for the new end of the range.

-----

### Function `etl::remove_copy_if` \[Algorithm\]

``` cpp
(1) template <typename InputIter, typename OutputIter, typename UnaryPredicate>
constexpr OutputIter remove_copy_if(InputIter first, InputIter last, OutputIter destination, UnaryPredicate p);

(2) template <typename InputIter, typename OutputIter, typename T>
constexpr OutputIter remove_copy(InputIter first, InputIter last, OutputIter destination, T const& value);
```

Copies elements from the range \[ first , last ), to another range beginning at destination, omitting the elements which satisfy specific criteria. Source and destination ranges cannot overlap. Ignores all elements for which predicate p returns true.

*Return values:* Iterator to the element past the last element copied.

-----

### Function `etl::replace_if` \[Algorithm\]

``` cpp
(1) template <typename ForwardIt, typename UnaryPredicate, typename T>
constexpr void replace_if(ForwardIt first, ForwardIt last, UnaryPredicate p, T const& newValue);

(2) template <typename ForwardIt, typename T>
constexpr void replace(ForwardIt first, ForwardIt last, T const& oldValue, T const& newValue);
```

Replaces all elements satisfying specific criteria with new\_value in the range \[ first , last ). Replaces all elements for which predicate p returns true.

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
(1) template <typename ForwardIterator>
constexpr ForwardIterator max_element(ForwardIterator first, ForwardIterator last) noexcept;

(2) template <typename ForwardIterator, typename Compare>
constexpr ForwardIterator max_element(ForwardIterator first, ForwardIterator last, Compare comp);
```
Finds the greatest element in the range \[first, last). Elements are compared using operator\<.

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
(1) template <typename ForwardIterator>
constexpr ForwardIterator min_element(ForwardIterator first, ForwardIterator last) noexcept;

(2) template <typename ForwardIterator, typename Compare>
constexpr ForwardIterator min_element(ForwardIterator first, ForwardIterator last, Compare comp);
```
Finds the smallest element in the range \[first, last). Elements are compared using operator\<.

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
(1) template <typename ForwardIter, typename Compare>
constexpr pair<ForwardIter, ForwardIter> minmax_element(ForwardIter first, ForwardIter last, Compare comp);

(2) template <typename ForwardIter>
constexpr pair<ForwardIter, ForwardIter> minmax_element(ForwardIter first, ForwardIter last);
```

Finds the smallest and greatest element in the range \[first, last).

-----

### Function `etl::all_of`

``` cpp
template <typename InputIter, typename UnaryPredicate>
constexpr bool all_of(InputIter first, InputIter last, UnaryPredicate p);
```

Checks if unary predicate p returns true for all elements in the range \[first, last).

*Complexity:* At most last - first applications of the predicate.

-----

### Function `etl::any_of`

``` cpp
template <typename InputIter, typename UnaryPredicate>
constexpr bool any_of(InputIter first, InputIter last, UnaryPredicate p);
```

Checks if unary predicate p returns true for at least one element in the range \[first, last).

*Complexity:* At most last - first applications of the predicate.

-----

### Function `etl::none_of`

``` cpp
template <typename InputIter, typename UnaryPredicate>
constexpr bool none_of(InputIter first, InputIter last, UnaryPredicate p);
```

Checks if unary predicate p returns true for no elements in the range \[first, last).

*Complexity:* At most last - first applications of the predicate.

-----

### Function `etl::reverse`

``` cpp
template <typename BidirIter>
constexpr void reverse(BidirIter first, BidirIter last);
```

Reverses the order of the elements in the range \[first, last). Behaves as if applying iter\_swap to every pair of iterators first+i, (last-i) - 1 for each non-negative i \< (last-first)/2.

-----

### Function `etl::reverse_copy`

``` cpp
template <typename BidirIter, typename OutputIter>
constexpr OutputIter reverse_copy(BidirIter first, BidirIter last, OutputIter destination);
```

Copies the elements from the range \[ first, last ) to another range beginning at d\_first in such a way that the elements in the new range are in reverse order.

If the source and destination ranges (that is, \[first, last) and \[d\_first, d\_first+(last-first)) respectively) overlap, the behavior is undefined.

-----

### Function `etl::rotate`

``` cpp
template <typename ForwardIter>
constexpr ForwardIter rotate(ForwardIter first, ForwardIter nFirst, ForwardIter last);
```

Performs a left rotation on a range of elements.

Specifically, rotate swaps the elements in the range \[first, last) in such a way that the element n\_first becomes the first element of the new range and n\_first - 1 becomes the last element. A precondition of this function is that \[first, n\_first) and \[n\_first, last) are valid ranges.

-----

### Function `etl::unique` \[Algorithm\]

``` cpp
(1) template <typename ForwardIter, typename BinaryPredicate>
constexpr ForwardIter unique(ForwardIter first, ForwardIter last, BinaryPredicate pred);

(2) template <typename ForwardIter>
constexpr ForwardIter unique(ForwardIter first, ForwardIter last);
```

Eliminates all except the first element from every consecutive group of equivalent elements from the range \[first, last) and returns a past-the-end iterator for the new logical end of the range.

-----

### Function `etl::unique_copy` \[Algorithm\]

``` cpp
(1) template <typename InputIter, typename OutputIter, typename BinaryPredicate>
constexpr OutputIter unique_copy(InputIter first, InputIter last, OutputIter destination, BinaryPredicate pred);

(2) template <typename InputIter, typename OutputIter>
constexpr OutputIter unique_copy(InputIter first, InputIter last, OutputIter destination);
```

Copies the elements from the range \[first, last), to another range beginning at d\_first in such a way that there are no consecutive equal elements. Only the first element of each group of equal elements is copied.
Elements are compared using the given binary predicate pred. The behavior is undefined if it is not an equivalence relation.

-----

### Function `etl::partition`

``` cpp
template <typename ForwardIter, typename UnaryPredicate>
constexpr ForwardIter partition(ForwardIter first, ForwardIter last, UnaryPredicate p);
```

Reorders the elements in the range \[first, last) in such a way that all elements for which the predicate p returns true precede the elements for which predicate p returns false. Relative order of the elements is not preserved.

-----

### Function `etl::partition_copy`

``` cpp
template <typename InputIter, typename OutputIter1, typename OutputIter2, typename UnaryPredicate>
constexpr pair<OutputIter1, OutputIter2> partition_copy(InputIter first, InputIter last, OutputIter1 destinationTrue, OutputIter2 destinationFalse, UnaryPredicate p);
```

Copies the elements from the range \[ first , last ) to two different ranges depending on the value returned by the predicate p. The elements that satisfy the predicate p are copied to the range beginning at destination\_true. The rest of the elements are copied to the range beginning at destination\_false.

The behavior is undefined if the input range overlaps either of the output ranges.

-----

### Function `etl::is_partitioned`

``` cpp
template <typename InputIter, typename UnaryPredicate>
constexpr bool is_partitioned(InputIter first, InputIter last, UnaryPredicate p);
```

Returns true if all elements in the range \[ first , last ) that satisfy the predicate p appear before all elements that don’t. Also returns true if the range is empty.

*Notes:* [cppreference.com](https://en.cppreference.com/w/cpp/algorithm/is_partitioned)

-----

### Function `etl::partition_point`

``` cpp
template <typename ForwardIter, typename UnaryPredicate>
constexpr ForwardIter partition_point(ForwardIter first, ForwardIter last, UnaryPredicate p);
```

Examines the partitioned (as if by partition) range \[ first , last ) and locates the end of the first partition, that is, the first element that does not satisfy p or last if all elements satisfy p.

-----

### Function `etl::stable_partition`

``` cpp
template <typename BidirIter, typename UnaryPredicate>
constexpr BidirIter stable_partition(BidirIter f, BidirIter l, UnaryPredicate p);
```

Reorders the elements in the range \[first, last) in such a way that all elements for which the predicate p returns true precede the elements for which predicate p returns false. Relative order of the elements is preserved.

-----

### Function `etl::copy` \[Algorithm\]

``` cpp
(1) template <typename InputIter, typename OutputIter>
constexpr OutputIter copy(InputIter first, InputIter last, OutputIter destination);

(2) template <typename InputIter, typename OutputIter, typename UnaryPredicate>
constexpr OutputIter copy_if(InputIter first, InputIter last, OutputIter dFirst, UnaryPredicate pred);
```

Copies the elements in the range, defined by \[first, last), to another range beginning at destination.

*Return values:* Output iterator to the element in the destination range, one past the last element copied.

Copies all elements in the range \[first, last) starting from first and proceeding to last - 1. The behavior is undefined if destination is within the range \[first, last). In this case, copy\_backward may be used instead.

-----

### Function `etl::copy_n`

``` cpp
template <typename InputIter, typename Size, typename OutputIter>
constexpr OutputIter copy_n(InputIter first, Size count, OutputIter result);
```

Copies exactly count values from the range beginning at first to the range beginning at result. Formally, for each integer 0 ≤ i \< count, performs \*(result + i) = \*(first + i). Overlap of ranges is formally permitted, but leads to unpredictable ordering of the results.

*Return values:* Iterator in the destination range, pointing past the last element copied if count\>0 or result otherwise.

-----

### Function `etl::copy_backward`

``` cpp
template <typename BidirIter1, typename BidirIter2>
constexpr BidirIter2 copy_backward(BidirIter1 first, BidirIter1 last, BidirIter2 dLast);
```

Copies the elements from the range, defined by \[first, last), to another range ending at d\_last. The elements are copied in reverse order (the last element is copied first), but their relative order is preserved.

*Return values:* Iterator to the last element copied.

The behavior is undefined if d\_last is within (first, last\]. copy must be used instead of copy\_backward in that case.

-----

### Function `etl::rotate_copy`

``` cpp
template <typename ForwardIter, typename OutputIter>
constexpr OutputIter rotate_copy(ForwardIter first, ForwardIter nFirst, ForwardIter last, OutputIter destination);
```

Copies the elements from the range \[ first , last ), to another range beginning at destination in such a way, that the element n\_first becomes the first element of the new range and n\_first - 1 becomes the last element.

-----

### Function `etl::fill`

``` cpp
template <typename ForwardIter, typename T>
constexpr void fill(ForwardIter first, ForwardIter last, T const& value);
```

Assigns the given value to the elements in the range \[first, last).

-----

### Function `etl::fill_n`

``` cpp
template <typename OutputIter, typename Size, typename T>
constexpr OutputIter fill_n(OutputIter first, Size count, T const& value);
```

Assigns the given value to the first count elements in the range beginning at first if count \> 0. Does nothing otherwise.

*Return values:* Iterator one past the last element assigned if count \> 0, first otherwise.

-----

### Function `etl::equal` \[Algorithm\]

``` cpp
(1) template <typename InputIter1, typename InputIter2, typename BinaryPredicate>
constexpr bool equal(InputIter1 first1, InputIter1 last1, InputIter2 first2, BinaryPredicate p);

(2) template <typename InputIter1, typename InputIter2>
constexpr bool equal(InputIter1 first1, InputIter1 last1, InputIter2 first2);

(3) template <typename InputIter1, typename InputIter2, typename BinaryPredicate>
constexpr bool equal(InputIter1 first1, InputIter1 last1, InputIter2 first2, InputIter2 last2, BinaryPredicate p);

(4) template <typename InputIter1, typename InputIter2>
constexpr bool equal(InputIter1 first1, InputIter1 last1, InputIter2 first2, InputIter2 last2);
```

Returns true if the range \[first1, last1) is equal to the range \[first2, first2

  - (last1 - first1)), and false otherwise.

-----

### Function `etl::lexicographical_compare` \[Algorithm\]

``` cpp
(1) template <typename InputIter1, typename InputIter2, typename Compare>
constexpr bool lexicographical_compare(InputIter1 first1, InputIter1 last1, InputIter2 first2, InputIter2 last2, Compare comp);

(2) template <typename InputIter1, typename InputIter2>
constexpr bool lexicographical_compare(InputIter1 first1, InputIter1 last1, InputIter2 first2, InputIter2 last2);
```
Checks if the first range \[first1, last1) is lexicographically less than the second range \[first2, last2). Elements are compared using the given binary comparison function comp.

*Notes:* [cppreference.com](https://en.cppreference.com/w/cpp/algorithm/lexicographical_compare)

-----

### Function `etl::sort` \[Algorithm\]

``` cpp
(1) template <typename RandomIter, typename Compare>
constexpr void sort(RandomIter first, RandomIter last, Compare comp);

(2) template <typename RandomIter>
constexpr void sort(RandomIter first, RandomIter last);
```

Sorts the elements in the range \[first, last) in non-descending order. The order of equal elements is not guaranteed to be preserved.

*Notes:* [cppreference.com](https://en.cppreference.com/w/cpp/algorithm/sort)

A sequence is sorted with respect to a comparator comp if for any iterator it pointing to the sequence and any non-negative integer n such that it + n is a valid iterator pointing to an element of the sequence, comp(\*(it

  - n), \*it) (or \*(it + n) \< \*it) evaluates to false. Bubble sort implementation.

-----

### Function `etl::stable_sort` \[Algorithm\]

``` cpp
(1) template <typename RandomIter, typename Compare>
constexpr void stable_sort(RandomIter first, RandomIter last, Compare cmp);

(2) template <typename RandomIter>
constexpr void stable_sort(RandomIter first, RandomIter last);
```
Sorts the elements in the range \[first, last) in non-descending order. The order of equivalent elements is guaranteed to be preserved. Elements are compared using the given comparison function comp.

*Notes:* [cppreference.com](https://en.cppreference.com/w/cpp/algorithm/stable_sort)

-----

### Function `etl::partial_sort` \[Algorithm\]

``` cpp
(1) template <typename RandomIter, typename Compare>
constexpr void partial_sort(RandomIter first, RandomIter middle, RandomIter last, Compare comp);

(2) template <typename RandomIter>
constexpr void partial_sort(RandomIter first, RandomIter middle, RandomIter last);
```
Rearranges elements such that the range \[first, middle) contains the sorted middle - first smallest elements in the range \[first, last). The order of equal elements is not guaranteed to be preserved. The order of the remaining elements in the range \[middle, last) is unspecified. Elements are compared using the given binary comparison function comp.

*Notes:* [cppreference.com](https://en.cppreference.com/w/cpp/algorithm/partial_sort) \\todo Improve. Currently forwards to regular sort.

-----

### Function `etl::nth_element` \[Algorithm\]

``` cpp
(1) template <typename RandomIter, typename Compare>
constexpr void nth_element(RandomIter first, RandomIter nth, RandomIter last, Compare comp);

(2) template <typename RandomIter>
constexpr void nth_element(RandomIter first, RandomIter nth, RandomIter last);
```

nth\_element is a partial sorting algorithm that rearranges elements in \[first, last) such that: The element pointed at by nth is changed to whatever element would occur in that position if \[first, last) were sorted. All of the elements before this new nth element are less than or equal to the elements after the new nth element.

*Notes:* [cppreference.com](https://en.cppreference.com/w/cpp/algorithm/nth_element) \\todo Improve. Currently forwards to regular sort.

-----

### Function `etl::is_sorted_until` \[Algorithm\]

``` cpp
(1) template <typename ForwardIter>
constexpr ForwardIter is_sorted_until(ForwardIter first, ForwardIter last);

(2) template <typename ForwardIter, typename Compare>
constexpr ForwardIter is_sorted_until(ForwardIter first, ForwardIter last, Compare comp);
```

Examines the range \[first, last) and finds the largest range beginning at first in which the elements are sorted in non-descending order.

-----

### Function `etl::is_sorted` \[Algorithm\]

``` cpp
(1) template <typename ForwardIter>
constexpr bool is_sorted(ForwardIter first, ForwardIter last);

(2) template <typename ForwardIter, typename Compare>
constexpr bool is_sorted(ForwardIter first, ForwardIter last, Compare comp);
```

Checks if the elements in range \[first, last) are sorted in non-descending order.

-----

### Function `etl::lower_bound` \[Algorithm\]

``` cpp
(1) template <typename ForwardIter, typename T, typename Compare>
constexpr ForwardIter lower_bound(ForwardIter first, ForwardIter last, T const& value, Compare comp) noexcept;

(2) template <typename ForwardIter, typename T>
constexpr ForwardIter lower_bound(ForwardIter first, ForwardIter last, T const& value) noexcept;
```

Returns an iterator pointing to the first element in the range \[first, last) that is not less than (i.e. greater or equal to) value, or last if no such element is found.

*Notes:* [cppreference.com](https://en.cppreference.com/w/cpp/algorithm/lower_bound)

-----

### Function `etl::upper_bound` \[Algorithm\]

``` cpp
(1) template <typename ForwardIter, typename T, typename Compare>
constexpr ForwardIter upper_bound(ForwardIter first, ForwardIter last, T const& value, Compare comp);

(2) template <typename ForwardIter, typename T>
constexpr ForwardIter upper_bound(ForwardIter first, ForwardIter last, T const& value);
```

Returns an iterator pointing to the first element in the range \[ first , last ) that is greater than value, or last if no such element is found.

The range \[ first , last ) must be partitioned with respect to the expression \!(value \< element) or \!comp(value, element), i.e., all elements for which the expression is true must precede all elements for which the expression is false. A fully-sorted range meets this criterion.

-----

### Function `etl::equal_range` \[Algorithm\]

``` cpp
(1) template <typename ForwardIt, typename T, typename Compare>
constexpr pair<ForwardIt, ForwardIt> equal_range(ForwardIt first, ForwardIt last, T const& value, Compare comp);

(2) template <typename ForwardIt, typename T>
constexpr pair<ForwardIt, ForwardIt> equal_range(ForwardIt first, ForwardIt last, T const& value);
```

Returns a range containing all elements equivalent to value in the range \[first, last).

*Notes:* [cppreference.com](https://en.cppreference.com/w/cpp/algorithm/equal_range)

-----

### Function `etl::binary_search` \[Algorithm\]

``` cpp
(1) template <typename ForwardIter, typename T, typename Compare>
constexpr bool binary_search(ForwardIter first, ForwardIter last, T const& value, Compare comp);

(2) template <typename ForwardIter, class T>
constexpr bool binary_search(ForwardIter first, ForwardIter last, T const& value);
```

Checks if an element equivalent to value appears within the range \[ first , last ).

*Notes:* [cppreference.com](https://en.cppreference.com/w/cpp/algorithm/binary_search)

For binary\_search to succeed, the range \[ first , last ) must be at least partially ordered with respect to value

-----

### Function `etl::merge` \[Algorithm\]

``` cpp
(1) template <typename InputIt1, typename InputIt2, typename OutputIt, typename Compare>
constexpr OutputIt merge(InputIt1 first1, InputIt1 last1, InputIt2 first2, InputIt2 last2, OutputIt destination, Compare comp);

(2) template <typename InputIt1, typename InputIt2, typename OutputIt>
constexpr OutputIt merge(InputIt1 first1, InputIt1 last1, InputIt2 first2, InputIt2 last2, OutputIt destination);
```
Merges two sorted ranges \[first1, last1) and \[first2, last2) into one sorted range beginning at d\_first. Elements are compared using the given binary comparison function comp.

-----

### Function `etl::includes` \[Algorithm\]

``` cpp
(1) template <typename InputIter1, typename InputIter2>
constexpr bool includes(InputIter1 first1, InputIter1 last1, InputIter2 first2, InputIter2 last2);

(2) template <typename InputIter1, typename InputIter2, typename Compare>
constexpr bool includes(InputIter1 first1, InputIter1 last1, InputIter2 first2, InputIter2 last2, Compare comp);
```

Returns true if the sorted range \[first2, last2) is a subsequence of the sorted range \[first1, last1). Both ranges must be sorted with operator\<.

-----

### Function `etl::set_difference` \[Algorithm\]

``` cpp
(1) template <typename InputIt1, typename InputIt2, typename OutputIt, typename Compare>
constexpr OutputIt set_difference(InputIt1 first1, InputIt1 last1, InputIt2 first2, InputIt2 last2, OutputIt destination, Compare comp);

(2) template <typename InputIt1, typename InputIt2, typename OutputIt>
constexpr OutputIt set_difference(InputIt1 first1, InputIt1 last1, InputIt2 first2, InputIt2 last2, OutputIt destination);
```
Copies the elements from the sorted range \[first1, last1) which are not found in the sorted range \[first2, last2) to the range beginning at destination. Elements are compared using the given binary comparison function comp and the ranges must be sorted with respect to the same.

-----

### Function `etl::set_intersection` \[Algorithm\]

``` cpp
(1) template <typename InputIt1, typename InputIt2, typename OutputIt, typename Compare>
constexpr OutputIt set_intersection(InputIt1 first1, InputIt1 last1, InputIt2 first2, InputIt2 last2, OutputIt dest, Compare comp);

(2) template <typename InputIt1, typename InputIt2, typename OutputIt>
constexpr OutputIt set_intersection(InputIt1 first1, InputIt1 last1, InputIt2 first2, InputIt2 last2, OutputIt dest);
```

Constructs a sorted range beginning at d\_first consisting of elements that are found in both sorted ranges \[first1, last1) and \[first2, last2). If some element is found m times in \[first1, last1) and n times in \[first2, last2), the first min(m, n) elements will be copied from the first range to the destination range. The order of equivalent elements is preserved. The resulting range cannot overlap with either of the input ranges.

-----

### Function `etl::set_symmetric_difference` \[Algorithm\]

``` cpp
(1) template <typename InputIter1, typename InputIter2, typename OutputIter, typename Compare>
constexpr OutputIter set_symmetric_difference(InputIter1 first1, InputIter1 last1, InputIter2 first2, InputIter2 last2, OutputIter destination, Compare comp);

(2) template <typename InputIter1, typename InputIter2, typename OutputIter>
constexpr OutputIter set_symmetric_difference(InputIter1 first1, InputIter1 last1, InputIter2 first2, InputIter2 last2, OutputIter dest);
```
Computes symmetric difference of two sorted ranges: the elements that are found in either of the ranges, but not in both of them are copied to the range beginning at destination. The resulting range is also sorted. Elements are compared using the given binary comparison function comp and the ranges must be sorted with respect to the same.

-----

### Function `etl::set_union` \[Algorithm\]

``` cpp
(1) template <typename InputIter1, typename InputIter2, typename OutputIter, typename Compare>
constexpr OutputIter set_union(InputIter1 first1, InputIter1 last1, InputIter2 first2, InputIter2 last2, OutputIter destination, Compare comp);

(2) template <typename InputIter1, typename InputIter2, typename OutputIter>
constexpr OutputIter set_union(InputIter1 first1, InputIter1 last1, InputIter2 first2, InputIter2 last2, OutputIter destination);
```
Constructs a sorted union beginning at destination consisting of the set of elements present in one or both sorted ranges \[first1, last1) and \[first2, last2). The resulting range cannot overlap with either of the input ranges. (1) Elements are compared using the given binary comparison function comp and the ranges must be sorted with respect to the same. (2) Elements are compared using operator\< and the ranges must be sorted with respect to the same.

-----

### Function `etl::is_permutation` \[Algorithm\]

``` cpp
(1) template <typename ForwardIter1, typename ForwardIter2>
constexpr bool is_permutation(ForwardIter1 first, ForwardIter1 last, ForwardIter2 first2);

(2) template <typename ForwardIter1, typename ForwardIter2>
constexpr bool is_permutation(ForwardIter1 first1, ForwardIter1 last1, ForwardIter2 first2, ForwardIter2 last2);
```

Returns true if there exists a permutation of the elements in the range \[first1, last1) that makes that range equal to the range \[first2,last2), where last2 denotes first2 + (last1 - first1) if it was not given.
Elements are compared using operator==. The behavior is undefined if it is not an equivalence relation.

-----
