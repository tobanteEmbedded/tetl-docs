---
title: "memory.hpp"
---

# Header file `memory.hpp`

``` cpp
#include "etl/version.hpp"
#include "etl/bit.hpp"
#include "etl/cassert.hpp"
#include "etl/cstddef.hpp"
#include "etl/limits.hpp"
#include "etl/type_traits.hpp"
#include "etl/warning.hpp"

namespace etl
{
    //=== addressof ===//
    template <typename T>
    enable_if_t<is_object_v<T>, T *> addressof(T& arg) noexcept;
    template <typename T>
    enable_if_t<!is_object_v<T>, T *> addressof(T& arg) noexcept;
    template <typename T>
    auto addressof(T const&&) = delete;

    //=== destroy ===//
    template <typename T>
    constexpr void destroy_at(T* p);
    template <typename ForwardIt>
    constexpr void destroy(ForwardIt first, ForwardIt last);
    template <typename ForwardIt, typename Size>
    constexpr ForwardIt destroy_n(ForwardIt first, Size n);

    //=== pointer_traits ===//
    template <typename Ptr>
    struct pointer_traits;
    template <typename T>
    struct pointer_traits<T*>;

    struct allocator_arg_t;

    constexpr etl::allocator_arg_t const allocator_arg;

    template <typename Type, typename Alloc>
    struct uses_allocator;

    template <typename Type, typename Alloc>inline constexpr auto uses_allocator_v = uses_allocator<Type, Alloc>::value;

    template <typename Type, etl::intptr_t BaseAddress = 0, typename StorageType = uint16_t>
    class small_ptr;

    //=== pointer_like_traits ===//
    template <typename T>
    struct pointer_like_traits;
    template <typename T>
    struct pointer_like_traits<T*>;
    template <typename T>
    struct pointer_like_traits<const T>;
    template <typename T>
    struct pointer_like_traits<const T*>;
    template <>
    struct pointer_like_traits<uintptr_t>;

    template <typename PointerT, unsigned int IntBits, typename PtrTraits>
    class pointer_int_pair_info;

    template <typename PointerT, unsigned int IntBits, typename IntType = unsigned, typename PtrTraits = pointer_like_traits<PointerT>, typename Info = pointer_int_pair_info<PointerT,IntBits,PtrTraits>>>
    class pointer_int_pair;

    template <typename PtrT, unsigned int IntBits, typename IntT, typename PtrTraits>
    struct pointer_like_traits<pointer_int_pair<PtrT, IntBits, IntT, PtrTraits>;

    template <typename T>
    class default_delete;

    template <typename T>
    class default_delete<T[]>;

    void* align(etl::size_t alignment, etl::size_t size, void*& ptr, etl::size_t& space) noexcept;
}
```

### Function `etl::addressof`

``` cpp
(1) template <typename T>
enable_if_t<is_object_v<T>, T *> addressof(T& arg) noexcept;

(2) template <typename T>
enable_if_t<!is_object_v<T>, T *> addressof(T& arg) noexcept;

(3) template <typename T>
auto addressof(T const&&) = delete;
```

Obtains the actual address of the object or function arg, even in presence of overloaded operator&.

-----

### Function `etl::destroy_at`

``` cpp
(1) template <typename T>
constexpr void destroy_at(T* p);

(2) template <typename ForwardIt>
constexpr void destroy(ForwardIt first, ForwardIt last);

(3) template <typename ForwardIt, typename Size>
constexpr ForwardIt destroy_n(ForwardIt first, Size n);
```

If T is not an array type, calls the destructor of the object pointed to by p, as if by p-\>\~T(). If T is an array type, recursively destroys elements of \*p in order, as if by calling destroy(begin(\*p), end(\*p)).

-----

### Struct `etl::pointer_traits`

``` cpp
(1) template <typename Ptr>
struct pointer_traits
{
    using pointer = Ptr;
    using element_type = typename Ptr::element_type;
    using difference_type = typename Ptr::difference_type;

    static pointer pointer_to(etl::pointer_traits::element_type& r);
};

(2) template <typename T>
struct pointer_traits<T*>
{
    using pointer = T*;
    using element_type = T;
    using difference_type = ::etl::ptrdiff_t;

    template <typename U>
    using rebind = U*;

    static pointer pointer_to(etl::pointer_traits<type-parameter-0-0 *>::element_type& r);
};
```

