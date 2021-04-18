---
title: "type_traits.hpp"
---

# Header file `type_traits.hpp`

``` cpp
#include "etl/version.hpp"

#define TETL_TYPETRAITS_HPP

namespace etl
{
    template <typename Type, Type Val>
    struct integral_constant;

    template <bool B>
    using bool_constant = integral_constant<bool, B>;

    template <typename ...>
    using void_t = void;

    template <typename T>
    struct type_identity;

    //=== conditional ===//
    template <bool B, typename T, typename F>
    struct conditional;
    template <bool B, typename T, typename F>
    using conditional_t = typename conditional<B, T, F>::type;

    //=== conjunction ===//
    template <typename ...>
    struct conjunction;
    template <typename...B>inline constexpr bool conjunction_v = conjunction<B...>::value;

    //=== disjunction ===//
    template <typename ...>
    struct disjunction;
    template <typename...B>inline constexpr bool disjunction_v = disjunction<B...>::value;

    //=== negation ===//
    template <typename B>
    struct negation;
    template <typename B>inline constexpr bool negation_v = negation<B>::value;

    //=== add_lvalue_reference ===//
    template <typename T>
    struct add_lvalue_reference;
    template <typename T>
    using add_lvalue_reference_t = typename add_lvalue_reference<T>::type;

    //=== add_rvalue_reference ===//
    template <typename T>
    struct add_rvalue_reference;
    template <typename T>
    using add_rvalue_reference_t = typename add_rvalue_reference<T>::type;

    //=== extent ===//
    template <typename T, unsigned int N = 0>
    struct extent;
    template <typename T>
    using extent_v = typename extent<T>::value;

    //=== remove_extent ===//
    template <typename T>
    struct remove_extent;
    template <typename T>
    using remove_extent_t = typename remove_extent<T>::type;

    //=== remove_all_extents ===//
    template <typename T>
    struct remove_all_extents;
    template <typename T>
    using remove_all_extents_t = typename remove_all_extents<T>::type;

    //=== remove_const ===//
    template <typename Type>
    struct remove_const;
    template <typename T>
    using remove_const_t = typename remove_const<T>::type;

    //=== remove_volatile ===//
    template <typename Type>
    struct remove_volatile;
    template <typename T>
    using remove_volatile_t = typename remove_volatile<T>::type;

    //=== remove_cv ===//
    template <typename Type>
    struct remove_cv;
    template <typename T>
    using remove_cv_t = typename remove_cv<T>::type;

    //=== remove_reference ===//
    template <typename T>
    struct remove_reference;
    template <typename T>
    using remove_reference_t = typename remove_reference<T>::type;

    //=== remove_cvref ===//
    template <typename T>
    struct remove_cvref;
    template <typename T>
    using remove_cvref_t = typename remove_cvref<T>::type;

    //=== remove_pointer ===//
    template <typename T>
    struct remove_pointer;
    template <typename T>
    using remove_pointer_t = typename remove_pointer<T>::type;

    //=== add_pointer ===//
    template <typename T>
    struct add_pointer;
    template <typename T>
    using add_pointer_t = typename add_pointer<T>::type;

    //=== add_cv ===//
    template <typename T>
    struct add_cv;
    template <typename T>
    using add_cv_t = typename add_cv<T>::type;

    //=== add_const ===//
    template <typename T>
    struct add_const;
    template <typename T>
    using add_const_t = typename add_const<T>::type;

    //=== add_volatile ===//
    template <typename T>
    struct add_volatile;
    template <typename T>
    using add_volatile_t = typename add_volatile<T>::type;

    //=== is_same ===//
    template <typename T, typename U>
    struct is_same;
    template <typename T, typename U>inline constexpr bool is_same_v = is_same<T, U>::value;

    //=== is_void ===//
    template <typename T>
    struct is_void;
    template <typename T>inline constexpr bool is_void_v = is_void<T>::value;

    //=== is_integral ===//
    template <typename Type>
    struct is_integral;
    template <typename T>inline constexpr bool is_integral_v = is_integral<T>::value;

    //=== make_signed ===//
    template <typename Type>
    struct make_signed;
    template <typename T>
    using make_signed_t = typename make_signed<T>::type;

    //=== make_unsigned ===//
    template <typename Type>
    struct make_unsigned;
    template <typename T>
    using make_unsigned_t = typename make_unsigned<T>::type;

    //=== integer_sequence ===//
    template <typename T, T Ints ... >
    struct integer_sequence;
    template <typename T, T Size>
    using make_integer_sequence = __make_integer_seq<integer_sequence, T, Size>;
    template <etl::size_t Ints ... >
    using index_sequence = integer_sequence<etl::size_t, Ints...>;
    template <etl::size_t Size>
    using make_index_sequence = make_integer_sequence<etl::size_t, Size>;
    template <typename ... T>
    using index_sequence_for = make_index_sequence<sizeof...(T)>;

    //=== is_floating_point ===//
    template <typename T>
    struct is_floating_point;
    template <typename T>inline constexpr bool is_floating_point_v = is_floating_point<T>::value;

    //=== is_const ===//
    template <typename T>
    struct is_const;
    template <typename T>inline constexpr bool is_const_v = is_const<T>::value;

    //=== is_volatile ===//
    template <typename T>
    struct is_volatile;
    template <typename T>inline constexpr bool is_volatile_v = is_volatile<T>::value;

    //=== is_empty ===//
    template <typename T>
    struct is_empty;
    template <typename T>inline constexpr bool is_empty_v = is_empty<T>::value;

    //=== is_polymorphic ===//
    template <typename T>
    struct is_polymorphic;
    template <typename T>inline constexpr bool is_polymorphic_v = is_polymorphic<T>::value;

    //=== is_final ===//
    template <typename T>
    struct is_final;
    template <typename T>inline constexpr bool is_final_v = is_final<T>::value;

    //=== is_abstract ===//
    template <typename T>
    struct is_abstract;
    template <typename T>inline constexpr bool is_abstract_v = is_abstract<T>::value;

    //=== is_aggregate ===//
    template <typename T>
    struct is_aggregate;
    template <typename T>inline constexpr bool is_aggregate_v = is_aggregate<T>::value;

    //=== is_reference ===//
    template <typename T>
    struct is_reference;
    template <typename T>inline constexpr bool is_reference_v = is_reference<T>::value;

    //=== is_null_pointer ===//
    template <typename T>
    struct is_null_pointer;
    template <typename T>inline constexpr bool is_null_pointer_v = is_null_pointer<T>::value;

    //=== is_array ===//
    template <typename T>
    struct is_array;
    template <typename T>inline constexpr bool is_array_v = is_array<T>::value;

    //=== is_function ===//
    template <typename T>
    struct is_function;
    template <typename T>inline constexpr bool is_function_v = is_function<T>::value;

    //=== is_pointer ===//
    template <typename T>
    struct is_pointer;
    template <typename T>inline constexpr bool is_pointer_v = is_pointer<T>::value;

    //=== is_lvalue_reference ===//
    template <typename T>
    struct is_lvalue_reference;
    template <typename T>inline constexpr bool is_lvalue_reference_v = is_lvalue_reference<T>::value;

    //=== is_rvalue_reference ===//
    template <typename T>
    struct is_rvalue_reference;
    template <typename T>inline constexpr bool is_rvalue_reference_v = is_rvalue_reference<T>::value;

    //=== is_class ===//
    template <typename T>
    struct is_class;
    template <typename T>inline constexpr bool is_class_v = is_class<T>::value;

    //=== is_enum ===//
    template <typename T>
    struct is_enum;
    template <typename T>inline constexpr bool is_enum_v = is_enum<T>::value;

    //=== is_union ===//
    template <typename T>
    struct is_union;
    template <typename T>inline constexpr bool is_union_v = is_union<T>::value;

    template <typename T>
    struct is_member_pointer;

    template <typename T>inline constexpr bool is_member_pointer_v = is_member_pointer<T>::value;

    template <typename T>
    struct is_member_function_pointer;

    template <typename T>inline constexpr bool is_member_function_pointer_v = is_member_function_pointer<T>::value;

    template <typename T>
    struct is_member_object_pointer;

    template <typename T>inline constexpr bool is_member_object_pointer_v = is_member_object_pointer<T>::value;

    template <typename T>
    struct is_arithmetic;

    template <typename T>inline constexpr bool is_arithmetic_v = is_arithmetic<T>::value;

    template <typename T>
    struct is_fundamental;

    template <typename T>inline constexpr bool is_fundamental_v = is_fundamental<T>::value;

    template <typename T>
    struct is_scalar;

    template <typename T>inline constexpr bool is_scalar_v = is_scalar<T>::value;

    template <typename T>
    struct is_object;

    template <typename T>inline constexpr bool is_object_v = is_object<T>::value;

    template <typename T>
    struct is_compound;

    template <typename T>inline constexpr bool is_compound_v = is_compound<T>::value;

    template <typename T>
    struct is_bounded_array;

    template <typename T, etl::size_t N>
    struct is_bounded_array<T[N]>;

    template <typename T>inline constexpr bool is_bounded_array_v = is_bounded_array<T>::value;

    template <typename T>
    struct is_unbounded_array;

    template <typename T>
    struct is_unbounded_array<T[]>;

    template <typename T>inline constexpr bool is_unbounded_array_v = is_unbounded_array<T>::value;

    template <typename T, typename ... Args>
    using is_constructible = 'hidden';

    template <typename T, typename...Args>inline constexpr bool is_constructible_v = is_constructible<T, Args...>::value;

    template <typename T, typename ... Args>
    struct is_trivially_constructible;

    template <typename T, typename...Args>inline constexpr bool is_trivially_constructible_v = is_trivially_constructible<T, Args...>::value;

    template <typename T, typename ... Args>
    struct is_nothrow_constructible;

    template <typename T, typename...Args>inline constexpr bool is_nothrow_constructible_v = is_nothrow_constructible<T, Args...>::value;

    template <typename T>
    struct is_default_constructible;

    template <typename T>inline constexpr bool is_default_constructible_v = is_default_constructible<T>::value;

    template <typename T>
    struct is_trivially_default_constructible;

    template <typename T>inline constexpr bool is_trivially_default_constructible_v = is_trivially_default_constructible<T>::value;

    template <typename T>
    struct is_nothrow_default_constructible;

    template <typename T>inline constexpr bool is_nothrow_default_constructible_v = is_nothrow_default_constructible<T>::value;

    template <typename T>
    struct is_copy_constructible;

    template <typename T>inline constexpr bool is_copy_constructible_v = is_copy_constructible<T>::value;

    template <typename T>
    struct is_trivially_copy_constructible;

    template <typename T>inline constexpr bool is_trivially_copy_constructible_v = is_trivially_copy_constructible<T>::value;

    template <typename T>
    struct is_nothrow_copy_constructible;

    template <typename T>inline constexpr bool is_nothrow_copy_constructible_v = is_nothrow_copy_constructible<T>::value;

    template <typename T>
    struct is_move_constructible;

    template <typename T>inline constexpr bool is_move_constructible_v = is_move_constructible<T>::value;

    template <typename T>
    struct is_trivially_move_constructible;

    template <typename T>inline constexpr bool is_trivially_move_constructible_v = is_trivially_move_constructible<T>::value;

    template <typename T>
    struct is_nothrow_move_constructible;

    template <typename T>inline constexpr bool is_nothrow_move_constructible_v = is_nothrow_move_constructible<T>::value;

    //=== is_destructible ===//
    template <typename T>
    struct is_destructible;
    template <typename T>inline constexpr auto is_destructible_v = is_destructible<T>::value;

    template <typename T>
    struct is_trivially_destructible;

    template <typename T>inline constexpr auto is_trivially_destructible_v = is_trivially_destructible<T>::value;

    //=== is_nothrow_destructible ===//
    template <typename Type>
    struct is_nothrow_destructible;
    template <typename T>inline constexpr bool is_nothrow_destructible_v = is_nothrow_destructible<T>::value;

    //=== has_virtual_destructor ===//
    template <typename T>
    struct has_virtual_destructor;
    template <typename T>inline constexpr auto has_virtual_destructor_v = has_virtual_destructor<T>::value;

    template <typename T, typename U>
    struct is_assignable;

    template <typename T, typename U>inline constexpr bool is_assignable_v = is_assignable<T, U>::value;

    template <typename T, typename U>
    struct is_trivially_assignable;

    template <typename T, typename U>inline constexpr bool is_trivially_assignable_v = is_trivially_assignable<T, U>::value;

    template <typename T, typename U>
    struct is_nothrow_assignable;

    template <typename T, typename U>inline constexpr bool is_nothrow_assignable_v = is_nothrow_assignable<T, U>::value;

    template <typename T>
    struct is_copy_assignable;

    template <typename T>inline constexpr bool is_copy_assignable_v = is_copy_assignable<T>::value;

    template <typename T>
    struct is_trivially_copy_assignable;

    template <typename T>inline constexpr bool is_trivially_copy_assignable_v = is_trivially_copy_assignable<T>::value;

    template <typename T>
    struct is_nothrow_copy_assignable;

    template <typename T>inline constexpr bool is_nothrow_copy_assignable_v = is_nothrow_copy_assignable<T>::value;

    template <typename T>
    struct is_move_assignable;

    template <typename T>inline constexpr bool is_move_assignable_v = is_move_assignable<T>::value;

    template <typename T>
    struct is_trivially_move_assignable;

    template <typename T>inline constexpr bool is_trivially_move_assignable_v = is_trivially_move_assignable<T>::value;

    template <typename T>
    struct is_nothrow_move_assignable;

    template <typename T>inline constexpr bool is_nothrow_move_assignable_v = is_nothrow_move_assignable<T>::value;

    template <typename T>
    struct is_swappable;

    template <typename T>inline constexpr bool is_swappable_v = is_swappable<T>::value;

    template <typename T>
    struct is_nothrow_swappable;

    template <typename T>inline constexpr bool is_nothrow_swappable_v = is_nothrow_swappable<T>::value;

    template <typename T, typename U>
    struct is_swappable_with;

    template <typename T, typename U>inline constexpr bool is_swappable_with_v = is_swappable_with<T, U>::value;

    //=== alignment_of ===//
    template <typename T>
    struct alignment_of;
    template <typename T>inline constexpr size_t alignment_of_v = alignment_of<T>::value;

    template <typename T>
    struct is_trivially_copyable;

    template <typename T>
    struct is_trivially_copyable<T*>;

    template <typename T>inline constexpr bool is_trivially_copyable_v = is_trivially_copyable<T>::value;

    //=== is_trivial ===//
    template <typename T>
    struct is_trivial;
    template <typename T>inline constexpr bool is_trivial_v = is_trivial<T>::value;

    template <typename T>
    struct is_standard_layout;

    template <typename T>inline constexpr bool is_standard_layout_v = is_standard_layout<T>::value;

    template <typename T>
    struct has_unique_object_representations;

    template <typename T>inline constexpr bool has_unique_object_representations_v = has_unique_object_representations<T>::value;

    template <typename T>
    struct is_unsigned;

    template <typename T>inline constexpr bool is_unsigned_v = is_unsigned<T>::value;

    template <typename T>
    struct is_signed;

    template <typename T>inline constexpr bool is_signed_v = is_signed<T>::value;

    template <typename Base, typename Derived>
    struct is_base_of;

    template <typename Base, typename Derived>inline constexpr bool is_base_of_v = is_base_of<Base, Derived>::value;

    template <typename T>
    struct rank;

    template <typename T>
    struct rank<T[]>;

    template <typename T, etl::size_t N>
    struct rank<T[N]>;

    template <typename Type>inline constexpr size_t rank_v = rank<Type>::value;

    template <typename T>
    struct decay;

    template <typename T>
    using decay_t = typename decay<T>::type;

    //=== common_type ===//
    template <typename ... T>
    struct common_type;
    template <typename ... T>
    using common_type_t = typename common_type<T...>::type;

    //=== is_convertible ===//
    template <typename From, typename To>
    struct is_convertible;
    template <typename From, typename To>inline constexpr bool is_convertible_v = is_convertible<From, To>::value;

    //=== invoke_result ===//
    template <typename F, typename ... ArgTypes>
    struct invoke_result;
    template <typename F, typename ... ArgTypes>
    using invoke_result_t = typename invoke_result<F, ArgTypes...>::type;

    //=== aligned_storage ===//
    template <etl::size_t Len, etl::size_t Align = alignof(max_align_t)>
    struct aligned_storage;
    template <etl::size_t Len, etl::size_t Align = alignof(max_align_t)>
    using aligned_storage_t = typename aligned_storage<Len, Align>::type;

    template <etl::size_t Len, typename ... Types>
    struct aligned_union;

    template <etl::size_t Len, typename ... Types>
    using aligned_union_t = typename aligned_union<Len, Types...>::type;

    template <typename T>
    struct underlying_type;

    template <typename T>
    using underlying_type_t = typename underlying_type<T>::type;

    template <typename T, bool = is_enum_v<T>>>
    struct is_scoped_enum;

    template <typename T>
    struct is_scoped_enum<T, true>;

    template <typename T>inline constexpr bool is_scoped_enum_v = is_scoped_enum<T>::value;

    constexpr bool is_constant_evaluated() noexcept;
}
```

