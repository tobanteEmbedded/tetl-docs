---
title: "numeric.hpp"
---

# Header file `numeric.hpp`

``` cpp
#include "etl/version.hpp"
#include "etl/cstddef.hpp"
#include "etl/functional.hpp"
#include "etl/limits.hpp"
#include "etl/type_traits.hpp"
#include "etl/utility.hpp"

namespace etl
{
    //=== accumulate ===//
    template <typename InputIt, typename Type>
    constexpr Type accumulate(InputIt first, InputIt last, Type init) noexcept;
    template <typename InputIt, typename Type, typename BinaryOperation>
    constexpr Type accumulate(InputIt first, InputIt last, Type init, BinaryOperation op) noexcept;

    //=== reduce ===//
    template <typename InputIter, typename T, typename BinaryOp>
    constexpr T reduce(InputIter first, InputIter last, T init, BinaryOp op);
    template <typename InputIter, typename T>
    constexpr T reduce(InputIter first, InputIter last, T init);
    template <typename InputIter>
    constexpr typename etl::iterator_traits<InputIter>::value_type reduce(InputIter first, InputIter last);

    //=== adjacent_difference ===//
    template <typename InputIt, typename OutputIt, typename BinaryOperation>
    constexpr OutputIt adjacent_difference(InputIt first, InputIt last, OutputIt destination, BinaryOperation op);
    template <typename InputIt, typename OutputIt>
    constexpr OutputIt adjacent_difference(InputIt first, InputIt last, OutputIt destination);

    //=== inner_product ===//
    template <typename InputIt1, typename InputIt2, typename T>
    constexpr T inner_product(InputIt1 first1, InputIt1 last1, InputIt2 first2, T init);
    template <typename InputIt1, typename InputIt2, typename T, typename BinaryOperation1, typename BinaryOperation2>
    constexpr T inner_product(InputIt1 first1, InputIt1 last1, InputIt2 first2, T init, BinaryOperation1 op1, BinaryOperation2 op2);

    //=== partial_sum ===//
    template <typename InputIt, typename OutputIt, typename BinaryOperation>
    constexpr OutputIt partial_sum(InputIt first, InputIt last, OutputIt destination, BinaryOperation op);
    template <typename InputIt, typename OutputIt>
    constexpr OutputIt partial_sum(InputIt first, InputIt last, OutputIt destination);

    //=== iota ===//
    template <typename ForwardIt, typename T>
    constexpr void iota(ForwardIt first, ForwardIt last, T value);

    template <typename M, typename N>
    constexpr etl::common_type_t<M, N> gcd(M m, N n) noexcept;

    template <typename M, typename N, int _concept_requires_244 = 42, ::etl::enable_if_t<(_concept_requires_244 == 43) || ((is_integral_v<M> && !is_same_v<M, bool> && is_integral_v<N> && !is_same_v<N, bool>)), int> = 0>
    constexpr etl::common_type_t<M, N> lcm(M m, N n);

    template <typename Type>
    constexpr Type abs(Type input) noexcept;

    //=== midpoint ===//
    template <typename Int, int _concept_requires_280 = 42, ::etl::enable_if_t<(_concept_requires_280 == 43) || ((is_integral_v<Int> && !is_same_v<Int, bool>)), int> = 0>
    constexpr Int midpoint(Int a, Int b) noexcept;
    template <typename Float, int _concept_requires_301 = 42, ::etl::enable_if_t<(_concept_requires_301 == 43) || (is_floating_point_v<Float>), int> = 0>
    constexpr Float midpoint(Float a, Float b) noexcept;
    template <typename Pointer>
    constexpr enable_if_t<is_pointer_v<Pointer>, Pointer> midpoint(Pointer a, Pointer b) noexcept;
}
```

### Function `etl::accumulate` \[Algorithm\]

``` cpp
(1) template <typename InputIt, typename Type>
constexpr Type accumulate(InputIt first, InputIt last, Type init) noexcept;

(2) template <typename InputIt, typename Type, typename BinaryOperation>
constexpr Type accumulate(InputIt first, InputIt last, Type init, BinaryOperation op) noexcept;
```

Computes the sum of the given value init and the elements in the range `[first, last)`.

