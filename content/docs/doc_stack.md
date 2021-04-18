---
title: "stack.hpp"
---

# Header file `stack.hpp`

``` cpp
#include "etl/version.hpp"
#include "etl/iterator.hpp"
#include "etl/type_traits.hpp"

namespace etl
{
    template <typename T, typename Container>
    class stack;

    template <typename T, typename Container, int _concept_requires_215 = 42, ::etl::enable_if_t<(_concept_requires_215 == 43) || (is_swappable_v<Container>), int> = 0>
    constexpr void swap(stack<T, Container>& lhs, stack<T, Container>& rhs) noexcept('hidden');
}
```

### Class `etl::stack` \[Containers\]

``` cpp
template <typename T, typename Container>
class stack
{
public:
    constexpr stack();

    constexpr stack(Container const& cont);

    constexpr stack(Container&& cont);

    constexpr stack(const stack<T, Container>& other) = default;

    constexpr stack(stack<T, Container>&& other) noexcept = default;

    constexpr bool empty() const noexcept('hidden');

    constexpr 'hidden' size() const noexcept('hidden');

    constexpr 'hidden' top() noexcept('hidden');

    constexpr 'hidden' top() const noexcept('hidden');

    constexpr void push('hidden' const& x) noexcept('hidden');

    constexpr void push('hidden'&& x) noexcept('hidden');

    template <typename ... Args>
    constexpr auto emplace(Args &&... args) noexcept('hidden');

    constexpr void pop() noexcept('hidden');

    constexpr void swap(stack<T, Container>& s) noexcept('hidden');

    friend constexpr bool operator==(const stack<T, Container>& lhs, const stack<T, Container>& rhs) noexcept('hidden');

    friend constexpr bool operator!=(const stack<T, Container>& lhs, const stack<T, Container>& rhs) noexcept('hidden');

    friend constexpr bool operator<(const stack<T, Container>& lhs, const stack<T, Container>& rhs) noexcept('hidden');

    friend constexpr bool operator<=(const stack<T, Container>& lhs, const stack<T, Container>& rhs) noexcept('hidden');

    friend constexpr bool operator>(const stack<T, Container>& lhs, const stack<T, Container>& rhs) noexcept('hidden');

    friend constexpr bool operator>=(const stack<T, Container>& lhs, const stack<T, Container>& rhs) noexcept('hidden');
};
```

The stack class is a container adapter that gives the programmer the functionality of a stack - specifically, a LIFO (last-in, first-out) data structure.

The class template acts as a wrapper to the underlying container - only a specific set of functions is provided. The stack pushes and pops the element from the back of the underlying container, known as the top of the stack.

### Constructor `etl::stack::stack`

``` cpp
constexpr stack();
```

Default constructor. Value-initializes the container.

-----

### Constructor `etl::stack::stack`

``` cpp
constexpr stack(Container const& cont);
```

Copy-constructs the underlying container c with the contents of cont.

-----

### Constructor `etl::stack::stack`

``` cpp
constexpr stack(Container&& cont);
```

Move-constructs the underlying container c with cont .

-----

### Constructor `etl::stack::stack`

``` cpp
constexpr stack(const stack<T, Container>& other) = default;
```

Copy constructor.

-----

### Constructor `etl::stack::stack`

``` cpp
constexpr stack(stack<T, Container>&& other) noexcept = default;
```

Move constructor.

-----

### Function `etl::stack::empty`

``` cpp
constexpr bool empty() const noexcept('hidden');
```

Checks if the underlying container has no elements.

-----

### Function `etl::stack::size`

``` cpp
constexpr 'hidden' size() const noexcept('hidden');
```

Returns the number of elements in the underlying container.

-----

### Function `etl::stack::top`

``` cpp
constexpr 'hidden' top() noexcept('hidden');
```

Returns reference to the top element in the stack. This is the most recently pushed element. This element will be removed on a call to pop().

-----

### Function `etl::stack::top`

``` cpp
constexpr 'hidden' top() const noexcept('hidden');
```

Returns reference to the top element in the stack. This is the most recently pushed element. This element will be removed on a call to pop().

-----

### Function `etl::stack::push`

``` cpp
constexpr void push('hidden' const& x) noexcept('hidden');
```

Pushes the given element value to the top of the stack.

-----

### Function `etl::stack::push`

``` cpp
constexpr void push('hidden'&& x) noexcept('hidden');
```

Pushes the given element value to the top of the stack.

-----

### Function `etl::stack::emplace`

``` cpp
template <typename ... Args>
constexpr auto emplace(Args &&... args) noexcept('hidden');
```

Pushes a new element on top of the stack. The element is constructed in-place, i.e. no copy or move operations are performed. The constructor of the element is called with exactly the same arguments as supplied to the function.

-----

### Function `etl::stack::pop`

``` cpp
constexpr void pop() noexcept('hidden');
```

Removes the top element from the stack.

*Complexity:* Equal to the complexity of Container::pop\_back.

-----

### Function `etl::stack::swap`

``` cpp
constexpr void swap(stack<T, Container>& s) noexcept('hidden');
```

Exchanges the contents of the container adaptor with those of other.

-----

### Friend function `operator==`

``` cpp
friend constexpr bool operator==(const stack<T, Container>& lhs, const stack<T, Container>& rhs) noexcept('hidden');
```

Compares the contents of the underlying containers of two container adaptors. The comparison is done by applying the corresponding operator to the underlying containers.

-----

### Friend function `operator!=`

``` cpp
friend constexpr bool operator!=(const stack<T, Container>& lhs, const stack<T, Container>& rhs) noexcept('hidden');
```

Compares the contents of the underlying containers of two container adaptors. The comparison is done by applying the corresponding operator to the underlying containers.

-----

### Friend function `operator<`

``` cpp
friend constexpr bool operator<(const stack<T, Container>& lhs, const stack<T, Container>& rhs) noexcept('hidden');
```

Compares the contents of the underlying containers of two container adaptors. The comparison is done by applying the corresponding operator to the underlying containers.

-----

### Friend function `operator<=`

``` cpp
friend constexpr bool operator<=(const stack<T, Container>& lhs, const stack<T, Container>& rhs) noexcept('hidden');
```

Compares the contents of the underlying containers of two container adaptors. The comparison is done by applying the corresponding operator to the underlying containers.

-----

### Friend function `operator>`

``` cpp
friend constexpr bool operator>(const stack<T, Container>& lhs, const stack<T, Container>& rhs) noexcept('hidden');
```

Compares the contents of the underlying containers of two container adaptors. The comparison is done by applying the corresponding operator to the underlying containers.

-----

### Friend function `operator>=`

``` cpp
friend constexpr bool operator>=(const stack<T, Container>& lhs, const stack<T, Container>& rhs) noexcept('hidden');
```

Compares the contents of the underlying containers of two container adaptors. The comparison is done by applying the corresponding operator to the underlying containers.

-----

-----

### Function `etl::swap`

``` cpp
template <typename T, typename Container, int _concept_requires_215 = 42, ::etl::enable_if_t<(_concept_requires_215 == 43) || (is_swappable_v<Container>), int> = 0>
constexpr void swap(stack<T, Container>& lhs, stack<T, Container>& rhs) noexcept('hidden');
```

Specializes the swap algorithm for stack. Swaps the contents of lhs and rhs. This overload only participates in overload resolution if is\_swappable\<Container\>::value is true.

-----