### Struct `etl::conditional`

``` cpp
(1) template <bool B, typename T, typename F>
struct conditional
{
};

(2) template <bool B, typename T, typename F>
using conditional_t = typename conditional<B, T, F>::type;
```

Provides member typedef type, which is defined as T if B is true at compile time, or as F if B is false.

-----

### Struct `etl::conjunction`

``` cpp
(1) template <typename ...>
struct conjunction
{
};

(2) template <typename...B>inline constexpr bool conjunction_v = conjunction<B...>::value;
```

Forms the logical conjunction of the type traits B…, effectively performing a logical AND on the sequence of traits.

-----

### Struct `etl::disjunction`

``` cpp
(1) template <typename ...>
struct disjunction
{
};

(2) template <typename...B>inline constexpr bool disjunction_v = disjunction<B...>::value;
```

Forms the logical disjunction of the type traits B…, effectively performing a logical OR on the sequence of traits.

-----

### Struct `etl::negation`

``` cpp
(1) template <typename B>
struct negation
: bool_constant<!bool(B::value)>
{
};

(2) template <typename B>inline constexpr bool negation_v = negation<B>::value;
```

Forms the logical negation of the type trait B.

-----

### Struct `etl::add_lvalue_reference`

``` cpp
(1) template <typename T>
struct add_lvalue_reference
: decltype(detail::try_add_lvalue_reference<T>(0))
{
};

(2) template <typename T>
using add_lvalue_reference_t = typename add_lvalue_reference<T>::type;
```

