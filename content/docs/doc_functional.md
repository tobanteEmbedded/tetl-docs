---
title: "functional.hpp"
---

# Header file `functional.hpp`

``` cpp
#include "etl/version.hpp"
#include "etl/cstddef.hpp"
#include "etl/iterator.hpp"
#include "etl/new.hpp"
#include "etl/utility.hpp"

namespace etl
{
    //=== plus ===//
    template <typename T = void>
    struct plus;
    template <>
    struct plus<void>;

    //=== minus ===//
    template <typename T = void>
    struct minus;
    template <>
    struct minus<void>;

    //=== multiplies ===//
    template <typename T = void>
    struct multiplies;
    template <>
    struct multiplies<void>;

    //=== divides ===//
    template <typename T = void>
    struct divides;
    template <>
    struct divides<void>;

    //=== modulus ===//
    template <typename T = void>
    struct modulus;
    template <>
    struct modulus<void>;

    //=== negate ===//
    template <typename T = void>
    struct negate;
    template <>
    struct negate<void>;

    //=== equal_to ===//
    template <typename T = void>
    struct equal_to;
    template <>
    struct equal_to<void>;

    //=== not_equal_to ===//
    template <typename T = void>
    struct not_equal_to;
    template <>
    struct not_equal_to<void>;

    //=== greater ===//
    template <typename T = void>
    struct greater;
    template <>
    struct greater<void>;

    //=== greater_equal ===//
    template <typename T = void>
    struct greater_equal;
    template <>
    struct greater_equal<void>;

    //=== less ===//
    template <typename T = void>
    struct less;
    template <>
    struct less<void>;

    //=== less_equal ===//
    template <typename T = void>
    struct less_equal;
    template <>
    struct less_equal<void>;

    //=== logical_and ===//
    template <typename T = void>
    struct logical_and;
    template <>
    struct logical_and<void>;

    //=== logical_or ===//
    template <typename T = void>
    struct logical_or;
    template <>
    struct logical_or<void>;

    //=== logical_not ===//
    template <typename T = void>
    struct logical_not;
    template <>
    struct logical_not<void>;

    //=== bit_and ===//
    template <typename T = void>
    struct bit_and;
    template <>
    struct bit_and<void>;

    //=== bit_or ===//
    template <typename T = void>
    struct bit_or;
    template <>
    struct bit_or<void>;

    //=== bit_xor ===//
    template <typename T = void>
    struct bit_xor;
    template <>
    struct bit_xor<void>;

    //=== bit_not ===//
    template <typename T = void>
    struct bit_not;
    template <>
    struct bit_not<void>;

    template <typename T>
    struct reference_wrapper;

    template <typename T>
    constexpr reference_wrapper<T> ref(T& t) noexcept;

    template <typename T>
    constexpr reference_wrapper<T> ref(reference_wrapper<T> t) noexcept;

    //=== cref ===//
    template <typename T>
    constexpr reference_wrapper<const T> cref(T const& t) noexcept;
    template <typename T>
    constexpr reference_wrapper<const T> cref(reference_wrapper<T> t) noexcept;
    template <typename T>
    void cref(T const&&) = delete;

    //=== function_view ===//
    template <typename>
    struct function_view;
    template <typename Res, typename ... Args>
    struct function_view<Res(Args...)>;

    //=== function ===//
    template <etl::size_t, typename>
    struct function;
    template <etl::size_t Capacity, typename Res, typename ... Args>
    struct function<Capacity, Res(Args...)>;

    template <typename ForwardIter, typename Predicate = equal_to<>>>
    class default_searcher;

    //=== hash ===//
    template <typename T>
    struct hash;
    template <>
    struct hash<bool>;
    template <>
    struct hash<char>;
    template <>
    struct hash<signed char>;
    template <>
    struct hash<unsigned char>;
    template <>
    struct hash<char16_t>;
    template <>
    struct hash<char32_t>;
    template <>
    struct hash<wchar_t>;
    template <>
    struct hash<short>;
    template <>
    struct hash<unsigned short>;
    template <>
    struct hash<int>;
    template <>
    struct hash<unsigned int>;
    template <>
    struct hash<long>;
    template <>
    struct hash<long long>;
    template <>
    struct hash<unsigned long>;
    template <>
    struct hash<unsigned long long>;
    template <>
    struct hash<float>;
    template <>
    struct hash<double>;
    template <>
    struct hash<long double>;
    template <>
    struct hash<etl::nullptr_t>;
    template <typename T>
    struct hash<T*>;
}
```