The pointer\_traits class template provides the standardized way to access certain properties of pointer-like types.

*Notes:* [cppreference.com/w/cpp/memory/pointer\_traits](https://en.cppreference.com/w/cpp/memory/pointer_traits)

### Type alias `etl::pointer_traits::pointer`

``` cpp
using pointer = Ptr;
```

The type …

-----

### Type alias `etl::pointer_traits::element_type`

``` cpp
using element_type = typename Ptr::element_type;
```

The type …

-----

### Type alias `etl::pointer_traits::difference_type`

``` cpp
using difference_type = typename Ptr::difference_type;
```

The type …

-----

### Function `etl::pointer_traits::pointer_to`

``` cpp
static pointer pointer_to(etl::pointer_traits::element_type& r);
```

Constructs a dereferenceable pointer or pointer-like object (“fancy pointer”) to its argument.

*Return values:* A pointer to r, of the type pointer\_traits::pointer.

*Notes:* [cppreference.com/w/cpp/memory/pointer\_traits/pointer\_to ](https://en.cppreference.com/w/cpp/memory/pointer_traits/pointer_to)

#### Parameters

  - `r` - Reference to an object of type element\_type&.

-----

-----

### Struct `etl::allocator_arg_t`

``` cpp
struct allocator_arg_t
{
};
```

allocator\_arg\_t is an empty class type used to disambiguate the overloads of constructors and member functions of allocator-aware objects.

-----

### Variable `etl::allocator_arg`

``` cpp
constexpr etl::allocator_arg_t const allocator_arg;
```

allocator\_arg is a constant of type allocator\_arg\_t used to disambiguate, at call site, the overloads of the constructors and member functions of allocator-aware objects.

-----

### Struct `etl::uses_allocator`

``` cpp
template <typename Type, typename Alloc>
struct uses_allocator
: detail::uses_allocator_impl<Type,Alloc>::type
{
};
```

If T has a member typedef allocator\_type which is convertible from Alloc, the member constant value is true. Otherwise value is false.

-----

### Unexposed entity `etl::uses_allocator_v`

``` cpp
template <typename Type, typename Alloc>inline constexpr auto uses_allocator_v = uses_allocator<Type, Alloc>::value;
```

If T has a member typedef allocator\_type which is convertible from Alloc, the member constant value is true. Otherwise value is false.

-----

### Class `etl::small_ptr`

``` cpp
template <typename Type, etl::intptr_t BaseAddress = 0, typename StorageType = uint16_t>
class small_ptr
{
public:
    small_ptr() = default;

    small_ptr(etl::nullptr_t null);

    small_ptr(Type* ptr);

    Type* get() noexcept;

    Type const* get() const noexcept;

    StorageType compressed_value() const noexcept;

    Type* operator->() const;

    Type& operator*();

    Type const& operator*() const;

    small_ptr<Type, BaseAddress, StorageType> operator++(int) noexcept;

    small_ptr<Type, BaseAddress, StorageType>& operator++() noexcept;

    small_ptr<Type, BaseAddress, StorageType> operator--(int) noexcept;

    small_ptr<Type, BaseAddress, StorageType>& operator--() noexcept;

    etl::ptrdiff_t operator-(small_ptr<Type, BaseAddress, StorageType> other) const noexcept;

    operator Type*() noexcept;

    operator Type const*() const noexcept;
};
```

Compressed pointer to specified size. Intended to be used as a drop in replacement for native pointers.

Uses the base address to calculate an offset, which will be stored internally. If used on micro controllers, the base address should be set to the start of RAM. See your linker script.

### Constructor `etl::small_ptr::small_ptr`

``` cpp
small_ptr() = default;
```

Default construct empty small\_ptr. May contain garbage.

-----

### Constructor `etl::small_ptr::small_ptr`

``` cpp
small_ptr(etl::nullptr_t null);
```

Construct from nullptr.

-----

### Constructor `etl::small_ptr::small_ptr`

``` cpp
small_ptr(Type* ptr);
```

Construct from raw pointer.

-----

### Function `etl::small_ptr::get`

``` cpp
Type* get() noexcept;
```

Returns a raw pointer to Type.

-----

### Function `etl::small_ptr::get`

``` cpp
Type const* get() const noexcept;
```

Returns a raw pointer to const Type.

-----

### Function `etl::small_ptr::compressed_value`

``` cpp
StorageType compressed_value() const noexcept;
```

Returns the compressed underlying integer address.

-----

### Function `etl::small_ptr::operator->`

``` cpp
Type* operator->() const;
```

Returns a raw pointer to Type.

-----

### Function `etl::small_ptr::operator*`

``` cpp
Type& operator*();
```

Dereference pointer to Type&.

-----

### Function `etl::small_ptr::operator*`

``` cpp
Type const& operator*() const;
```

Dereference pointer to Type const&.

-----

### Function `etl::small_ptr::operator++`

``` cpp
small_ptr<Type, BaseAddress, StorageType> operator++(int) noexcept;
```

Pre increment of pointer.

-----

### Function `etl::small_ptr::operator++`

``` cpp
small_ptr<Type, BaseAddress, StorageType>& operator++() noexcept;
```

Post increment of pointer.

-----

### Function `etl::small_ptr::operator--`

``` cpp
small_ptr<Type, BaseAddress, StorageType> operator--(int) noexcept;
```

Pre decrement of pointer.

-----

### Function `etl::small_ptr::operator--`

``` cpp
small_ptr<Type, BaseAddress, StorageType>& operator--() noexcept;
```

Post decrement of pointer.

-----

### Function `etl::small_ptr::operator-`

``` cpp
etl::ptrdiff_t operator-(small_ptr<Type, BaseAddress, StorageType> other) const noexcept;
```

Returns distance from this to other.

-----

### Conversion operator `etl::small_ptr::operator Type*`

``` cpp
operator Type*() noexcept;
```

Implicit conversion to raw pointer to mutable.

-----

### Conversion operator `etl::small_ptr::operator Type const*`

``` cpp
operator Type const*() const noexcept;
```

Implicit conversion to raw pointer to const.

-----

-----

### Struct `etl::pointer_like_traits`

``` cpp
(1) template <typename T>
struct pointer_like_traits;

(2) template <typename T>
struct pointer_like_traits<T*>
{
};

(3) template <typename T>
struct pointer_like_traits<const T>
{
};

(4) template <typename T>
struct pointer_like_traits<const T*>
{
};

(5) template <>
struct pointer_like_traits<uintptr_t>
{
};
```

A traits type that is used to handle pointer types and things that are just wrappers for pointers as a uniform entity.

-----

### Class `etl::pointer_int_pair`

``` cpp
template <typename PointerT, unsigned int IntBits, typename IntType = unsigned, typename PtrTraits = pointer_like_traits<PointerT>, typename Info = pointer_int_pair_info<PointerT,IntBits,PtrTraits>>>
class pointer_int_pair
{
public:
    static pointer_int_pair<PointerT, IntBits, IntType, PtrTraits, Info> get_from_opaque_value(void const* v);
};
```

This class implements a pair of a pointer and small integer.  It is designed to represent this in the space required by one pointer by bitmangling the integer into the low part of the pointer.  This can only be done for small integers: typically up to 3 bits, but it depends on the number of bits available according to pointer\_like\_traits for the type.

Note that pointer\_int\_pair always puts the IntVal part in the highest bits possible.  For example, pointer\_int\_pair\<void\*, 1, bool\> will put the bit for the bool into bit \#2, not bit \#0, which allows the low two bits to be used for something else.  For example, this allows: pointer\_int\_pair\<pointer\_int\_pair\<void\*, 1, bool\>, 1, bool\> … and the two bools will land in different bits.

### Function `etl::pointer_int_pair::get_from_opaque_value`

``` cpp
static pointer_int_pair<PointerT, IntBits, IntType, PtrTraits, Info> get_from_opaque_value(void const* v);
```

Allow pointer\_int\_pairs to be created from const void \* if and only if the pointer type could be created from a const void \*.

-----

-----

### Function `etl::align`

``` cpp
void* align(etl::size_t alignment, etl::size_t size, void*& ptr, etl::size_t& space) noexcept;
```

Given a pointer ptr to a buffer of size space, returns a pointer aligned by the specified alignment for size number of bytes and decreases space argument by the number of bytes used for alignment. The first aligned address is returned.

The function modifies the pointer only if it would be possible to fit the wanted number of bytes aligned by the given alignment into the buffer. If the buffer is too small, the function does nothing and returns nullptr.

The behavior is undefined if alignment is not a power of two.

-----