Creates a lvalue reference type of T.

-----

### Struct `etl::add_rvalue_reference`

``` cpp
(1) template <typename T>
struct add_rvalue_reference
: decltype(detail::try_add_rvalue_reference<T>(0))
{
};

(2) template <typename T>
using add_rvalue_reference_t = typename add_rvalue_reference<T>::type;
```

Creates a rvalue reference type of T.

-----

### Struct `etl::extent`

``` cpp
(1) template <typename T, unsigned int N = 0>
struct extent
: integral_constant<size_t,0>
{
};

(2) template <typename T>
using extent_v = typename extent<T>::value;
```

If T is an array type, provides the member constant value equal to the number of elements along the Nth dimension of the array, if N is in \[0, rank\_v\<T\>). For any other type, or if T is an array of unknown bound along its first dimension and N is 0, value is 0.

-----

### Struct `etl::remove_extent`

``` cpp
(1) template <typename T>
struct remove_extent
{
};

(2) template <typename T>
using remove_extent_t = typename remove_extent<T>::type;
```

If T is an array of some type X, provides the member typedef type equal to X, otherwise type is T. Note that if T is a multidimensional array, only the first dimension is removed. The behavior of a program that adds specializations for remove\_extent is undefined.

-----

### Struct `etl::remove_all_extents`

``` cpp
(1) template <typename T>
struct remove_all_extents
{
};

(2) template <typename T>
using remove_all_extents_t = typename remove_all_extents<T>::type;
```

If T is a multidimensional array of some type X, provides the member typedef type equal to X, otherwise type is T. The behavior of a program that adds specializations for remove\_all\_extents is undefined.

-----

### Struct `etl::remove_const`

``` cpp
(1) template <typename Type>
struct remove_const
{
};

(2) template <typename T>
using remove_const_t = typename remove_const<T>::type;
```

Provides the member typedef type which is the same as T, except that its topmost cv-qualifiers are removed. Removes the topmost const.

The behavior of a program that adds specializations for any of the templates described on this page is undefined.

-----

### Struct `etl::remove_volatile`

``` cpp
(1) template <typename Type>
struct remove_volatile
{
};

(2) template <typename T>
using remove_volatile_t = typename remove_volatile<T>::type;
```

Provides the member typedef type which is the same as T, except that its topmost cv-qualifiers are removed. Removes the topmost volatile.

The behavior of a program that adds specializations for any of the templates described on this page is undefined.

-----

### Struct `etl::remove_cv`

``` cpp
(1) template <typename Type>
struct remove_cv
{
};

(2) template <typename T>
using remove_cv_t = typename remove_cv<T>::type;
```

Provides the member typedef type which is the same as T, except that its topmost cv-qualifiers are removed. Removes the topmost const, or the topmost volatile, or both, if present.

The behavior of a program that adds specializations for any of the templates described on this page is undefined.

-----

### Struct `etl::remove_reference`

``` cpp
(1) template <typename T>
struct remove_reference
{
};

(2) template <typename T>
using remove_reference_t = typename remove_reference<T>::type;
```

-----

### Struct `etl::remove_cvref`

``` cpp
(1) template <typename T>
struct remove_cvref
{
};

(2) template <typename T>
using remove_cvref_t = typename remove_cvref<T>::type;
```

If the type T is a reference type, provides the member typedef type which is the type referred to by T with its topmost cv-qualifiers removed. Otherwise type is T with its topmost cv-qualifiers removed.

The behavior of a program that adds specializations for remove\_cvref is undefined.

-----

### Struct `etl::remove_pointer`

``` cpp
(1) template <typename T>
struct remove_pointer
{
};

(2) template <typename T>
using remove_pointer_t = typename remove_pointer<T>::type;
```

Provides the member typedef type which is the type pointed to by T, or, if T is not a pointer, then type is the same as T. The behavior of a program that adds specializations for remove\_pointer is undefined.

-----

### Struct `etl::add_pointer`

``` cpp
(1) template <typename T>
struct add_pointer
: decltype(detail::try_add_pointer<T>(0))
{
};

(2) template <typename T>
using add_pointer_t = typename add_pointer<T>::type;
```