### Struct `etl::plus` \[Utility\]

``` cpp
(1) template <typename T = void>
struct plus
{
    constexpr T operator()(T const& lhs, T const& rhs) const;
};

(2) template <>
struct plus<void>
{
    template <typename T, typename U>
    constexpr decltype(forward<T>(lhs)+forward<U>(rhs)) operator()(T&& lhs, U&& rhs) const;
};
```

Function object for performing addition. Effectively calls operator+ on two instances of type T.

*Notes:* [cppreference.com/w/cpp/utility/functional/plus](https://en.cppreference.com/w/cpp/utility/functional/plus)

### Function `etl::plus::operator()`

``` cpp
constexpr T operator()(T const& lhs, T const& rhs) const;
```

Returns the sum of lhs and rhs.

-----

-----

### Struct `etl::minus` \[Utility\]

``` cpp
(1) template <typename T = void>
struct minus
{
    constexpr T operator()(T const& lhs, T const& rhs) const;
};

(2) template <>
struct minus<void>
{
    template <typename T, typename U>
    constexpr decltype(etl::forward<T>(lhs)-etl::forward<U>(rhs)) operator()(T&& lhs, U&& rhs) const;
};
```

Function object for performing subtraction. Effectively calls operator- on two instances of type T.

*Notes:* [cppreference.com/w/cpp/utility/functional/minus](https://en.cppreference.com/w/cpp/utility/functional/minus)

### Function `etl::minus::operator()`

``` cpp
constexpr T operator()(T const& lhs, T const& rhs) const;
```

Returns the difference between lhs and rhs.

-----

-----

### Struct `etl::multiplies` \[Utility\]

``` cpp
(1) template <typename T = void>
struct multiplies
{
    constexpr T operator()(T const& lhs, T const& rhs) const;
};

(2) template <>
struct multiplies<void>
{
    template <typename T, typename U>
    constexpr decltype(etl::forward<T>(lhs)*etl::forward<U>(rhs)) operator()(T&& lhs, U&& rhs) const;
};
```

Function object for performing multiplication. Effectively calls operator\* on two instances of type T.

*Notes:* [cppreference.com/w/cpp/utility/functional/multiplies](https://en.cppreference.com/w/cpp/utility/functional/multiplies)

### Function `etl::multiplies::operator()`

``` cpp
constexpr T operator()(T const& lhs, T const& rhs) const;
```

Returns the product between lhs and rhs.

-----

-----

### Struct `etl::divides` \[Utility\]

``` cpp
(1) template <typename T = void>
struct divides
{
};

(2) template <>
struct divides<void>
{
};
```

Function object for performing division. Effectively calls operator/ on two instances of type T.

*Notes:* [cppreference.com/w/cpp/utility/functional/divides](https://en.cppreference.com/w/cpp/utility/functional/divides)

-----

### Struct `etl::modulus` \[Utility\]

``` cpp
(1) template <typename T = void>
struct modulus
{
};

(2) template <>
struct modulus<void>
{
};
```

Function object for computing remainders of divisions. Implements operator% for type T.

*Notes:* [cppreference.com/w/cpp/utility/functional/modulus](https://en.cppreference.com/w/cpp/utility/functional/modulus)

-----

### Struct `etl::negate` \[Utility\]

``` cpp
(1) template <typename T = void>
struct negate
{
};

(2) template <>
struct negate<void>
{
};
```

Function object for performing negation. Effectively calls operator- on an instance of type T.

*Notes:* [cppreference.com/w/cpp/utility/functional/negate](https://en.cppreference.com/w/cpp/utility/functional/negate)

-----

### Struct `etl::equal_to` \[Utility\]

``` cpp
(1) template <typename T = void>
struct equal_to
{
};

(2) template <>
struct equal_to<void>
{
};
```

Function object for performing comparisons. Unless specialised, invokes operator== on type T.

*Notes:* [cppreference.com/w/cpp/utility/functional/equal\_to](https://en.cppreference.com/w/cpp/utility/functional/equal_to)

-----

### Struct `etl::not_equal_to` \[Utility\]

``` cpp
(1) template <typename T = void>
struct not_equal_to
{
};

(2) template <>
struct not_equal_to<void>
{
};
```

Function object for performing comparisons. Unless specialised, invokes operator\!= on type T.

*Notes:* [cppreference.com/w/cpp/utility/functional/not\_equal\_to](https://en.cppreference.com/w/cpp/utility/functional/not_equal_to)

-----

### Struct `etl::greater` \[Utility\]

``` cpp
(1) template <typename T = void>
struct greater
{
};

(2) template <>
struct greater<void>
{
};
```

Function object for performing comparisons. Unless specialised, invokes operator\> on type T.

*Notes:* [cppreference.com/w/cpp/utility/functional/greater](https://en.cppreference.com/w/cpp/utility/functional/greater)

-----

### Struct `etl::greater_equal` \[Utility\]

``` cpp
(1) template <typename T = void>
struct greater_equal
{
};

(2) template <>
struct greater_equal<void>
{
};
```

Function object for performing comparisons. Unless specialised, invokes operator\>= on type T.

*Notes:* [cppreference.com/w/cpp/utility/functional/greater\_equal](https://en.cppreference.com/w/cpp/utility/functional/greater_equal)

-----

### Struct `etl::less` \[Utility\]

``` cpp
(1) template <typename T = void>
struct less
{
};

(2) template <>
struct less<void>
{
};
```

Function object for performing comparisons. Unless specialised, invokes operator\< on type T.

*Notes:* [cppreference.com/w/cpp/utility/functional/less](https://en.cppreference.com/w/cpp/utility/functional/less)

-----

### Struct `etl::less_equal` \[Utility\]

``` cpp
(1) template <typename T = void>
struct less_equal
{
};

(2) template <>
struct less_equal<void>
{
};
```

Function object for performing comparisons. Unless specialised, invokes operator\<= on type T.

*Notes:* [cppreference.com/w/cpp/utility/functional/less\_equal](https://en.cppreference.com/w/cpp/utility/functional/less_equal)

-----

### Struct `etl::logical_and` \[Utility\]

``` cpp
(1) template <typename T = void>
struct logical_and
{
};

(2) template <>
struct logical_and<void>
{
};
```

Function object for performing logical AND (logical conjunction). Effectively calls operator&& on type T.

*Notes:* [cppreference.com/w/cpp/utility/functional/logical\_and](https://en.cppreference.com/w/cpp/utility/functional/logical_and)

-----

### Struct `etl::logical_or` \[Utility\]

``` cpp
(1) template <typename T = void>
struct logical_or
{
};

(2) template <>
struct logical_or<void>
{
};
```

Function object for performing logical OR (logical disjunction). Effectively calls operator|| on type T.

*Notes:* [cppreference.com/w/cpp/utility/functional/logical\_or](https://en.cppreference.com/w/cpp/utility/functional/logical_or)

-----

### Struct `etl::logical_not` \[Utility\]

``` cpp
(1) template <typename T = void>
struct logical_not
{
};

(2) template <>
struct logical_not<void>
{
};
```

Function object for performing logical NOT (logical negation). Effectively calls operator\! for type T.

*Notes:* [cppreference.com/w/cpp/utility/functional/logical\_not](https://en.cppreference.com/w/cpp/utility/functional/logical_not)

-----

### Struct `etl::bit_and` \[Utility\]

``` cpp
(1) template <typename T = void>
struct bit_and
{
};

(2) template <>
struct bit_and<void>
{
};
```

Function object for performing bitwise AND. Effectively calls operator& on type T.

*Notes:* [cppreference.com/w/cpp/utility/functional/bit\_and](https://en.cppreference.com/w/cpp/utility/functional/bit_and)

-----

### Struct `etl::bit_or` \[Utility\]

``` cpp
(1) template <typename T = void>
struct bit_or
{
};

(2) template <>
struct bit_or<void>
{
};
```

Function object for performing bitwise OR. Effectively calls operator| on type T.

*Notes:* [cppreference.com/w/cpp/utility/functional/bit\_or](https://en.cppreference.com/w/cpp/utility/functional/bit_or)

-----

### Struct `etl::bit_xor` \[Utility\]

``` cpp
(1) template <typename T = void>
struct bit_xor
{
};

(2) template <>
struct bit_xor<void>
{
};
```

Function object for performing bitwise XOR. Effectively calls operator^ on type T.

*Notes:* [cppreference.com/w/cpp/utility/functional/bit\_xor](https://en.cppreference.com/w/cpp/utility/functional/bit_xor)

-----

### Struct `etl::bit_not` \[Utility\]

``` cpp
(1) template <typename T = void>
struct bit_not
{
};

(2) template <>
struct bit_not<void>
{
};
```

Function object for performing bitwise NOT. Effectively calls operator\~ on type T.

*Notes:* [cppreference.com/w/cpp/utility/functional/bit\_not](https://en.cppreference.com/w/cpp/utility/functional/bit_not)

-----

### Struct `etl::reference_wrapper`

``` cpp
template <typename T>
struct reference_wrapper
{
    template <typename U, typename = decltype(detail::FUN<T>(declval<U>()),enable_if_t<!is_same_v<reference_wrapper,remove_cvref_t<U>>>())>
    constexpr reference_wrapper(U&& u) noexcept('hidden');

    constexpr reference_wrapper(const reference_wrapper<T>& x) noexcept = default;

    constexpr reference_wrapper<T>& operator=(const reference_wrapper<T>& x) noexcept = default;

    constexpr operator 'hidden'&() const noexcept;

    constexpr 'hidden'& get() const noexcept;

    template <typename ... Args>
    constexpr invoke_result_t<T &, Args...> operator()(Args &&... args) const noexcept('hidden');
};
```

reference\_wrapper is a class template that wraps a reference in a copyable, assignable object. It is frequently used as a mechanism to store references inside standard containers (like etl::static\_vector) which cannot normally hold references. Specifically, reference\_wrapper is a CopyConstructible and CopyAssignable wrapper around a reference to object or reference to function of type T. Instances of reference\_wrapper are objects (they can be copied or stored in containers) but they are implicitly convertible to T&, so that they can be used as arguments with the functions that take the underlying type by reference. If the stored reference is Callable, reference\_wrapper is callable with the same arguments.

### Constructor `etl::reference_wrapper::reference_wrapper`

``` cpp
template <typename U, typename = decltype(detail::FUN<T>(declval<U>()),enable_if_t<!is_same_v<reference_wrapper,remove_cvref_t<U>>>())>
constexpr reference_wrapper(U&& u) noexcept('hidden');
```

Constructs a new reference wrapper. Converts x to T& as if by T& t = forward\<U\>(x);, then stores a reference to t. This overload only participates in overload resolution if decay\_t\<U\> is not the same type as reference\_wrapper and the expression FUN(declval\<U\>()) is well-formed, where FUN names the set of imaginary functions:

*Notes:* [cppreference.com/w/cpp/utility/functional/reference\_wrapper/reference\_wrapper](https://en.cppreference.com/w/cpp/utility/functional/reference_wrapper/reference_wrapper)

void FUN(T&) noexcept; void FUN(T&&) = delete;

-----

### Constructor `etl::reference_wrapper::reference_wrapper`

``` cpp
constexpr reference_wrapper(const reference_wrapper<T>& x) noexcept = default;
```

Constructs a new reference wrapper. Copy constructor. Stores a reference to other.get().

-----

### Function `etl::reference_wrapper::operator=`

``` cpp
constexpr reference_wrapper<T>& operator=(const reference_wrapper<T>& x) noexcept = default;
```

Copy assignment operator. Drops the current reference and stores a reference to other.get().

-----

### Conversion operator `etl::reference_wrapper::operator type&`

``` cpp
constexpr operator 'hidden'&() const noexcept;
```

Returns the stored reference.

-----

### Function `etl::reference_wrapper::get`

``` cpp
constexpr 'hidden'& get() const noexcept;
```

Returns the stored reference.

-----

### Function `etl::reference_wrapper::operator()`

``` cpp
template <typename ... Args>
constexpr invoke_result_t<T &, Args...> operator()(Args &&... args) const noexcept('hidden');
```

Calls the Callable object, reference to which is stored. This function is available only if the stored reference points to a Callable object. T must be a complete type.

*Return values:* The return value of the called function.

-----

-----

### Function `etl::ref`

``` cpp
template <typename T>
constexpr reference_wrapper<T> ref(T& t) noexcept;
```
Function templates ref and cref are helper functions that generate an object of type reference\_wrapper, using template argument deduction to determine the template argument of the result.

-----

### Function `etl::ref`

``` cpp
template <typename T>
constexpr reference_wrapper<T> ref(reference_wrapper<T> t) noexcept;
```
Function templates ref and cref are helper functions that generate an object of type reference\_wrapper, using template argument deduction to determine the template argument of the result.

-----

### Function `etl::cref`

``` cpp
(1) template <typename T>
constexpr reference_wrapper<const T> cref(T const& t) noexcept;

(2) template <typename T>
constexpr reference_wrapper<const T> cref(reference_wrapper<T> t) noexcept;

(3) template <typename T>
void cref(T const&&) = delete;
```
Function templates ref and cref are helper functions that generate an object of type reference\_wrapper, using template argument deduction to determine the template argument of the result.

module Utility

-----

### Struct `etl::function_view` \[Utility\]

``` cpp
(1) template <typename>
struct function_view;

(2) template <typename Res, typename ... Args>
struct function_view<Res(Args...)>
{
};
```

function\_view

-----

### Struct `etl::function` \[Utility\]

``` cpp
(1) template <etl::size_t, typename>
struct function;

(2) template <etl::size_t Capacity, typename Res, typename ... Args>
struct function<Capacity, Res(Args...)>
{
};
```

function

-----

### Class `etl::default_searcher` \[Utility\]

``` cpp
template <typename ForwardIter, typename Predicate = equal_to<>>>
class default_searcher
{
};
```

Default searcher. A class suitable for use with Searcher overload of etl::search that delegates the search operation to the pre-C++17 standard library’s etl::search.

-----

### Struct `etl::hash` \[Utility\]

``` cpp
(1) template <typename T>
struct hash;

(2) template <>
struct hash<bool>
{
};

(3) template <>
struct hash<char>
{
};

(4) template <>
struct hash<signed char>
{
};

(5) template <>
struct hash<unsigned char>
{
};

(6) template <>
struct hash<char16_t>
{
};

(7) template <>
struct hash<char32_t>
{
};

(8) template <>
struct hash<wchar_t>
{
};

(9) template <>
struct hash<short>
{
};

(10) template <>
struct hash<unsigned short>
{
};

(11) template <>
struct hash<int>
{
};

(12) template <>
struct hash<unsigned int>
{
};

(13) template <>
struct hash<long>
{
};

(14) template <>
struct hash<long long>
{
};

(15) template <>
struct hash<unsigned long>
{
};

(16) template <>
struct hash<unsigned long long>
{
};

(17) template <>
struct hash<float>
{
};

(18) template <>
struct hash<double>
{
};

(19) template <>
struct hash<long double>
{
};

(20) template <>
struct hash<etl::nullptr_t>
{
};

(21) template <typename T>
struct hash<T*>
{
};
```

hash

-----