*Notes:* [cppreference.com/w/cpp/algorithm/accumulate](https://en.cppreference.com/w/cpp/algorithm/accumulate)

1.  Uses `operator+` to sum up the elements.

2.  Uses the BinaryOperation to sum up the elements.

-----

### Function `etl::reduce` \[Algorithm\]

``` cpp
(1) template <typename InputIter, typename T, typename BinaryOp>
constexpr T reduce(InputIter first, InputIter last, T init, BinaryOp op);

(2) template <typename InputIter, typename T>
constexpr T reduce(InputIter first, InputIter last, T init);

(3) template <typename InputIter>
constexpr typename etl::iterator_traits<InputIter>::value_type reduce(InputIter first, InputIter last);
```

Similar to etl::accumulate.

*Notes:* [cppreference.com/w/cpp/algorithm/reduce](https://en.cppreference.com/w/cpp/algorithm/reduce)

-----

### Function `etl::adjacent_difference` \[Algorithm\]

``` cpp
(1) template <typename InputIt, typename OutputIt, typename BinaryOperation>
constexpr OutputIt adjacent_difference(InputIt first, InputIt last, OutputIt destination, BinaryOperation op);

(2) template <typename InputIt, typename OutputIt>
constexpr OutputIt adjacent_difference(InputIt first, InputIt last, OutputIt destination);
```

Computes the differences between the second and the first of each adjacent pair of elements of the range \[first, last) and writes them to the range beginning at destination + 1. An unmodified copy of \*first is written to \*destination.

-----

### Function `etl::inner_product` \[Algorithm\]

``` cpp
(1) template <typename InputIt1, typename InputIt2, typename T>
constexpr T inner_product(InputIt1 first1, InputIt1 last1, InputIt2 first2, T init);

(2) template <typename InputIt1, typename InputIt2, typename T, typename BinaryOperation1, typename BinaryOperation2>
constexpr T inner_product(InputIt1 first1, InputIt1 last1, InputIt2 first2, T init, BinaryOperation1 op1, BinaryOperation2 op2);
```

Computes inner product (i.e. sum of products) or performs ordered map/reduce operation on the range \[first1, last1) and the range beginning at first2.

-----

### Function `etl::partial_sum` \[Algorithm\]

``` cpp
(1) template <typename InputIt, typename OutputIt, typename BinaryOperation>
constexpr OutputIt partial_sum(InputIt first, InputIt last, OutputIt destination, BinaryOperation op);

(2) template <typename InputIt, typename OutputIt>
constexpr OutputIt partial_sum(InputIt first, InputIt last, OutputIt destination);
```

Computes the partial sums of the elements in the subranges of the range \[first, last) and writes them to the range beginning at destination. This version uses the given binary function op, both applying etl::move to their operands on the left hand side.

*Notes:* [cppreference.com/w/cpp/algorithm/partial\_sum](https://en.cppreference.com/w/cpp/algorithm/partial_sum)

*Return values:* Iterator to the element past the last element written.

BinaryFunction must not invalidate any iterators, including the end iterators, or modify any elements of the range involved.

-----

### Function `etl::iota` \[Algorithm\]

``` cpp
(1) template <typename ForwardIt, typename T>
constexpr void iota(ForwardIt first, ForwardIt last, T value);
```

Fills the range \[first, last) with sequentially increasing values, starting with value and repetitively evaluating ++value.

-----

### Function `etl::gcd`

``` cpp
template <typename M, typename N>
constexpr etl::common_type_t<M, N> gcd(M m, N n) noexcept;
```

Computes the greatest common divisor of the integers m and n.

*Return values:* If both m and n are zero, returns zero. Otherwise, returns the greatest common divisor of |m| and |n|.

-----

### Function `etl::lcm`

``` cpp
template <typename M, typename N, int _concept_requires_244 = 42, ::etl::enable_if_t<(_concept_requires_244 == 43) || ((is_integral_v<M> && !is_same_v<M, bool> && is_integral_v<N> && !is_same_v<N, bool>)), int> = 0>
constexpr etl::common_type_t<M, N> lcm(M m, N n);
```

Computes the least common multiple of the integers m and n.

*Return values:* If either m or n is zero, returns zero. Otherwise, returns the least common multiple of |m| and |n|.

-----

### Function `etl::abs`

``` cpp
template <typename Type>
constexpr Type abs(Type input) noexcept;
```

Returns the absolute value.

-----

### Function `etl::midpoint`

``` cpp
(1) template <typename Int, int _concept_requires_280 = 42, ::etl::enable_if_t<(_concept_requires_280 == 43) || ((is_integral_v<Int> && !is_same_v<Int, bool>)), int> = 0>
constexpr Int midpoint(Int a, Int b) noexcept;

(2) template <typename Float, int _concept_requires_301 = 42, ::etl::enable_if_t<(_concept_requires_301 == 43) || (is_floating_point_v<Float>), int> = 0>
constexpr Float midpoint(Float a, Float b) noexcept;

(3) template <typename Pointer>
constexpr enable_if_t<is_pointer_v<Pointer>, Pointer> midpoint(Pointer a, Pointer b) noexcept;
```

Returns half the sum of a + b. If the sum is odd, the result is rounded towards a.

*Notes:* [.youtube.com/watch?v=sBtAGxBh-XI](https://www.youtube.com/watch?v=sBtAGxBh-XI)

*Notes:* [cppreference.com/w/cpp/numeric/midpoint](https://en.cppreference.com/w/cpp/numeric/midpoint)

CppCon 2019: Marshall Clow “midpoint? How Hard Could it Be?”

-----