If T is a reference type, then provides the member typedef type which is a pointer to the referred type. Otherwise, if T names an object type, a function type that is not cv- or ref-qualified, or a (possibly cv-qualified) void type, provides the member typedef type which is the type T\*. Otherwise (if T is a cv- or ref-qualified function type), provides the member typedef type which is the type T. The behavior of a program that adds specializations for add\_pointer is undefined.

-----

### Struct `etl::add_cv`

``` cpp
(1) template <typename T>
struct add_cv
{
};

(2) template <typename T>
using add_cv_t = typename add_cv<T>::type;
```

Provides the member typedef type which is the same as T, except it has a cv-qualifier added (unless T is a function, a reference, or already has this cv-qualifier). Adds both const and volatile.

-----

### Struct `etl::add_const`

``` cpp
(1) template <typename T>
struct add_const
{
};

(2) template <typename T>
using add_const_t = typename add_const<T>::type;
```

Provides the member typedef type which is the same as T, except it has a cv-qualifier added (unless T is a function, a reference, or already has this cv-qualifier). Adds const.

-----

### Struct `etl::add_volatile`

``` cpp
(1) template <typename T>
struct add_volatile
{
};

(2) template <typename T>
using add_volatile_t = typename add_volatile<T>::type;
```

Provides the member typedef type which is the same as T, except it has a cv-qualifier added (unless T is a function, a reference, or already has this cv-qualifier). Adds volatile.

-----

### Struct `etl::is_same`

``` cpp
(1) template <typename T, typename U>
struct is_same
{
};

(2) template <typename T, typename U>inline constexpr bool is_same_v = is_same<T, U>::value;
```

If T and U name the same type (taking into account const/volatile qualifications), provides the member constant value equal to true. Otherwise value is false.

-----

### Struct `etl::is_void`

``` cpp
(1) template <typename T>
struct is_void
: is_same<void,typename remove_cv<T>::type>
{
};

(2) template <typename T>inline constexpr bool is_void_v = is_void<T>::value;
```

Define a member typedef only if a boolean constant is true.

-----

### Struct `etl::is_integral`

``` cpp
(1) template <typename Type>
struct is_integral
: detail::is_integral_helper<remove_cv_t<Type>>::type
{
};

(2) template <typename T>inline constexpr bool is_integral_v = is_integral<T>::value;
```

-----

### Struct `etl::make_signed`

``` cpp
(1) template <typename Type>
struct make_signed
{
};

(2) template <typename T>
using make_signed_t = typename make_signed<T>::type;
```

If T is an integral (except bool) or enumeration type, provides the member typedef type which is the unsigned integer type corresponding to T, with the same cv-qualifiers. If T is signed or unsigned char, short, int, long, long long; the unsigned type from this list corresponding to T is provided. The behavior of a program that adds specializations for make\_signed is undefined.

    // Convert an unsigned int to signed int
    static_assert(is_same_v<make_signed_t<unsigned>, int>);

-----

### Struct `etl::make_unsigned`

``` cpp
(1) template <typename Type>
struct make_unsigned
{
};

(2) template <typename T>
using make_unsigned_t = typename make_unsigned<T>::type;
```

If T is an integral (except bool) or enumeration type, provides the member typedef type which is the unsigned integer type corresponding to T, with the same cv-qualifiers. If T is signed or unsigned char, short, int, long, long long; the unsigned type from this list corresponding to T is provided. The behavior of a program that adds specializations for make\_unsigned is undefined.

-----

### Struct `etl::integer_sequence`

``` cpp
(1) template <typename T, T Ints ... >
struct integer_sequence
{
    static_assert(is_integral_v<T>, "T must be an integral type.");
};

(2) template <typename T, T Size>
using make_integer_sequence = __make_integer_seq<integer_sequence, T, Size>;

(3) template <etl::size_t Ints ... >
using index_sequence = integer_sequence<etl::size_t, Ints...>;

(4) template <etl::size_t Size>
using make_index_sequence = make_integer_sequence<etl::size_t, Size>;

(5) template <typename ... T>
using index_sequence_for = make_index_sequence<sizeof...(T)>;
```

-----

### Struct `etl::is_floating_point`

``` cpp
(1) template <typename T>
struct is_floating_point
: bool_constant<is_same_v<float,remove_cv_t<T>>||is_same_v<double,remove_cv_t<T>>||is_same_v<long double,remove_cv_t<T>>>
{
};

(2) template <typename T>inline constexpr bool is_floating_point_v = is_floating_point<T>::value;
```

Checks whether T is a floating-point type. Provides the member constant value which is equal to true, if T is the type float, double, long double, including any cv-qualified variants. Otherwise, value is equal to false.

The behavior of a program that adds specializations for is\_floating\_point or is\_floating\_point\_v is undefined.

-----

### Struct `etl::is_const`

``` cpp
(1) template <typename T>
struct is_const
{
};

(2) template <typename T>inline constexpr bool is_const_v = is_const<T>::value;
```

If T is a const-qualified type (that is, const, or const volatile), provides the member constant value equal to true. For any other type, value is false.

-----

### Struct `etl::is_volatile`

``` cpp
(1) template <typename T>
struct is_volatile
{
};

(2) template <typename T>inline constexpr bool is_volatile_v = is_volatile<T>::value;
```

-----

### Struct `etl::is_empty`

``` cpp
(1) template <typename T>
struct is_empty
{
};

(2) template <typename T>inline constexpr bool is_empty_v = is_empty<T>::value;
```

f T is an empty type (that is, a non-union class type with no non-static data members other than bit-fields of size 0, no virtual functions, no virtual base classes, and no non-empty base classes), provides the member constant value equal to true. For any other type, value is false.

-----

### Struct `etl::is_polymorphic`

``` cpp
(1) template <typename T>
struct is_polymorphic
: bool_constant<__is_polymorphic(T)>
{
};

(2) template <typename T>inline constexpr bool is_polymorphic_v = is_polymorphic<T>::value;
```

-----

### Struct `etl::is_final`

``` cpp
(1) template <typename T>
struct is_final
: bool_constant<__is_final(T)>
{
};

(2) template <typename T>inline constexpr bool is_final_v = is_final<T>::value;
```

If T is a final class (that is, a class declared with the final specifier), provides the member constant value equal true. For any other type, value is false. If T is a class type, T shall be a complete type; otherwise, the behavior is undefined.

-----

### Struct `etl::is_abstract`

``` cpp
(1) template <typename T>
struct is_abstract
: bool_constant<__is_abstract(T)>
{
};

(2) template <typename T>inline constexpr bool is_abstract_v = is_abstract<T>::value;
```

-----

### Struct `etl::is_aggregate`

``` cpp
(1) template <typename T>
struct is_aggregate
: bool_constant<__is_aggregate(remove_cv_t<T>)>
{
};

(2) template <typename T>inline constexpr bool is_aggregate_v = is_aggregate<T>::value;
```

-----

### Struct `etl::is_reference`

``` cpp
(1) template <typename T>
struct is_reference
{
};

(2) template <typename T>inline constexpr bool is_reference_v = is_reference<T>::value;
```

If T is a reference type (lvalue reference or rvalue reference), provides the member constant value equal true. For any other type, value is false. The behavior of a program that adds specializations for is\_reference or is\_reference\_v is undefined.

-----

### Struct `etl::is_null_pointer`

``` cpp
(1) template <typename T>
struct is_null_pointer
: is_same<nullptr_t,remove_cv_t<T>>
{
};

(2) template <typename T>inline constexpr bool is_null_pointer_v = is_null_pointer<T>::value;
```

-----

### Struct `etl::is_array`

``` cpp
(1) template <typename T>
struct is_array
{
};

(2) template <typename T>inline constexpr bool is_array_v = is_array<T>::value;
```

Checks whether T is an array type. Provides the member constant value which is equal to true, if T is an array type. Otherwise, value is equal to false.

