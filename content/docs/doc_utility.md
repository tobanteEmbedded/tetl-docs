---
title: "utility.hpp"
---

# Header file `utility.hpp`

``` cpp
#include "etl/version.hpp"
#include "etl/limits.hpp"
#include "etl/type_traits.hpp"

namespace etl
{
    template <typename T>
    add_rvalue_reference_t<T> declval() noexcept;

    template <typename T>
    constexpr remove_reference_t<T>&& move(T&& t) noexcept;

    //=== forward ===//
    template <typename T>
    constexpr T&& forward(remove_reference_t<T>& param) noexcept;
    template <typename T>
    constexpr T&& forward(remove_reference_t<T>&& param) noexcept;

    template <typename T, typename U = T>
    constexpr T exchange(T& obj, U&& newValue);

    //=== as_const ===//
    template <typename T>
    constexpr add_const_t<T>& as_const(T& t) noexcept;
    template <typename T>
    constexpr void as_const(T const&&) = delete;

    template <typename T, typename U, int _concept_requires_139 = 42, ::etl::enable_if_t<(_concept_requires_139 == 43) || (detail::is_integer_and_not_char_v<T> && detail::is_integer_and_not_char_v<U>), int> = 0>
    constexpr bool cmp_equal(T t, U u) noexcept;

    template <typename T, typename U, int _concept_requires_167 = 42, ::etl::enable_if_t<(_concept_requires_167 == 43) || (detail::is_integer_and_not_char_v<T> && detail::is_integer_and_not_char_v<U>), int> = 0>
    constexpr bool cmp_not_equal(T t, U u) noexcept;

    template <typename T, typename U, int _concept_requires_184 = 42, ::etl::enable_if_t<(_concept_requires_184 == 43) || (detail::is_integer_and_not_char_v<T> && detail::is_integer_and_not_char_v<U>), int> = 0>
    constexpr bool cmp_less(T t, U u) noexcept;

    template <typename T, typename U, int _concept_requires_211 = 42, ::etl::enable_if_t<(_concept_requires_211 == 43) || (detail::is_integer_and_not_char_v<T> && detail::is_integer_and_not_char_v<U>), int> = 0>
    constexpr bool cmp_greater(T t, U u) noexcept;

    template <typename T, typename U, int _concept_requires_228 = 42, ::etl::enable_if_t<(_concept_requires_228 == 43) || (detail::is_integer_and_not_char_v<T> && detail::is_integer_and_not_char_v<U>), int> = 0>
    constexpr bool cmp_less_equal(T t, U u) noexcept;

    template <typename T, typename U, int _concept_requires_245 = 42, ::etl::enable_if_t<(_concept_requires_245 == 43) || (detail::is_integer_and_not_char_v<T> && detail::is_integer_and_not_char_v<U>), int> = 0>
    constexpr bool cmp_greater_equal(T t, U u) noexcept;

    template <typename R, typename T, int _concept_requires_262 = 42, ::etl::enable_if_t<(_concept_requires_262 == 43) || (detail::is_integer_and_not_char_v<T>), int> = 0>
    constexpr bool in_range(T t) noexcept;

    struct piecewise_construct_t;

    constexpr etl::piecewise_construct_t const piecewise_construct;

    struct in_place_t;

    template <typename T>
    struct in_place_type_t;

    template <typename T>inline constexpr auto in_place_type = in_place_type_t<T>{};

    template <etl::size_t I>
    struct in_place_index_t;

    template <size_t I>inline constexpr auto in_place_index = in_place_index_t<I>{};

    template <typename T1, typename T2>
    struct pair;

    template <typename T1, typename T2>
    constexpr void swap(pair<T1, T2>& lhs, pair<T1, T2>& rhs) noexcept('hidden');

    template <typename T1, typename T2>
    constexpr pair<decay_t<T1>, decay_t<T2>> make_pair(T1&& t, T2&& u);

    template <typename T1, typename T2>
    constexpr bool operator==(pair<T1, T2> const& lhs, pair<T1, T2> const& rhs);

    template <typename T1, typename T2>
    constexpr bool operator!=(pair<T1, T2> const& lhs, pair<T1, T2> const& rhs);

    template <typename T1, typename T2>
    constexpr bool operator<(pair<T1, T2> const& lhs, pair<T1, T2> const& rhs);

    template <typename T1, typename T2>
    constexpr bool operator<=(pair<T1, T2> const& lhs, pair<T1, T2> const& rhs);

    template <typename T1, typename T2>
    constexpr bool operator>(pair<T1, T2> const& lhs, pair<T1, T2> const& rhs);

    template <typename T1, typename T2>
    constexpr bool operator>=(pair<T1, T2> const& lhs, pair<T1, T2> const& rhs);

    template <typename T1, typename T2>
    struct tuple_size<pair<T1, T2>;

    template <etl::size_t I, typename T1, typename T2>
    struct tuple_element<I, pair<T1, T2>;

    template <etl::size_t I, typename T1, typename T2>
    constexpr tuple_element_t<I, pair<T1, T2>>& get(pair<T1, T2>& p) noexcept;

    template <etl::size_t I, typename T1, typename T2>
    constexpr tuple_element_t<I, pair<T1, T2>> const& get(pair<T1, T2> const& p) noexcept;

    template <etl::size_t I, typename T1, typename T2>
    constexpr tuple_element_t<I, pair<T1, T2>>&& get(pair<T1, T2>&& p) noexcept;

    template <etl::size_t I, typename T1, typename T2>
    constexpr tuple_element_t<I, pair<T1, T2>> const&& get(pair<T1, T2> const&& p) noexcept;
}
```

