---
title: "mutex.hpp"
---

# Header file `mutex.hpp`

``` cpp
#include "etl/version.hpp"
#include "etl/chrono.hpp"

namespace etl
{
    struct defer_lock_t;

    struct try_to_lock_t;

    struct adopt_lock_t;

    constexpr etl::defer_lock_t const defer_lock;

    constexpr etl::try_to_lock_t const try_to_lock;

    constexpr etl::adopt_lock_t const adopt_lock;

    template <typename MutexT>
    struct lock_guard;

    template <typename Mutex>
    struct unique_lock;

    template <typename Mutex>
    void swap(unique_lock<Mutex>& lhs, unique_lock<Mutex>& rhs) noexcept('hidden');
}
```

### Struct `etl::defer_lock_t`

``` cpp
struct defer_lock_t
{
};
```

Empty class tag types used to specify locking strategy for etl::lock\_guard, etl::scoped\_lock, etl::unique\_lock, and etl::shared\_lock.

Do not acquire ownership of the mutex.

-----

### Struct `etl::try_to_lock_t`

``` cpp
struct try_to_lock_t
{
};
```

Empty class tag types used to specify locking strategy for etl::lock\_guard, etl::scoped\_lock, etl::unique\_lock, and etl::shared\_lock.

Try to acquire ownership of the mutex without blocking.

-----

### Struct `etl::adopt_lock_t`

``` cpp
struct adopt_lock_t
{
};
```

Empty class tag types used to specify locking strategy for etl::lock\_guard, etl::scoped\_lock, etl::unique\_lock, and etl::shared\_lock.

Assume the calling thread already has ownership of the mutex.

-----

### Variable `etl::defer_lock`

``` cpp
constexpr etl::defer_lock_t const defer_lock;
```

Instances of empty struct tag types. See defer\_lock\_t.

-----

### Variable `etl::try_to_lock`

``` cpp
constexpr etl::try_to_lock_t const try_to_lock;
```

Instances of empty struct tag types. See try\_to\_lock\_t.

-----

### Variable `etl::adopt_lock`

``` cpp
constexpr etl::adopt_lock_t const adopt_lock;
```

Instances of empty struct tag types. See adopt\_lock\_t.

-----

### Struct `etl::lock_guard`

``` cpp
template <typename MutexT>
struct lock_guard
{
};
```

The class lock\_guard is a mutex wrapper that provides a convenient RAII-style mechanism for owning a mutex for the duration of a scoped block. When a lock\_guard object is created, it attempts to take ownership of the mutex it is given. When control leaves the scope in which the lock\_guard object was created, the lock\_guard is destructed and the mutex is released. The lock\_guard class is non-copyable.

-----

### Struct `etl::unique_lock`

``` cpp
template <typename Mutex>
struct unique_lock
{
    unique_lock() noexcept = default;

    explicit unique_lock('hidden'& m);

    unique_lock('hidden'& m, etl::defer_lock_t) noexcept;

    unique_lock('hidden'& m, etl::try_to_lock_t) noexcept;

    unique_lock('hidden'& m, etl::adopt_lock_t);

    template <typename Clock, typename Duration>
    unique_lock('hidden'& m, chrono::time_point<Clock, Duration> const& abs_time) noexcept;

    template <typename Rep, typename Period>
    unique_lock('hidden'& m, chrono::duration<Rep, Period> const& rel_time) noexcept;

    unique_lock(const unique_lock<Mutex>&) = delete;

    unique_lock<Mutex>& operator=(const unique_lock<Mutex>&) = delete;

    unique_lock(unique_lock<Mutex>&& u) noexcept;

    unique_lock<Mutex>& operator=(unique_lock<Mutex>&& u) noexcept;

    void lock() noexcept('hidden');

    bool try_lock() noexcept('hidden');

    template <typename Rep, typename Period>
    bool try_lock_for(chrono::duration<Rep, Period> const& dur) noexcept('hidden');

    template <typename Clock, typename Duration>
    bool try_lock_until(chrono::time_point<Clock, Duration> const& tp) noexcept('hidden');

    void unlock();

    void swap(unique_lock<Mutex>& other) noexcept;

    'hidden'* release() noexcept;

    bool owns_lock() const noexcept;

    explicit operator bool() const noexcept;

    'hidden'* mutex() const noexcept;
};
```

The class unique\_lock is a general-purpose mutex ownership wrapper allowing deferred locking, time-constrained attempts at locking, recursive locking, transfer of lock ownership, and use with condition variables.

The class unique\_lock is movable, but not copyable – it meets the requirements of MoveConstructible and MoveAssignable but not of CopyConstructible or CopyAssignable. The class unique\_lock meets the BasicLockable requirements. If Mutex meets the Lockable requirements, unique\_lock also meets the Lockable requirements (ex.: can be used in lock); if Mutex meets the TimedLockable requirements, unique\_lock also meets the TimedLockable requirements.

### Constructor `etl::unique_lock::unique_lock`

``` cpp
unique_lock() noexcept = default;
```

Constructs a unique\_lock with no associated mutex.

-----

### Constructor `etl::unique_lock::unique_lock`

``` cpp
explicit unique_lock('hidden'& m);
```

Constructs a unique\_lock with m as the associated mutex. Additionally: Locks the associated mutex by calling m.lock(). The behavior is undefined if the current thread already owns the mutex except when the mutex is recursive.

-----

### Constructor `etl::unique_lock::unique_lock`

``` cpp
unique_lock('hidden'& m, etl::defer_lock_t) noexcept;
```