The behavior of a program that adds specializations for is\_array or is\_array\_v is undefined.

-----

### Struct `etl::is_function`

``` cpp
(1) template <typename T>
struct is_function
: bool_constant<!is_const_v<T const>&&!is_reference_v<T>>
{
};

(2) template <typename T>inline constexpr bool is_function_v = is_function<T>::value;
```

Checks whether T is a function type. Types like etl::function, lambdas, classes with overloaded operator() and pointers to functions don’t count as function types. Provides the member constant value which is equal to true, if T is a function type. Otherwise, value is equal to false.

The behavior of a program that adds specializations for is\_function or is\_function\_v is undefined.

-----

### Struct `etl::is_pointer`

``` cpp
(1) template <typename T>
struct is_pointer
{
};

(2) template <typename T>inline constexpr bool is_pointer_v = is_pointer<T>::value;
```

Checks whether T is a pointer to object or a pointer to function (but not a pointer to member/member function). Provides the member constant value which is equal to true, if T is a object/function pointer type. Otherwise, value is equal to false.

The behavior of a program that adds specializations for is\_pointer or is\_pointer\_v is undefined.

-----

### Struct `etl::is_lvalue_reference`

``` cpp
(1) template <typename T>
struct is_lvalue_reference
{
};

(2) template <typename T>inline constexpr bool is_lvalue_reference_v = is_lvalue_reference<T>::value;
```

Checks whether T is a lvalue reference type. Provides the member constant value which is equal to true, if T is a lvalue reference type. Otherwise, value is equal to false.

-----

### Struct `etl::is_rvalue_reference`

``` cpp
(1) template <typename T>
struct is_rvalue_reference
{
};

(2) template <typename T>inline constexpr bool is_rvalue_reference_v = is_rvalue_reference<T>::value;
```

Checks whether T is a rvalue reference type. Provides the member constant value which is equal to true, if T is a rvalue reference type. Otherwise, value is equal to false.

-----

### Struct `etl::is_class`

``` cpp
(1) template <typename T>
struct is_class
: bool_constant<__is_class(T)>
{
};

(2) template <typename T>inline constexpr bool is_class_v = is_class<T>::value;
```

-----

### Struct `etl::is_enum`

``` cpp
(1) template <typename T>
struct is_enum
: bool_constant<__is_enum(T)>
{
};

(2) template <typename T>inline constexpr bool is_enum_v = is_enum<T>::value;
```

-----

### Struct `etl::is_union`

``` cpp
(1) template <typename T>
struct is_union
: bool_constant<__is_union(T)>
{
};

(2) template <typename T>inline constexpr bool is_union_v = is_union<T>::value;
```

-----

### Struct `etl::is_member_pointer`

``` cpp
template <typename T>
struct is_member_pointer
{
};
```

If T is pointer to non-static member object or a pointer to non-static member function, provides the member constant value equal true. For any other type, value is false. The behavior of a program that adds specializations for is\_member\_pointer or is\_member\_pointer\_v (since C++17) is undefined.

-----

### Struct `etl::is_member_function_pointer`

``` cpp
template <typename T>
struct is_member_function_pointer
{
};
```

Checks whether T is a non-static member function pointer. Provides the member constant value which is equal to true, if T is a non-static member function pointer type. Otherwise, value is equal to false.

-----

### Struct `etl::is_member_object_pointer`

``` cpp
template <typename T>
struct is_member_object_pointer
: bool_constant<is_member_pointer_v<T>&&!is_member_function_pointer_v<T>>
{
};
```

Checks whether T is a non-static member object pointer. Provides the member constant value which is equal to true, if T is a non-static member object pointer type. Otherwise, value is equal to false.

-----

### Struct `etl::is_arithmetic`

``` cpp
template <typename T>
struct is_arithmetic
: bool_constant<is_integral_v<T>||is_floating_point_v<T>>
{
};
```

If T is an arithmetic type (that is, an integral type or a floating-point type) or a cv-qualified version thereof, provides the member constant value equal true. For any other type, value is false. The behavior of a program that adds specializations for is\_arithmetic or is\_arithmetic\_v (since C++17) is undefined.

-----

### Struct `etl::is_fundamental`

``` cpp
template <typename T>
struct is_fundamental
: bool_constant<is_arithmetic_v<T>||is_void_v<T>||is_null_pointer_v<T>>
{
};
```

If T is a fundamental type (that is, arithmetic type, void, or nullptr\_t), provides the member constant value equal true. For any other type, value is false.

-----

### Struct `etl::is_scalar`

``` cpp
template <typename T>
struct is_scalar
: bool_constant<is_arithmetic_v<T>||is_enum_v<T>||is_pointer_v<T>||is_member_pointer_v<T>||is_null_pointer_v<T>>
{
};
```

If T is a scalar type (that is a possibly cv-qualified arithmetic, pointer, pointer to member, enumeration, or etl::nullptr\_t type), provides the member constant value equal true. For any other type, value is false.

-----

### Struct `etl::is_object`

``` cpp
template <typename T>
struct is_object
: bool_constant<is_scalar_v<T>||is_array_v<T>||is_union_v<T>||is_class_v<T>>
{
};
```

If T is an object type (that is any possibly cv-qualified type other than function, reference, or void types), provides the member constant value equal true. For any other type, value is false.

-----

### Struct `etl::is_compound`

``` cpp
template <typename T>
struct is_compound
: bool_constant<!is_fundamental_v<T>>
{
};
```

If T is a compound type (that is, array, function, object pointer, function pointer, member object pointer, member function pointer, reference, class, union, or enumeration, including any cv-qualified variants), provides the member constant value equal true. For any other type, value is false.

-----

### Struct `etl::is_bounded_array`

``` cpp
template <typename T>
struct is_bounded_array
{
};
```

Checks whether T is an array type of known bound. Provides the member constant value which is equal to true, if T is an array type of known bound. Otherwise, value is equal to false.

-----

### Struct `etl::is_unbounded_array`

``` cpp
template <typename T>
struct is_unbounded_array
{
};
```

Checks whether T is an array type of unknown bound. Provides the member constant value which is equal to true, if T is an array type of unknown bound. Otherwise, value is equal to false.

-----

### Struct `etl::is_trivially_constructible`

``` cpp
template <typename T, typename ... Args>
struct is_trivially_constructible
: bool_constant<__is_trivially_constructible(T)>
{
};
```

The variable definition does not call any operation that is not trivial. For the purposes of this check, the call to etl::declval is considered trivial.

-----

### Struct `etl::is_nothrow_constructible`

``` cpp
template <typename T, typename ... Args>
struct is_nothrow_constructible
: detail::is_nothrow_constructible_helper<T,Args...>::type
{
};
```

The variable definition does not call any operation that is not trivial. For the purposes of this check, the call to etl::declval is considered trivial.

-----

### Struct `etl::is_default_constructible`

``` cpp
template <typename T>
struct is_default_constructible
{
};
```

If etl::is\_constructible\<T\>::value is true, provides the member constant value equal to true, otherwise value is false.

T shall be a complete type, (possibly cv-qualified) void, or an array of unknown bound. Otherwise, the behavior is undefined. If an instantiation of a template above depends, directly or indirectly, on an incomplete type, and that instantiation could yield a different result if that type were hypothetically completed, the behavior is undefined.

The behavior of a program that adds specializations for any of the templates described on this page is undefined.

-----

### Struct `etl::is_trivially_default_constructible`

``` cpp
template <typename T>
struct is_trivially_default_constructible
: is_trivially_constructible<T>
{
};
```

If etl::is\_trivially\_constructible\<T\>::value is true, provides the member constant value equal to true, otherwise value is false.