### Function `etl::declval`

``` cpp
template <typename T>
add_rvalue_reference_t<T> declval() noexcept;
```

Converts any type T to a reference type, making it possible to use member functions in decltype expressions without the need to go through constructors.

-----

### Function `etl::move`

``` cpp
template <typename T>
constexpr remove_reference_t<T>&& move(T&& t) noexcept;
```

move is used to indicate that an object t may be “moved from”, i.e. allowing the efficient transfer of resources from t to another object. In particular, move produces an xvalue expression that identifies its argument t. It is exactly equivalent to a static\_cast to an rvalue reference type.

*Return values:* `static_cast<remove_reference_t<T>&&>(t)`

-----

### Function `etl::forward`

``` cpp
(1) template <typename T>
constexpr T&& forward(remove_reference_t<T>& param) noexcept;

(2) template <typename T>
constexpr T&& forward(remove_reference_t<T>&& param) noexcept;
```

Forwards lvalues as either lvalues or as rvalues, depending on T. When t is a forwarding reference (a function argument that is declared as an rvalue reference to a cv-unqualified function template parameter), this overload forwards the argument to another function with the value category it had when passed to the calling function.

*Notes:* [cppreference.com/w/cpp/utility/forward](https://en.cppreference.com/w/cpp/utility/forward)

-----

### Function `etl::exchange`

``` cpp
template <typename T, typename U = T>
constexpr T exchange(T& obj, U&& newValue);
```

Replaces the value of obj with new\_value and returns the old value of obj.

*Return values:* The old value of obj.

-----

### Function `etl::as_const`

``` cpp
(1) template <typename T>
constexpr add_const_t<T>& as_const(T& t) noexcept;

(2) template <typename T>
constexpr void as_const(T const&&) = delete;
```

Forms lvalue reference to const type of t.

-----

### Function `etl::cmp_equal`

``` cpp
template <typename T, typename U, int _concept_requires_139 = 42, ::etl::enable_if_t<(_concept_requires_139 == 43) || (detail::is_integer_and_not_char_v<T> && detail::is_integer_and_not_char_v<U>), int> = 0>
constexpr bool cmp_equal(T t, U u) noexcept;
```

Compare the values of two integers t and u. Unlike builtin comparison operators, negative signed integers always compare less than (and not equal to) unsigned integers: the comparison is safe against lossy integer conversion.

*Notes:* [cppreference.com/w/cpp/utility/intcmp](https://en.cppreference.com/w/cpp/utility/intcmp)

It is a compile-time error if either T or U is not a signed or unsigned integer type (including standard integer type and extended integer type).

-----

### Function `etl::cmp_not_equal`

``` cpp
template <typename T, typename U, int _concept_requires_167 = 42, ::etl::enable_if_t<(_concept_requires_167 == 43) || (detail::is_integer_and_not_char_v<T> && detail::is_integer_and_not_char_v<U>), int> = 0>
constexpr bool cmp_not_equal(T t, U u) noexcept;
```

Compare the values of two integers t and u. Unlike builtin comparison operators, negative signed integers always compare less than (and not equal to) unsigned integers: the comparison is safe against lossy integer conversion.

*Notes:* [cppreference.com/w/cpp/utility/intcmp](https://en.cppreference.com/w/cpp/utility/intcmp)

It is a compile-time error if either T or U is not a signed or unsigned integer type (including standard integer type and extended integer type).

-----

### Function `etl::cmp_less`

``` cpp
template <typename T, typename U, int _concept_requires_184 = 42, ::etl::enable_if_t<(_concept_requires_184 == 43) || (detail::is_integer_and_not_char_v<T> && detail::is_integer_and_not_char_v<U>), int> = 0>
constexpr bool cmp_less(T t, U u) noexcept;
```

Compare the values of two integers t and u. Unlike builtin comparison operators, negative signed integers always compare less than (and not equal to) unsigned integers: the comparison is safe against lossy integer conversion.

*Notes:* [cppreference.com/w/cpp/utility/intcmp](https://en.cppreference.com/w/cpp/utility/intcmp)

It is a compile-time error if either T or U is not a signed or unsigned integer type (including standard integer type and extended integer type).

-----

### Function `etl::cmp_greater`

``` cpp
template <typename T, typename U, int _concept_requires_211 = 42, ::etl::enable_if_t<(_concept_requires_211 == 43) || (detail::is_integer_and_not_char_v<T> && detail::is_integer_and_not_char_v<U>), int> = 0>
constexpr bool cmp_greater(T t, U u) noexcept;
```

Compare the values of two integers t and u. Unlike builtin comparison operators, negative signed integers always compare less than (and not equal to) unsigned integers: the comparison is safe against lossy integer conversion.

*Notes:* [cppreference.com/w/cpp/utility/intcmp](https://en.cppreference.com/w/cpp/utility/intcmp)

It is a compile-time error if either T or U is not a signed or unsigned integer type (including standard integer type and extended integer type).

-----

### Function `etl::cmp_less_equal`

``` cpp
template <typename T, typename U, int _concept_requires_228 = 42, ::etl::enable_if_t<(_concept_requires_228 == 43) || (detail::is_integer_and_not_char_v<T> && detail::is_integer_and_not_char_v<U>), int> = 0>
constexpr bool cmp_less_equal(T t, U u) noexcept;
```

Compare the values of two integers t and u. Unlike builtin comparison operators, negative signed integers always compare less than (and not equal to) unsigned integers: the comparison is safe against lossy integer conversion.

*Notes:* [cppreference.com/w/cpp/utility/intcmp](https://en.cppreference.com/w/cpp/utility/intcmp)

It is a compile-time error if either T or U is not a signed or unsigned integer type (including standard integer type and extended integer type).

-----

### Function `etl::cmp_greater_equal`

``` cpp
template <typename T, typename U, int _concept_requires_245 = 42, ::etl::enable_if_t<(_concept_requires_245 == 43) || (detail::is_integer_and_not_char_v<T> && detail::is_integer_and_not_char_v<U>), int> = 0>
constexpr bool cmp_greater_equal(T t, U u) noexcept;
```

Compare the values of two integers t and u. Unlike builtin comparison operators, negative signed integers always compare less than (and not equal to) unsigned integers: the comparison is safe against lossy integer conversion.

*Notes:* [cppreference.com/w/cpp/utility/intcmp](https://en.cppreference.com/w/cpp/utility/intcmp)

It is a compile-time error if either T or U is not a signed or unsigned integer type (including standard integer type and extended integer type).

-----

### Function `etl::in_range`

``` cpp
template <typename R, typename T, int _concept_requires_262 = 42, ::etl::enable_if_t<(_concept_requires_262 == 43) || (detail::is_integer_and_not_char_v<T>), int> = 0>
constexpr bool in_range(T t) noexcept;
```

Returns true if the value of t is in the range of values that can be represented in R, that is, if t can be converted to R without data loss.

*Notes:* [cppreference.com/w/cpp/utility/in\_range](https://en.cppreference.com/w/cpp/utility/in_range)

It is a compile-time error if either T or R is not a signed or unsigned integer type (including standard integer type and extended integer type). This function cannot be used with etl::byte, char, char8\_t, char16\_t, char32\_t, wchar\_t and bool.

-----

### Struct `etl::piecewise_construct_t`

``` cpp
struct piecewise_construct_t
{
};
```

etl::piecewise\_construct\_t is an empty class tag type used to disambiguate between different functions that take two tuple arguments.

*Notes:* [cppreference.com/w/cpp/utility/piecewise\_construct\_t](https://en.cppreference.com/w/cpp/utility/piecewise_construct_t)

The overloads that do not use etl::piecewise\_construct\_t assume that each tuple argument becomes the element of a pair. The overloads that use etl::piecewise\_construct\_t assume that each tuple argument is used to construct, piecewise, a new object of specified type, which will become the element of the pair.

-----

### Variable `etl::piecewise_construct`

``` cpp
constexpr etl::piecewise_construct_t const piecewise_construct;
```

The constant etl::piecewise\_construct is an instance of an empty struct tag type etl::piecewise\_construct\_t.

-----

### Struct `etl::in_place_type_t`

``` cpp
template <typename T>
struct in_place_type_t
{
};
```

Disambiguation tags that can be passed to the constructors of etl::optional, etl::variant, and etl::any to indicate that the contained object should be constructed in-place, and (for the latter two) the type of the object to be constructed.

The corresponding type/type templates etl::in\_place\_t, etl::in\_place\_type\_t and etl::in\_place\_index\_t can be used in the constructor’s parameter list to match the intended tag.

-----

### Struct `etl::in_place_index_t`

``` cpp
template <etl::size_t I>
struct in_place_index_t
{
};
```

Disambiguation tags that can be passed to the constructors of etl::optional, etl::variant, and etl::any to indicate that the contained object should be constructed in-place, and (for the latter two) the type of the object to be constructed.

The corresponding type/type templates etl::in\_place\_t, etl::in\_place\_type\_t and etl::in\_place\_index\_t can be used in the constructor’s parameter list to match the intended tag.

-----

### Struct `etl::pair`

``` cpp
template <typename T1, typename T2>
struct pair
{
    template <int _concept_requires_357 = 42, ::etl::enable_if_t<(_concept_requires_357 == 43) || (is_default_constructible_v<T1> && is_default_constructible_v<T2>), int> = 0>
    constexpr pair();

    template <int _concept_requires_361 = 42, ::etl::enable_if_t<(_concept_requires_361 == 43) || (is_copy_constructible_v<T1> && is_copy_constructible_v<T2>), int> = 0>
    constexpr pair(T1 const& t1, T2 const& t2);

    template <typename U1, typename U2, int _concept_requires_368 = 42, ::etl::enable_if_t<(_concept_requires_368 == 43) || (is_constructible_v<U1 &&, first_type> && is_constructible_v<U2 &&, second_type>), int> = 0>
    constexpr pair(U1&& x, U2&& y);

    template <typename U1, typename U2, int _concept_requires_377 = 42, ::etl::enable_if_t<(_concept_requires_377 == 43) || (is_constructible_v<first_type, const U1 &> && is_constructible_v<second_type, const U2 &>), int> = 0>
    constexpr pair(pair<U1, U2> const& p);

    template <typename U1, typename U2, int _concept_requires_387 = 42, ::etl::enable_if_t<(_concept_requires_387 == 43) || (is_constructible_v<first_type, U1 &&> && is_constructible_v<second_type, U2 &&>), int> = 0>
    constexpr pair(pair<U1, U2>&& p);

    constexpr pair(const pair<T1, T2>& p) = default;

    constexpr pair(pair<T1, T2>&& p) noexcept = default;

    ~pair() noexcept = default;
};
```

etl::pair is a class template that provides a way to store two heterogeneous objects as a single unit. A pair is a specific case of a etl::tuple with two elements. If neither T1 nor T2 is a possibly cv-qualified class type with non-trivial destructor, or array thereof, the destructor of pair is trivial.

*Notes:* [cppreference.com/w/cpp/utility/pair](https://en.cppreference.com/w/cpp/utility/pair)

\\todo Add conditional explicit when C++20 is available.

### Constructor `etl::pair::pair`

``` cpp
template <int _concept_requires_357 = 42, ::etl::enable_if_t<(_concept_requires_357 == 43) || (is_default_constructible_v<T1> && is_default_constructible_v<T2>), int> = 0>
constexpr pair();
```

Default constructor. Value-initializes both elements of the pair, first and second.

-----

### Constructor `etl::pair::pair`

``` cpp
template <int _concept_requires_361 = 42, ::etl::enable_if_t<(_concept_requires_361 == 43) || (is_copy_constructible_v<T1> && is_copy_constructible_v<T2>), int> = 0>
constexpr pair(T1 const& t1, T2 const& t2);
```

Initializes first with x and second with y.

-----

### Constructor `etl::pair::pair`

``` cpp
template <typename U1, typename U2, int _concept_requires_368 = 42, ::etl::enable_if_t<(_concept_requires_368 == 43) || (is_constructible_v<U1 &&, first_type> && is_constructible_v<U2 &&, second_type>), int> = 0>
constexpr pair(U1&& x, U2&& y);
```

Initializes first with etl::forward\<U1\>(x) and second with etl::forward\<U2\>(y).

-----

### Constructor `etl::pair::pair`

``` cpp
template <typename U1, typename U2, int _concept_requires_377 = 42, ::etl::enable_if_t<(_concept_requires_377 == 43) || (is_constructible_v<first_type, const U1 &> && is_constructible_v<second_type, const U2 &>), int> = 0>
constexpr pair(pair<U1, U2> const& p);
```

Initializes first with p.first and second with p.second.

-----

### Constructor `etl::pair::pair`

``` cpp
template <typename U1, typename U2, int _concept_requires_387 = 42, ::etl::enable_if_t<(_concept_requires_387 == 43) || (is_constructible_v<first_type, U1 &&> && is_constructible_v<second_type, U2 &&>), int> = 0>
constexpr pair(pair<U1, U2>&& p);
```

Initializes first with etl::forward\<U1\>(p.first) and second with etl::forward\<U2\>(p.second).

-----

### Constructor `etl::pair::pair`

``` cpp
constexpr pair(const pair<T1, T2>& p) = default;
```

Copy constructor is defaulted, and is constexpr if copying of both elements satisfies the requirements on constexpr functions.

-----

### Constructor `etl::pair::pair`

``` cpp
constexpr pair(pair<T1, T2>&& p) noexcept = default;
```

Move constructor is defaulted, and is constexpr if moving of both elements satisfies the requirements on constexpr functions.

-----

### Destructor `etl::pair::~pair`

``` cpp
~pair() noexcept = default;
```

Defaulted destructor.

-----

-----

### Function `etl::swap`

``` cpp
template <typename T1, typename T2>
constexpr void swap(pair<T1, T2>& lhs, pair<T1, T2>& rhs) noexcept('hidden');
```

Swaps the contents of x and y. Equivalent to x.swap(y).

-----

### Function `etl::make_pair`

``` cpp
template <typename T1, typename T2>
constexpr pair<decay_t<T1>, decay_t<T2>> make_pair(T1&& t, T2&& u);
```

Creates a etl::pair object, deducing the target type from the types of arguments.

*Notes:* [cppreference.com/w/cpp/utility/pair/make\_pair](https://en.cppreference.com/w/cpp/utility/pair/make_pair)

The deduced types V1 and V2 are etl::decay\<T1\>::type and etl::decay\<T2\>::type (the usual type transformations applied to arguments of functions passed by value).

-----

### Function `etl::operator==`

``` cpp
template <typename T1, typename T2>
constexpr bool operator==(pair<T1, T2> const& lhs, pair<T1, T2> const& rhs);
```

Tests if both elements of lhs and rhs are equal, that is, compares lhs.first with rhs.first and lhs.second with rhs.second.

-----

### Function `etl::operator!=`

``` cpp
template <typename T1, typename T2>
constexpr bool operator!=(pair<T1, T2> const& lhs, pair<T1, T2> const& rhs);
```

Tests if both elements of lhs and rhs are equal, that is, compares lhs.first with rhs.first and lhs.second with rhs.second.

-----

### Function `etl::operator<`

``` cpp
template <typename T1, typename T2>
constexpr bool operator<(pair<T1, T2> const& lhs, pair<T1, T2> const& rhs);
```

Compares lhs and rhs lexicographically by operator\<, that is, compares the first elements and only if they are equivalent, compares the second elements.

-----

### Function `etl::operator<=`

``` cpp
template <typename T1, typename T2>
constexpr bool operator<=(pair<T1, T2> const& lhs, pair<T1, T2> const& rhs);
```

Compares lhs and rhs lexicographically by operator\<, that is, compares the first elements and only if they are equivalent, compares the second elements.

-----

### Function `etl::operator>`

``` cpp
template <typename T1, typename T2>
constexpr bool operator>(pair<T1, T2> const& lhs, pair<T1, T2> const& rhs);
```

Compares lhs and rhs lexicographically by operator\<, that is, compares the first elements and only if they are equivalent, compares the second elements.

-----

### Function `etl::operator>=`

``` cpp
template <typename T1, typename T2>
constexpr bool operator>=(pair<T1, T2> const& lhs, pair<T1, T2> const& rhs);
```

Compares lhs and rhs lexicographically by operator\<, that is, compares the first elements and only if they are equivalent, compares the second elements.

-----

### Struct `etl::tuple_size`

``` cpp
template <typename T1, typename T2>
struct tuple_size<pair<T1, T2>
: integral_constant<size_t,2>
{
};
```
The partial specialization of tuple\_size for pairs provides a compile-time way to obtain the number of elements in a pair, which is always 2, using tuple-like syntax.

-----

### Struct `etl::tuple_element`

``` cpp
template <etl::size_t I, typename T1, typename T2>
struct tuple_element<I, pair<T1, T2>
{
    static_assert(I<2, "pair index out of range");
};
```
The partial specializations of tuple\_element for pairs provide compile-time access to the types of the pair’s elements, using tuple-like syntax. The program is ill-formed if I \>= 2.

-----

### Function `etl::get`

``` cpp
template <etl::size_t I, typename T1, typename T2>
constexpr tuple_element_t<I, pair<T1, T2>>& get(pair<T1, T2>& p) noexcept;
```
Extracts an element from the pair using tuple-like interface.

The index-based overloads (1-4) fail to compile if the index I is neither 0 nor 1. See Alisdar Meredith talk “Recreational C++” 35:00 to 46:00. https://youtu.be/ovxNM865WaU

-----

### Function `etl::get`

``` cpp
template <etl::size_t I, typename T1, typename T2>
constexpr tuple_element_t<I, pair<T1, T2>> const& get(pair<T1, T2> const& p) noexcept;
```
Extracts an element from the pair using tuple-like interface.

The index-based overloads (1-4) fail to compile if the index I is neither 0 nor 1. See Alisdar Meredith talk “Recreational C++” 35:00 to 46:00. https://youtu.be/ovxNM865WaU

-----

### Function `etl::get`

``` cpp
template <etl::size_t I, typename T1, typename T2>
constexpr tuple_element_t<I, pair<T1, T2>>&& get(pair<T1, T2>&& p) noexcept;
```
Extracts an element from the pair using tuple-like interface.

The index-based overloads (1-4) fail to compile if the index I is neither 0 nor 1. See Alisdar Meredith talk “Recreational C++” 35:00 to 46:00. https://youtu.be/ovxNM865WaU

-----

### Function `etl::get`

``` cpp
template <etl::size_t I, typename T1, typename T2>
constexpr tuple_element_t<I, pair<T1, T2>> const&& get(pair<T1, T2> const&& p) noexcept;
```
Extracts an element from the pair using tuple-like interface.

The index-based overloads (1-4) fail to compile if the index I is neither 0 nor 1. See Alisdar Meredith talk “Recreational C++” 35:00 to 46:00. https://youtu.be/ovxNM865WaU

-----