Constructs a unique\_lock with m as the associated mutex. Additionally: Does not lock the associated mutex.

-----

### Constructor `etl::unique_lock::unique_lock`

``` cpp
unique_lock('hidden'& m, etl::try_to_lock_t) noexcept;
```

Constructs a unique\_lock with m as the associated mutex. Additionally: Tries to lock the associated mutex without blocking by calling m.try\_lock(). The behavior is undefined if the current thread already owns the mutex except when the mutex is recursive.

-----

### Constructor `etl::unique_lock::unique_lock`

``` cpp
unique_lock('hidden'& m, etl::adopt_lock_t);
```

Constructs a unique\_lock with m as the associated mutex. Additionally: Assumes the calling thread already owns m.

-----

### Constructor `etl::unique_lock::unique_lock`

``` cpp
template <typename Clock, typename Duration>
unique_lock('hidden'& m, chrono::time_point<Clock, Duration> const& abs_time) noexcept;
```

Constructs a unique\_lock with m as the associated mutex. Additionally: Tries to lock the associated mutex by calling m.try\_lock\_until(timeout\_time). Blocks until specified timeout\_time has been reached or the lock is acquired, whichever comes first. May block for longer than until timeout\_time has been reached.

-----

### Constructor `etl::unique_lock::unique_lock`

``` cpp
template <typename Rep, typename Period>
unique_lock('hidden'& m, chrono::duration<Rep, Period> const& rel_time) noexcept;
```

Constructs a unique\_lock with m as the associated mutex. Additionally: Tries to lock the associated mutex by calling m.try\_lock\_for(timeout\_duration). Blocks until specified timeout\_duration has elapsed or the lock is acquired, whichever comes first. May block for longer than timeout\_duration.

-----

### Constructor `etl::unique_lock::unique_lock`

``` cpp
unique_lock(const unique_lock<Mutex>&) = delete;
```

Deleted copy constructor. unique\_lock is move only.

-----

### Function `etl::unique_lock::operator=`

``` cpp
unique_lock<Mutex>& operator=(const unique_lock<Mutex>&) = delete;
```

Deleted copy assignment. unique\_lock is move only.

-----

### Constructor `etl::unique_lock::unique_lock`

``` cpp
unique_lock(unique_lock<Mutex>&& u) noexcept;
```

Move constructor. Initializes the unique\_lock with the contents of other. Leaves other with no associated mutex.

-----

### Function `etl::unique_lock::operator=`

``` cpp
unique_lock<Mutex>& operator=(unique_lock<Mutex>&& u) noexcept;
```
Move assignment operator. Replaces the contents with those of other using move semantics. If prior to the call \*this has an associated mutex and has acquired ownership of it, the mutex is unlocked.

-----

### Function `etl::unique_lock::lock`

``` cpp
void lock() noexcept('hidden');
```

Locks (i.e., takes ownership of) the associated mutex.

-----

### Function `etl::unique_lock::try_lock`

``` cpp
bool try_lock() noexcept('hidden');
```

Tries to lock (i.e., takes ownership of) the associated mutex without blocking.

*Return values:* true if the ownership of the mutex has been acquired successfully, false otherwise.

-----

### Function `etl::unique_lock::try_lock_for`

``` cpp
template <typename Rep, typename Period>
bool try_lock_for(chrono::duration<Rep, Period> const& dur) noexcept('hidden');
```

Tries to lock (i.e., takes ownership of) the associated mutex. Blocks until specified timeout\_duration has elapsed or the lock is acquired, whichever comes first. On successful lock acquisition returns true, otherwise returns false. Effectively calls mutex()-\>try\_lock\_for(timeout\_duration). This function may block for longer than timeout\_duration due to scheduling or resource contention delays.

-----

### Function `etl::unique_lock::try_lock_until`

``` cpp
template <typename Clock, typename Duration>
bool try_lock_until(chrono::time_point<Clock, Duration> const& tp) noexcept('hidden');
```

Tries to lock (i.e., takes ownership of) the associated mutex without blocking.

-----

### Function `etl::unique_lock::unlock`

``` cpp
void unlock();
```

Unlocks (i.e., releases ownership of) the associated mutex and releases ownership. Silently does nothing, if there is no associated mutex or if the mutex is not locked.

-----

### Function `etl::unique_lock::swap`

``` cpp
void swap(unique_lock<Mutex>& other) noexcept;
```

Exchanges the internal states of the lock objects.

-----

### Function `etl::unique_lock::release`

``` cpp
'hidden'* release() noexcept;
```

Breaks the association of the associated mutex, if any, and \*this. No locks are unlocked. If the \*this held ownership of the associated mutex prior to the call, the caller is now responsible to unlock the mutex.

*Return values:* Pointer to the associated mutex or a null pointer if there was no associated mutex.

-----

### Function `etl::unique_lock::owns_lock`

``` cpp
bool owns_lock() const noexcept;
```

Checks whether \*this owns a locked mutex or not.

-----

### Conversion operator `etl::unique_lock::operator bool`

``` cpp
explicit operator bool() const noexcept;
```

Checks whether \*this owns a locked mutex or not.

-----

### Function `etl::unique_lock::mutex`

``` cpp
'hidden'* mutex() const noexcept;
```

Returns a pointer to the associated mutex, or a null pointer if there is no associated mutex.

-----

-----

### Function `etl::swap`

``` cpp
template <typename Mutex>
void swap(unique_lock<Mutex>& lhs, unique_lock<Mutex>& rhs) noexcept('hidden');
```

Specializes the swap algorithm for unique\_lock. Exchanges the state of lhs with that of rhs.

-----