T shall be a complete type, (possibly cv-qualified) void, or an array of unknown bound. Otherwise, the behavior is undefined. If an instantiation of a template above depends, directly or indirectly, on an incomplete type, and that instantiation could yield a different result if that type were hypothetically completed, the behavior is undefined.

The behavior of a program that adds specializations for any of the templates described on this page is undefined.

-----

### Struct `etl::is_nothrow_default_constructible`

``` cpp
template <typename T>
struct is_nothrow_default_constructible
: is_nothrow_constructible<T>
{
};
```

If etl::is\_nothrow\_constructible\<T\>::value is true, provides the member constant value equal to true, otherwise value is false.

T shall be a complete type, (possibly cv-qualified) void, or an array of unknown bound. Otherwise, the behavior is undefined. If an instantiation of a template above depends, directly or indirectly, on an incomplete type, and that instantiation could yield a different result if that type were hypothetically completed, the behavior is undefined.

The behavior of a program that adds specializations for any of the templates described on this page is undefined.

-----

### Struct `etl::is_copy_constructible`

``` cpp
template <typename T>
struct is_copy_constructible
{
};
```

If T is not a referenceable type (i.e., possibly cv-qualified void or a function type with a cv-qualifier-seq or a ref-qualifier), provides a member constant value equal to false. Otherwise, provides a member constant value equal to etl::is\_constructible\<T, T const&\>::value.

T shall be a complete type, (possibly cv-qualified) void, or an array of unknown bound. Otherwise, the behavior is undefined. If an instantiation of a template above depends, directly or indirectly, on an incomplete type, and that instantiation could yield a different result if that type were hypothetically completed, the behavior is undefined.

The behavior of a program that adds specializations for any of the templates described on this page is undefined.

-----

### Struct `etl::is_trivially_copy_constructible`

``` cpp
template <typename T>
struct is_trivially_copy_constructible
: is_trivially_constructible<T,add_lvalue_reference_t<add_const_t<T>>>
{
};
```

Same as copy, but uses etl::is\_trivially\_constructible\<T, T const&\>.

T shall be a complete type, (possibly cv-qualified) void, or an array of unknown bound. Otherwise, the behavior is undefined. If an instantiation of a template above depends, directly or indirectly, on an incomplete type, and that instantiation could yield a different result if that type were hypothetically completed, the behavior is undefined.

The behavior of a program that adds specializations for any of the templates described on this page is undefined.

-----

### Struct `etl::is_nothrow_copy_constructible`

``` cpp
template <typename T>
struct is_nothrow_copy_constructible
: is_nothrow_constructible<T,add_lvalue_reference_t<add_const_t<T>>>
{
};
```

Same as copy, but uses etl::is\_nothrow\_constructible\<T, T const&\>.

T shall be a complete type, (possibly cv-qualified) void, or an array of unknown bound. Otherwise, the behavior is undefined. If an instantiation of a template above depends, directly or indirectly, on an incomplete type, and that instantiation could yield a different result if that type were hypothetically completed, the behavior is undefined.

The behavior of a program that adds specializations for any of the templates described on this page is undefined.

-----

### Struct `etl::is_move_constructible`

``` cpp
template <typename T>
struct is_move_constructible
{
};
```

If T is not a referenceable type (i.e., possibly cv-qualified void or a function type with a cv-qualifier-seq or a ref-qualifier), provides a member constant value equal to false. Otherwise, provides a member constant value equal to etl::is\_constructible\<T, T&&\>::value.

-----

### Struct `etl::is_trivially_move_constructible`

``` cpp
template <typename T>
struct is_trivially_move_constructible
: is_trivially_constructible<T,add_rvalue_reference_t<T>>
{
};
```

If T is not a referenceable type (i.e., possibly cv-qualified void or a function type with a cv-qualifier-seq or a ref-qualifier), provides a member constant value equal to false. Otherwise, provides a member constant value equal to etl::is\_trivially\_constructible\<T, T&&\>::value.

-----

### Struct `etl::is_nothrow_move_constructible`

``` cpp
template <typename T>
struct is_nothrow_move_constructible
: is_nothrow_constructible<T,add_rvalue_reference_t<T>>
{
};
```

If T is not a referenceable type (i.e., possibly cv-qualified void or a function type with a cv-qualifier-seq or a ref-qualifier), provides a member constant value equal to false. Otherwise, provides a member constant value equal to etl::is\_nothrow\_constructible\<T, T&&\>::value.

-----

### Struct `etl::is_destructible`

``` cpp
(1) template <typename T>
struct is_destructible
{
    static_assert(detail::is_complete_or_unbounded(type_identity<T>{}), "");
};

(2) template <typename T>inline constexpr auto is_destructible_v = is_destructible<T>::value;
```

Because the C++ program terminates if a destructor throws an exception during stack unwinding (which usually cannot be predicted), all practical destructors are non-throwing even if they are not declared noexcept. All destructors found in the C++ standard library are non-throwing.

*Notes:* [cppreference.com/w/cpp/types/is\_destructible](https://en.cppreference.com/w/cpp/types/is_destructible)

-----

### Struct `etl::is_trivially_destructible`

``` cpp
template <typename T>
struct is_trivially_destructible
: bool_constant<__has_trivial_destructor(T)>
{
};
```

Storage occupied by trivially destructible objects may be reused without calling the destructor. \\notes [cppreference.com/w/cpp/types/is\_destructible](https://en.cppreference.com/w/cpp/types/is_destructible)

-----

### Struct `etl::is_nothrow_destructible`

``` cpp
(1) template <typename Type>
struct is_nothrow_destructible
{
};

(2) template <typename T>inline constexpr bool is_nothrow_destructible_v = is_nothrow_destructible<T>::value;
```

*Notes:* <https://en.cppreference.com/w/cpp/types/is_destructible>

-----

### Struct `etl::has_virtual_destructor`

``` cpp
(1) template <typename T>
struct has_virtual_destructor
: bool_constant<__has_virtual_destructor(T)>
{
};

(2) template <typename T>inline constexpr auto has_virtual_destructor_v = has_virtual_destructor<T>::value;
```

*Notes:* <https://en.cppreference.com/w/cpp/types/has_virtual_destructor>

-----

### Struct `etl::is_assignable`

``` cpp
template <typename T, typename U>
struct is_assignable
: bool_constant<__is_assignable(T,U)>
{
};
```

If the expression etl::declval\<T\>() = etl::declval\<U\>() is well-formed in unevaluated context, provides the member constant value equal true. Otherwise, value is false. Access checks are performed as if from a context unrelated to either type.

-----

### Struct `etl::is_trivially_assignable`

``` cpp
template <typename T, typename U>
struct is_trivially_assignable
: bool_constant<__is_trivially_assignable(T,U)>
{
};
```

If the expression etl::declval\<T\>() = etl::declval\<U\>() is well-formed in unevaluated context, provides the member constant value equal true. Otherwise, value is false. Access checks are performed as if from a context unrelated to either type.

-----

### Struct `etl::is_nothrow_assignable`

``` cpp
template <typename T, typename U>
struct is_nothrow_assignable
: bool_constant<is_assignable_v<T,U>&&detail::is_nothrow_assignable_helper<T,U>::value>
{
};
```

If the expression etl::declval\<T\>() = etl::declval\<U\>() is well-formed in unevaluated context, provides the member constant value equal true. Otherwise, value is false. Access checks are performed as if from a context unrelated to either type.

-----

### Struct `etl::is_copy_assignable`

``` cpp
template <typename T>
struct is_copy_assignable
: is_assignable<add_lvalue_reference_t<T>,add_lvalue_reference_t<const T>>
{
};
```

If T is not a referenceable type (i.e., possibly cv-qualified void or a function type with a cv-qualifier-seq or a ref-qualifier), provides a member constant value equal to false. Otherwise, provides a member constant value equal to etl::is\_assignable\<T&, T const&\>::value.

T shall be a complete type, (possibly cv-qualified) void, or an array of unknown bound. Otherwise, the behavior is undefined. If an instantiation of a template above depends, directly or indirectly, on an incomplete type, and that instantiation could yield a different result if that type were hypothetically completed, the behavior is undefined. The behavior of a program that adds specializations for any of the templates described on this page is undefined.

-----

### Struct `etl::is_trivially_copy_assignable`

``` cpp
template <typename T>
struct is_trivially_copy_assignable
: is_trivially_assignable<add_lvalue_reference_t<T>,add_lvalue_reference_t<const T>>
{
};
```

If T is not a referenceable type (i.e., possibly cv-qualified void or a function type with a cv-qualifier-seq or a ref-qualifier), provides a member constant value equal to false. Otherwise, provides a member constant value equal to etl::is\_trivially\_assignable\<T&, T const&\>::value.

T shall be a complete type, (possibly cv-qualified) void, or an array of unknown bound. Otherwise, the behavior is undefined. If an instantiation of a template above depends, directly or indirectly, on an incomplete type, and that instantiation could yield a different result if that type were hypothetically completed, the behavior is undefined. The behavior of a program that adds specializations for any of the templates described on this page is undefined.

-----

### Struct `etl::is_nothrow_copy_assignable`

``` cpp
template <typename T>
struct is_nothrow_copy_assignable
: is_nothrow_assignable<add_lvalue_reference_t<T>,add_lvalue_reference_t<const T>>
{
};
```

If T is not a referenceable type (i.e., possibly cv-qualified void or a function type with a cv-qualifier-seq or a ref-qualifier), provides a member constant value equal to false. Otherwise, provides a member constant value equal to etl::is\_nothrow\_assignable\<T&, T const&\>::value.

T shall be a complete type, (possibly cv-qualified) void, or an array of unknown bound. Otherwise, the behavior is undefined. If an instantiation of a template above depends, directly or indirectly, on an incomplete type, and that instantiation could yield a different result if that type were hypothetically completed, the behavior is undefined. The behavior of a program that adds specializations for any of the templates described on this page is undefined.

-----

### Struct `etl::is_move_assignable`

``` cpp
template <typename T>
struct is_move_assignable
: is_assignable<add_lvalue_reference_t<T>,add_rvalue_reference_t<T>>
{
};
```

If T is not a referenceable type (i.e., possibly cv-qualified void or a function type with a cv-qualifier-seq or a ref-qualifier), provides a member constant value equal to false. Otherwise, provides a member constant value equal to etl::is\_assignable\<T&, T&&\>::value.

T shall be a complete type, (possibly cv-qualified) void, or an array of unknown bound. Otherwise, the behavior is undefined. If an instantiation of a template above depends, directly or indirectly, on an incomplete type, and that instantiation could yield a different result if that type were hypothetically completed, the behavior is undefined. The behavior of a program that adds specializations for any of the templates described on this page is undefined.

-----

### Struct `etl::is_trivially_move_assignable`

``` cpp
template <typename T>
struct is_trivially_move_assignable
: is_trivially_assignable<add_lvalue_reference_t<T>,add_rvalue_reference_t<T>>
{
};
```

If T is not a referenceable type (i.e., possibly cv-qualified void or a function type with a cv-qualifier-seq or a ref-qualifier), provides a member constant value equal to false. Otherwise, provides a member constant value equal to etl::is\_assignable\<T&, T&&\>::value.

T shall be a complete type, (possibly cv-qualified) void, or an array of unknown bound. Otherwise, the behavior is undefined. If an instantiation of a template above depends, directly or indirectly, on an incomplete type, and that instantiation could yield a different result if that type were hypothetically completed, the behavior is undefined. The behavior of a program that adds specializations for any of the templates described on this page is undefined.

-----

### Struct `etl::is_nothrow_move_assignable`

``` cpp
template <typename T>
struct is_nothrow_move_assignable
: is_nothrow_assignable<add_lvalue_reference_t<T>,add_rvalue_reference_t<T>>
{
};
```

If T is not a referenceable type (i.e., possibly cv-qualified void or a function type with a cv-qualifier-seq or a ref-qualifier), provides a member constant value equal to false. Otherwise, provides a member constant value equal to etl::is\_assignable\<T&, T&&\>::value.

T shall be a complete type, (possibly cv-qualified) void, or an array of unknown bound. Otherwise, the behavior is undefined. If an instantiation of a template above depends, directly or indirectly, on an incomplete type, and that instantiation could yield a different result if that type were hypothetically completed, the behavior is undefined. The behavior of a program that adds specializations for any of the templates described on this page is undefined.

-----

### Struct `etl::is_swappable`

``` cpp
template <typename T>
struct is_swappable
: bool_constant<detail::is_swappable_helper<T>::value>
{
};
```

If T is not a referenceable type (i.e., possibly cv-qualified void or a function type with a cv-qualifier-seq or a ref-qualifier), provides a member constant value equal to false. Otherwise, provides a member constant value equal to etl::is\_swappable\_with\<T&, T&\>::value

-----

### Struct `etl::is_nothrow_swappable`

``` cpp
template <typename T>
struct is_nothrow_swappable
{
};
```

If T is not a referenceable type (i.e., possibly cv-qualified void or a function type with a cv-qualifier-seq or a ref-qualifier), provides a member constant value equal to false. Otherwise, provides a member constant value equal to etl::is\_nothrow\_swappable\_with\<T&, T&\>::value

-----

### Struct `etl::is_swappable_with`

``` cpp
template <typename T, typename U>
struct is_swappable_with
: bool_constant<conjunction_v<detail::is_swappable_with_impl<T,U>,detail::is_swappable_with_impl<U,T>>>
{
};
```
If the expressions swap(etl::declval\<T\>(), etl::declval\<U\>()) and swap(etl::declval\<U\>(), etl::declval\<T\>()) are both well-formed in unevaluated context after using etl::swap; provides the member constant value equal true. Otherwise, value is false. Access checks are performed as if from a context unrelated to either type.

-----

### Struct `etl::alignment_of`

``` cpp
(1) template <typename T>
struct alignment_of
: integral_constant<size_t,alignof(T)>
{
};

(2) template <typename T>inline constexpr size_t alignment_of_v = alignment_of<T>::value;
```

alignment\_of

-----

### Struct `etl::is_trivially_copyable`

``` cpp
template <typename T>
struct is_trivially_copyable
{
};
```

If T is a TriviallyCopyable type, provides the member constant value equal to true. For any other type, value is false. The only trivially copyable types are scalar types, trivially copyable classes, and arrays of such types/classes (possibly cv-qualified). group is\_trivial\_copyable

-----

### Struct `etl::is_trivially_copyable`

``` cpp
template <typename T>
struct is_trivially_copyable<T*>
{
};
```

group is\_trivial\_copyable

-----

### Struct `etl::is_trivial`

``` cpp
(1) template <typename T>
struct is_trivial
: bool_constant<is_trivially_copyable_v<T>and is_trivially_default_constructible_v<T>>
{
};

(2) template <typename T>inline constexpr bool is_trivial_v = is_trivial<T>::value;
```

If T is TrivialType (that is, a scalar type, a trivially copyable class with a trivial default constructor, or array of such type/class, possibly cv-qualified), provides the member constant value equal to true. For any other type, value is false.

*Notes:* [cppreference.com/w/cpp/types/is\_trivial](https://en.cppreference.com/w/cpp/types/is_trivial)

-----

### Struct `etl::is_standard_layout`

``` cpp
template <typename T>
struct is_standard_layout
: bool_constant<__is_standard_layout(T)>
{
};
```

If T is a standard layout type (that is, a scalar type, a standard-layout class, or an array of such type/class, possibly cv-qualified), provides the member constant value equal to true. For any other type, value is false.

-----

### Struct `etl::has_unique_object_representations`

``` cpp
template <typename T>
struct has_unique_object_representations
: bool_constant<__has_unique_object_representations(remove_cv_t<remove_all_extents_t<T>>)>
{
    static_assert(detail::is_complete_or_unbounded(type_identity<T>{}), "");
};
```

If T is TriviallyCopyable and if any two objects of type T with the same value have the same object representation, provides the member constant value equal true. For any other type, value is false.

For the purpose of this trait, two arrays have the same value if their elements have the same values, two non-union classes have the same value if their direct subobjects have the same value, and two unions have the same value if they have the same active member and the value of that member is the same. It is implementation-defined which scalar types satisfy this trait, but unsigned (until C++20) integer types that do not use padding bits are guaranteed to have unique object representations. The behavior is undefined if T is an incomplete type other than (possibly cv-qualified) void or array of unknown bound. The behavior of a program that adds specializations for has\_unique\_object\_representations or has\_unique\_object\_representations\_v is undefined.

-----

### Struct `etl::is_unsigned`

``` cpp
template <typename T>
struct is_unsigned
: detail::is_unsigned<T>::type
{
};
```

If T is an arithmetic type, provides the member constant value equal to true if T(0) \< T(-1): this results in true for the unsigned integer types and the type bool and in false for the signed integer types and the floating-point types. For any other type, value is false. The behavior of a program that adds specializations for is\_unsigned or is\_unsigned\_v (since C++17) is undefined.

-----

### Struct `etl::is_signed`

``` cpp
template <typename T>
struct is_signed
: detail::is_signed<T>::type
{
};
```

If T is an arithmetic type, provides the member constant value equal to true if T(-1) \< T(0): this results in true for the floating-point types and the signed integer types, and in false for the unsigned integer types and the type bool. For any other type, value is false.

-----

### Struct `etl::is_base_of`

``` cpp
template <typename Base, typename Derived>
struct is_base_of
: bool_constant<is_class_v<Base>and is_class_v<Derived>and decltype(detail::test_pre_is_base_of<Base,Derived>(0))::value>
{
};
```

If Derived is derived from Base or if both are the same non-union class (in both cases ignoring cv-qualification), provides the member constant value equal to true. Otherwise value is false.

*Notes:* [cppreference.com/w/cpp/types/is\_base\_of](https://en.cppreference.com/w/cpp/types/is_base_of)

If both Base and Derived are non-union class types, and they are not the same type (ignoring cv-qualification), Derived shall be a complete type; otherwise the behavior is undefined.

-----

### Struct `etl::rank`

``` cpp
template <typename T>
struct rank
: integral_constant<size_t,0>
{
};
```

If Type is an array type, provides the member constant value equal to the number of dimensions of the array. For any other type, value is 0. The behavior of a program that adds specializations for rank or rank\_v is undefined.

-----

### Struct `etl::decay`

``` cpp
template <typename T>
struct decay
{
};
```

Applies lvalue-to-rvalue, array-to-pointer, and function-to-pointer implicit conversions to the type T, removes cv-qualifiers, and defines the resulting type as the member typedef type.

-----

### Struct `etl::common_type`

``` cpp
(1) template <typename ... T>
struct common_type;

(2) template <typename ... T>
using common_type_t = typename common_type<T...>::type;
```

Determines the common type among all types `T...`, that is the type all `T...` can be implicitly converted to. If such a type exists, the member type names that type. Otherwise, there is no member type. \\notes [cppreference.com/w/cpp/types/common\_type](https://en.cppreference.com/w/cpp/types/common_type)

-----

### Struct `etl::is_convertible`

``` cpp
(1) template <typename From, typename To>
struct is_convertible
: bool_constant<(decltype(detail::test_returnable<To>(0))::value&&decltype(detail::test_nonvoid_convertible<From,To>(0))::value)||(is_void_v<From>&&is_void_v<To>)>
{
};

(2) template <typename From, typename To>inline constexpr bool is_convertible_v = is_convertible<From, To>::value;
```
If the imaginary function definition `To test() { return etl::declval<From>(); }` is well-formed, (that is, either `etl::declval<From>()` can be converted to To using implicit conversions, or both From and To are possibly cv-qualified void), provides the member constant value equal to true. Otherwise value is false. For the purposes of this check, the use of `etl::declval` in the return statement is not considered an odr-use. Access checks are performed as if from a context unrelated to either type. Only the validity of the immediate context of the expression in the return statement (including conversions to the return type) is considered.

-----

### Struct `etl::invoke_result`

``` cpp
(1) template <typename F, typename ... ArgTypes>
struct invoke_result
{
};

(2) template <typename F, typename ... ArgTypes>
using invoke_result_t = typename invoke_result<F, ArgTypes...>::type;
```

Deduces the return type of an INVOKE expression at compile time. F and all types in ArgTypes can be any complete type, array of unknown bound, or (possibly cv-qualified) void. The behavior of a program that adds specializations for any of the templates described on this page is undefined. This implementation is copied from **cppreference.com**.

*Notes:* [cppreference.com/w/cpp/types/result\_of](https://en.cppreference.com/w/cpp/types/result_of)

-----

### Struct `etl::aligned_storage`

``` cpp
(1) template <etl::size_t Len, etl::size_t Align = alignof(max_align_t)>
struct aligned_storage
{
    struct type;
};

(2) template <etl::size_t Len, etl::size_t Align = alignof(max_align_t)>
using aligned_storage_t = typename aligned_storage<Len, Align>::type;
```

Provides the nested type type, which is a trivial standard-layout type suitable for use as uninitialized storage for any object whose size is at most Len and whose alignment requirement is a divisor of Align. The default value of Align is the most stringent (the largest) alignment requirement for any object whose size is at most Len. If the default value is not used, Align must be the value of alignof(T) for some type T, or the behavior is undefined.

-----

### Struct `etl::aligned_union`

``` cpp
template <etl::size_t Len, typename ... Types>
struct aligned_union
{
    struct type;
};
```

Provides the nested type type, which is a trivial standard-layout type of a size and alignment suitable for use as uninitialized storage for an object of any of the types listed in Types. The size of the storage is at least Len. aligned\_union also determines the strictest (largest) alignment requirement among all Types and makes it available as the constant alignment\_value. If sizeof…(Types) == 0 or if any of the types in Types is not a complete object type, the behavior is undefined. It is implementation-defined whether any extended alignment is supported. The behavior of a program that adds specializations for aligned\_union is undefined.

-----

### Struct `etl::underlying_type`

``` cpp
template <typename T>
struct underlying_type
{
};
```

The underlying type of an enum.

-----

### Unexposed entity `etl::is_scoped_enum_v`

``` cpp
template <typename T>inline constexpr bool is_scoped_enum_v = is_scoped_enum<T>::value;
```

Checks whether T is an scoped enumeration type. Provides the member constant value which is equal to true, if T is an scoped enumeration type. Otherwise, value is equal to false. The behavior of a program that adds specializations for is\_scoped\_enum or is\_scoped\_enum\_v is undefined.

*Notes:* [cppreference.com/w/cpp/types/is\_scoped\_enum](https://en.cppreference.com/w/cpp/types/is_scoped_enum)

-----

### Function `etl::is_constant_evaluated`

``` cpp
constexpr bool is_constant_evaluated() noexcept;
```

Detects whether the function call occurs within a constant-evaluated context. Returns true if the evaluation of the call occurs within the evaluation of an expression or conversion that is manifestly constant-evaluated; otherwise returns false.

*Notes:* [cppreference.com/w/cpp/types/is\_constant\_evaluated](https://en.cppreference.com/w/cpp/types/is_constant_evaluated)

-----
