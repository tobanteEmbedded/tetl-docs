---
title: "chrono.hpp"
---

# Header file `chrono.hpp`

``` cpp
#include "etl/version.hpp"
#include "etl/ratio.hpp"
#include "etl/type_traits.hpp"

namespace etl
{
    namespace chrono
    {
        template <typename Rep>
        struct duration_values;

        //=== treat_as_floating_point ===//
        template <typename Rep>
        struct treat_as_floating_point;
        template <typename Rep>inline constexpr bool treat_as_floating_point_v = treat_as_floating_point<Rep>::value;

        template <typename Rep, typename Period = etl::ratio<1>>>
        class duration;

        template <typename Clock, typename Duration = typename Clock::duration>
        class time_point;

        template <typename Rep1, typename Period1, typename Rep2, typename Period2>
        constexpr bool operator==(duration<Rep1, Period1> const& lhs, duration<Rep2, Period2> const& rhs);

        template <typename Rep1, typename Period1, typename Rep2, typename Period2>
        constexpr bool operator!=(duration<Rep1, Period1> const& lhs, duration<Rep2, Period2> const& rhs);

        template <typename Rep1, typename Period1, typename Rep2, typename Period2>
        constexpr bool operator<(duration<Rep1, Period1> const& lhs, duration<Rep2, Period2> const& rhs);

        template <typename Rep1, typename Period1, typename Rep2, typename Period2>
        constexpr bool operator<=(duration<Rep1, Period1> const& lhs, duration<Rep2, Period2> const& rhs);

        template <typename Rep1, typename Period1, typename Rep2, typename Period2>
        constexpr bool operator>(duration<Rep1, Period1> const& lhs, duration<Rep2, Period2> const& rhs);

        template <typename Rep1, typename Period1, typename Rep2, typename Period2>
        constexpr bool operator>=(duration<Rep1, Period1> const& lhs, duration<Rep2, Period2> const& rhs);

        template <typename Clock, typename Dur1, typename Dur2>
        constexpr bool operator==(time_point<Clock, Dur1> const& lhs, time_point<Clock, Dur2> const& rhs) noexcept;

        template <typename Clock, typename Dur1, typename Dur2>
        constexpr bool operator!=(time_point<Clock, Dur1> const& lhs, time_point<Clock, Dur2> const& rhs) noexcept;

        template <typename Clock, typename Dur1, typename Dur2>
        constexpr bool operator<(time_point<Clock, Dur1> const& lhs, time_point<Clock, Dur2> const& rhs) noexcept;

        template <typename Clock, typename Dur1, typename Dur2>
        constexpr bool operator<=(time_point<Clock, Dur1> const& lhs, time_point<Clock, Dur2> const& rhs) noexcept;

        template <typename Clock, typename Dur1, typename Dur2>
        constexpr bool operator>(time_point<Clock, Dur1> const& lhs, time_point<Clock, Dur2> const& rhs) noexcept;

        template <typename Clock, typename Dur1, typename Dur2>
        constexpr bool operator>=(time_point<Clock, Dur1> const& lhs, time_point<Clock, Dur2> const& rhs) noexcept;

        //=== duration_typedefs ===//
        using nanoseconds = duration<long long, etl::nano>;
        using microseconds = duration<long long, etl::micro>;
        using milliseconds = duration<long long, etl::milli>;
        using seconds = duration<long long>;
        using minutes = duration<int, ratio<60>>;
        using hours = duration<int, ratio<3600>>;
        using days = duration<int, ratio<86400>>;
        using weeks = duration<int, ratio<604800>>;
        using years = duration<int, ratio<2629746>>;
        using months = duration<int, ratio<31556952>>;

        template <typename ToDur, typename Rep, typename Period, int _concept_requires_645 = 42, ::etl::enable_if_t<(_concept_requires_645 == 43) || (detail::is_duration<ToDur>::value), int> = 0>
        constexpr ToDur duration_cast(duration<Rep, Period> const& duration) noexcept('hidden');

        template <typename To, typename Rep, typename Period, int _concept_requires_661 = 42, ::etl::enable_if_t<(_concept_requires_661 == 43) || (detail::is_duration<To>::value), int> = 0>
        constexpr To floor(duration<Rep, Period> const& d) noexcept('hidden');

        template <typename Rep, typename Period, int _concept_requires_699 = 42, ::etl::enable_if_t<(_concept_requires_699 == 43) || (numeric_limits<Rep>::is_signed), int> = 0>
        constexpr duration<Rep, Period> abs(duration<Rep, Period> d) noexcept('hidden');

        inline constexpr bool treat_as_floating_point_v = treat_as_floating_point<Rep>::value;

        inline constexpr bool treat_as_floating_point_v = treat_as_floating_point<Rep>::value;

        inline constexpr bool treat_as_floating_point_v = treat_as_floating_point<Rep>::value;
    }
}

namespace etl
{
    template <typename Rep1, typename Period1, typename Rep2, typename Period2>
    struct common_type<chrono::duration<Rep1, Period1>, chrono::duration<Rep2, Period2>;

    template <typename Clock, typename Duration1, typename Duration2>
    struct common_type<chrono::time_point<Clock, Duration1>, chrono::time_point<Clock, Duration2>;

    inline namespace literals
    {
        inline namespace chrono_literals
        {
            constexpr etl::chrono::hours operator""_h(unsigned long long h);

            constexpr etl::chrono::duration<long double, ratio<3600, 1>> operator""_h(long double h);

            constexpr etl::chrono::minutes operator""_min(unsigned long long m);

            constexpr etl::chrono::duration<long double, etl::ratio<60, 1>> operator""_min(long double m);

            constexpr etl::chrono::seconds operator""_s(unsigned long long m);

            constexpr etl::chrono::duration<long double> operator""_s(long double m);

            constexpr etl::chrono::milliseconds operator""_ms(unsigned long long m);

            constexpr etl::chrono::duration<long double, etl::milli> operator""_ms(long double m);

            constexpr etl::chrono::microseconds operator""_us(unsigned long long m);

            constexpr etl::chrono::duration<long double, etl::micro> operator""_us(long double m);

            constexpr etl::chrono::nanoseconds operator""_ns(unsigned long long m);

            constexpr etl::chrono::duration<long double, etl::nano> operator""_ns(long double m);
        }
    }

    namespace chrono
    {
        using namespace ::etl::literals::chrono_literals;
    }
}
```

### Struct `etl::chrono::duration_values`

``` cpp
template <typename Rep>
struct duration_values
{
    static constexpr Rep zero();

    static constexpr Rep min();

    static constexpr Rep max();
};
```

The etl::chrono::duration\_values type defines three common durations.

The zero, min, and max methods in etl::chrono::duration forward their work to these methods. This type can be specialized if the representation Rep requires a specific implementation to return these duration objects.

### Function `etl::chrono::duration_values::zero`

``` cpp
static constexpr Rep zero();
```

Returns a zero-length representation.

-----

### Function `etl::chrono::duration_values::min`

``` cpp
static constexpr Rep min();
```

Returns the smallest possible representation.

-----

### Function `etl::chrono::duration_values::max`

``` cpp
static constexpr Rep max();
```

Returns the special duration value max.

-----

-----

### Struct `etl::chrono::treat_as_floating_point`

``` cpp
(1) template <typename Rep>
struct treat_as_floating_point
: etl::is_floating_point<Rep>
{
};

(2) template <typename Rep>inline constexpr bool treat_as_floating_point_v = treat_as_floating_point<Rep>::value;
```

The etl::chrono::treat\_as\_floating\_point trait helps determine if a duration can be converted to another duration with a different tick period.

Implicit conversions between two durations normally depends on the tick period of the durations. However, implicit conversions can happen regardless of tick period if etl::chrono::treat\_as\_floating\_point\<Rep\>::value == true. \\note etl::chrono::treat\_as\_floating\_point may be specialized for program-defined types.

-----

### Class `etl::chrono::duration`

``` cpp
template <typename Rep, typename Period = etl::ratio<1>>>
class duration
{
public:
    using rep = Rep;
    using period = typename Period::type;

    constexpr duration() noexcept = default;

    constexpr duration(const duration<Rep, Period>&) noexcept = default;

    template <typename Rep2, int _concept_requires_128 = 42, ::etl::enable_if_t<(_concept_requires_128 == 43) || ((is_convertible_v<Rep2, rep>) && (treat_as_floating_point_v<rep> || !treat_as_floating_point_v<Rep2>)), int> = 0>
    constexpr duration(Rep2 const& r) noexcept;

    template <typename Rep2, typename Period2, int _concept_requires_153 = 42, ::etl::enable_if_t<(_concept_requires_153 == 43) || ((treat_as_floating_point_v<rep>) || (ratio_divide<Period2, period>::den == 1 && !treat_as_floating_point_v<Rep2>)), int> = 0>
    constexpr duration(duration<Rep2, Period2> const& other) noexcept;

    duration<Rep, Period>& operator=(const duration<Rep, Period>& other) = default;

    constexpr rep count() const;

    static constexpr duration<Rep, Period> zero() noexcept;

    static constexpr duration<Rep, Period> min() noexcept;

    static constexpr duration<Rep, Period> max() noexcept;

    constexpr etl::common_type_t<duration<Rep, Period>> operator+() const;

    constexpr etl::common_type_t<duration<Rep, Period>> operator-() const;

    constexpr duration<Rep, Period>& operator++();

    constexpr duration<Rep, Period> operator++(int);

    constexpr duration<Rep, Period>& operator--();

    constexpr duration<Rep, Period> operator--(int);

    constexpr duration<Rep, Period>& operator+=(const duration<Rep, Period>& d) noexcept;

    constexpr duration<Rep, Period>& operator-=(const duration<Rep, Period>& d) noexcept;

    constexpr duration<Rep, Period>& operator*=(etl::chrono::duration::rep const& rhs) noexcept;

    constexpr duration<Rep, Period>& operator/=(etl::chrono::duration::rep const& rhs) noexcept;

    constexpr duration<Rep, Period>& operator%=(etl::chrono::duration::rep const& rhs) noexcept;

    constexpr duration<Rep, Period>& operator%=(const duration<Rep, Period>& rhs) noexcept;
};
```

Class template etl::chrono::duration represents a time interval.

It consists of a count of ticks of type Rep and a tick period, where the tick period is a compile-time rational constant representing the number of seconds from one tick to the next. The only data stored in a duration is a tick count of type Rep. If Rep is floating point, then the duration can represent fractions of ticks. Period is included as part of the duration’s type, and is only used when converting between different durations.

### Type alias `etl::chrono::duration::rep`

``` cpp
using rep = Rep;
```

Rep, an arithmetic type representing the number of ticks.

-----

### Type alias `etl::chrono::duration::period`

``` cpp
using period = typename Period::type;
```

A etl::ratio representing the tick period (i.e. the number of seconds per tick).

-----

### Constructor `etl::chrono::duration::duration`

``` cpp
constexpr duration() noexcept = default;
```

Constructs a new duration from one of several optional data sources. The default constructor is defaulted.

-----

### Constructor `etl::chrono::duration::duration`

``` cpp
constexpr duration(const duration<Rep, Period>&) noexcept = default;
```

Constructs a new duration from one of several optional data sources. The copy constructor is defaulted (makes a bitwise copy of the tick count).

-----

### Constructor `etl::chrono::duration::duration`

``` cpp
template <typename Rep2, int _concept_requires_128 = 42, ::etl::enable_if_t<(_concept_requires_128 == 43) || ((is_convertible_v<Rep2, rep>) && (treat_as_floating_point_v<rep> || !treat_as_floating_point_v<Rep2>)), int> = 0>
constexpr duration(Rep2 const& r) noexcept;
```

Constructs a duration with r ticks.

Note that this constructor only participates in overload resolution if const Rep2& (the argument type) is implicitly convertible to rep (the type of this duration’s ticks) and treat\_as\_floating\_point\<rep\>::value is true, or treat\_as\_floating\_point\<Rep2\>::value is false.

That is, a duration with an integer tick count cannot be constructed from a floating-point value, but a duration with a floating-point tick count can be constructed from an integer value

-----

### Constructor `etl::chrono::duration::duration`

``` cpp
template <typename Rep2, typename Period2, int _concept_requires_153 = 42, ::etl::enable_if_t<(_concept_requires_153 == 43) || ((treat_as_floating_point_v<rep>) || (ratio_divide<Period2, period>::den == 1 && !treat_as_floating_point_v<Rep2>)), int> = 0>
constexpr duration(duration<Rep2, Period2> const& other) noexcept;
```

Constructs a duration by converting d to an appropriate period and tick count, as if by duration\_cast\<duration\>(d).count().

In order to prevent truncation during conversion, this constructor only participates in overload resolution if computation of the conversion factor (by etl::ratio\_divide\<Period2, Period\>) does not overflow and:

treat\_as\_floating\_point\<rep\>::value == true

or both:

ratio\_divide\<Period2, period\>::den == 1, and treat\_as\_floating\_point\<Rep2\>::value == false

That is, either the duration uses floating-point ticks, or Period2 is exactly divisible by period

-----

### Function `etl::chrono::duration::operator=`

``` cpp
duration<Rep, Period>& operator=(const duration<Rep, Period>& other) = default;
```

Assigns the contents of one duration to another.

-----

### Function `etl::chrono::duration::count`

``` cpp
constexpr rep count() const;
```

Returns the number of ticks for this duration.

-----

### Function `etl::chrono::duration::zero`

``` cpp
static constexpr duration<Rep, Period> zero() noexcept;
```

Returns a zero-length duration.

-----

### Function `etl::chrono::duration::min`

``` cpp
static constexpr duration<Rep, Period> min() noexcept;
```

Returns a duration with the lowest possible value.

-----

### Function `etl::chrono::duration::max`

``` cpp
static constexpr duration<Rep, Period> max() noexcept;
```

Returns a duration with the largest possible value.

-----

### Function `etl::chrono::duration::operator+`

``` cpp
constexpr etl::common_type_t<duration<Rep, Period>> operator+() const;
```

Implements unary plus and unary minus for the durations.

-----

### Function `etl::chrono::duration::operator-`

``` cpp
constexpr etl::common_type_t<duration<Rep, Period>> operator-() const;
```

Implements unary plus and unary minus for the durations.

-----

### Function `etl::chrono::duration::operator++`

``` cpp
constexpr duration<Rep, Period>& operator++();
```

Increments or decrements the number of ticks for this duration. Equivalent to ++rep\_; return \*this;

-----

### Function `etl::chrono::duration::operator++`

``` cpp
constexpr duration<Rep, Period> operator++(int);
```

Increments or decrements the number of ticks for this duration. Equivalent to return duration(rep\_++)

-----

### Function `etl::chrono::duration::operator--`

``` cpp
constexpr duration<Rep, Period>& operator--();
```

Increments or decrements the number of ticks for this duration. Equivalent to –rep\_; return \*this;

-----

### Function `etl::chrono::duration::operator--`

``` cpp
constexpr duration<Rep, Period> operator--(int);
```

Increments or decrements the number of ticks for this duration. Equivalent to return duration(rep\_–);

-----

### Function `etl::chrono::duration::operator+=`

``` cpp
constexpr duration<Rep, Period>& operator+=(const duration<Rep, Period>& d) noexcept;
```

Performs compound assignments between two durations with the same period or between a duration and a tick count value.

-----

### Function `etl::chrono::duration::operator-=`

``` cpp
constexpr duration<Rep, Period>& operator-=(const duration<Rep, Period>& d) noexcept;
```

Performs compound assignments between two durations with the same period or between a duration and a tick count value.

-----

### Function `etl::chrono::duration::operator*=`

``` cpp
constexpr duration<Rep, Period>& operator*=(etl::chrono::duration::rep const& rhs) noexcept;
```

Performs compound assignments between two durations with the same period or between a duration and a tick count value.

-----

### Function `etl::chrono::duration::operator/=`

``` cpp
constexpr duration<Rep, Period>& operator/=(etl::chrono::duration::rep const& rhs) noexcept;
```

Performs compound assignments between two durations with the same period or between a duration and a tick count value.

-----

### Function `etl::chrono::duration::operator%=`

``` cpp
constexpr duration<Rep, Period>& operator%=(etl::chrono::duration::rep const& rhs) noexcept;
```

Performs compound assignments between two durations with the same period or between a duration and a tick count value.

-----

### Function `etl::chrono::duration::operator%=`

``` cpp
constexpr duration<Rep, Period>& operator%=(const duration<Rep, Period>& rhs) noexcept;
```

Performs compound assignments between two durations with the same period or between a duration and a tick count value.

-----

-----

### Class `etl::chrono::time_point`

``` cpp
template <typename Clock, typename Duration = typename Clock::duration>
class time_point
{
public:
    using clock = Clock;
    using duration = Duration;
    using rep = typename duration::rep;
    using period = typename duration::period;

    constexpr time_point() noexcept = default;

    constexpr time_point(etl::chrono::time_point::duration const& d) noexcept;

    template <typename Dur2, int _concept_requires_308 = 42, ::etl::enable_if_t<(_concept_requires_308 == 43) || (is_convertible_v<Dur2, duration>), int> = 0>
    constexpr time_point(time_point<etl::chrono::time_point::clock, Dur2> const& t);

    constexpr duration time_since_epoch() const noexcept;

    constexpr time_point<Clock, Duration>& operator+=(etl::chrono::time_point::duration const& d) noexcept;

    constexpr time_point<Clock, Duration>& operator-=(etl::chrono::time_point::duration const& d) noexcept;

    constexpr time_point<Clock, Duration>& operator++() noexcept;

    constexpr time_point<Clock, Duration> operator++(int) noexcept;

    constexpr time_point<Clock, Duration>& operator--() noexcept;

    constexpr time_point<Clock, Duration> operator--(int) noexcept;

    static constexpr time_point<Clock, Duration> min() noexcept;

    static constexpr time_point<Clock, Duration> max() noexcept;
};
```

Class template time\_point represents a point in time. It is implemented as if it stores a value of type Duration indicating the time interval from the start of the Clock’s epoch.

*Notes:* [cppreference.com/w/cpp/named\_req/Clock](https://en.cppreference.com/w/cpp/named_req/Clock)

#### Template parameters

  - `Clock` - Must meet the requirements for Clock

### Type alias `etl::chrono::time_point::clock`

``` cpp
using clock = Clock;
```

Clock, the clock on which this time point is measured.

-----

### Type alias `etl::chrono::time_point::duration`

``` cpp
using duration = Duration;
```

Duration, a duration type used to measure the time since epoch.

-----

### Type alias `etl::chrono::time_point::rep`

``` cpp
using rep = typename duration::rep;
```

Rep, an arithmetic type representing the number of ticks of the duration.

-----

### Type alias `etl::chrono::time_point::period`

``` cpp
using period = typename duration::period;
```

Period, a ratio type representing the tick period of the duration.

-----

### Constructor `etl::chrono::time_point::time_point`

``` cpp
constexpr time_point() noexcept = default;
```

Constructs a new time\_point from one of several optional data sources. Default constructor, creates a time\_point representing the Clock’s epoch (i.e., time\_since\_epoch() is zero).

-----

### Constructor `etl::chrono::time_point::time_point`

``` cpp
constexpr time_point(etl::chrono::time_point::duration const& d) noexcept;
```

Constructs a new time\_point from one of several optional data sources. Constructs a time\_point at Clock’s epoch plus d.

-----

### Constructor `etl::chrono::time_point::time_point`

``` cpp
template <typename Dur2, int _concept_requires_308 = 42, ::etl::enable_if_t<(_concept_requires_308 == 43) || (is_convertible_v<Dur2, duration>), int> = 0>
constexpr time_point(time_point<etl::chrono::time_point::clock, Dur2> const& t);
```

Constructs a new time\_point from one of several optional data sources. Constructs a time\_point by converting t to duration. This constructor only participates in overload resolution if Duration2 is implicitly convertible to duration.

-----

### Function `etl::chrono::time_point::time_since_epoch`

``` cpp
constexpr duration time_since_epoch() const noexcept;
```

Returns a duration representing the amount of time between \*this and the clock’s epoch.

-----

### Function `etl::chrono::time_point::operator+=`

``` cpp
constexpr time_point<Clock, Duration>& operator+=(etl::chrono::time_point::duration const& d) noexcept;
```

Modifies the time point by the given duration. Applies the offset d to pt. Effectively, d is added to the internally stored duration d\_ as d\_ += d.

-----

### Function `etl::chrono::time_point::operator-=`

``` cpp
constexpr time_point<Clock, Duration>& operator-=(etl::chrono::time_point::duration const& d) noexcept;
```

Modifies the time point by the given duration. Applies the offset d to pt in negative direction. Effectively, d is subtracted from internally stored duration d\_ as d\_ -= d.

-----

### Function `etl::chrono::time_point::operator++`

``` cpp
constexpr time_point<Clock, Duration>& operator++() noexcept;
```

Modifies the point in time \*this represents by one tick of the duration.

-----

### Function `etl::chrono::time_point::operator++`

``` cpp
constexpr time_point<Clock, Duration> operator++(int) noexcept;
```

Modifies the point in time \*this represents by one tick of the duration.

-----

### Function `etl::chrono::time_point::operator--`

``` cpp
constexpr time_point<Clock, Duration>& operator--() noexcept;
```

Modifies the point in time \*this represents by one tick of the duration.

-----

### Function `etl::chrono::time_point::operator--`

``` cpp
constexpr time_point<Clock, Duration> operator--(int) noexcept;
```

Modifies the point in time \*this represents by one tick of the duration.

-----

### Function `etl::chrono::time_point::min`

``` cpp
static constexpr time_point<Clock, Duration> min() noexcept;
```

Returns a time\_point with the smallest possible duration,

-----

### Function `etl::chrono::time_point::max`

``` cpp
static constexpr time_point<Clock, Duration> max() noexcept;
```

Returns a time\_point with the largest possible duration,

-----

-----

### Function `etl::chrono::operator==`

``` cpp
template <typename Rep1, typename Period1, typename Rep2, typename Period2>
constexpr bool operator==(duration<Rep1, Period1> const& lhs, duration<Rep2, Period2> const& rhs);
```

Compares two durations. Checks if lhs and rhs are equal, i.e. the number of ticks for the type common to both durations are equal.

-----

### Function `etl::chrono::operator!=`

``` cpp
template <typename Rep1, typename Period1, typename Rep2, typename Period2>
constexpr bool operator!=(duration<Rep1, Period1> const& lhs, duration<Rep2, Period2> const& rhs);
```

Compares two durations. Checks if lhs and rhs are equal, i.e. the number of ticks for the type common to both durations are equal.

-----

### Function `etl::chrono::operator<`

``` cpp
template <typename Rep1, typename Period1, typename Rep2, typename Period2>
constexpr bool operator<(duration<Rep1, Period1> const& lhs, duration<Rep2, Period2> const& rhs);
```

Compares two durations. Compares lhs to rhs, i.e. compares the number of ticks for the type common to both durations.

-----

### Function `etl::chrono::operator<=`

``` cpp
template <typename Rep1, typename Period1, typename Rep2, typename Period2>
constexpr bool operator<=(duration<Rep1, Period1> const& lhs, duration<Rep2, Period2> const& rhs);
```

Compares two durations. Compares lhs to rhs, i.e. compares the number of ticks for the type common to both durations.

-----

### Function `etl::chrono::operator>`

``` cpp
template <typename Rep1, typename Period1, typename Rep2, typename Period2>
constexpr bool operator>(duration<Rep1, Period1> const& lhs, duration<Rep2, Period2> const& rhs);
```

Compares two durations. Compares lhs to rhs, i.e. compares the number of ticks for the type common to both durations.

-----

### Function `etl::chrono::operator>=`

``` cpp
template <typename Rep1, typename Period1, typename Rep2, typename Period2>
constexpr bool operator>=(duration<Rep1, Period1> const& lhs, duration<Rep2, Period2> const& rhs);
```

Compares two durations. Compares lhs to rhs, i.e. compares the number of ticks for the type common to both durations.

-----

### Function `etl::chrono::operator==`

``` cpp
template <typename Clock, typename Dur1, typename Dur2>
constexpr bool operator==(time_point<Clock, Dur1> const& lhs, time_point<Clock, Dur2> const& rhs) noexcept;
```

Compares two time points. The comparison is done by comparing the results time\_since\_epoch() for the time points.

-----

### Function `etl::chrono::operator!=`

``` cpp
template <typename Clock, typename Dur1, typename Dur2>
constexpr bool operator!=(time_point<Clock, Dur1> const& lhs, time_point<Clock, Dur2> const& rhs) noexcept;
```

Compares two time points. The comparison is done by comparing the results time\_since\_epoch() for the time points.

-----

### Function `etl::chrono::operator<`

``` cpp
template <typename Clock, typename Dur1, typename Dur2>
constexpr bool operator<(time_point<Clock, Dur1> const& lhs, time_point<Clock, Dur2> const& rhs) noexcept;
```

Compares two time points. The comparison is done by comparing the results time\_since\_epoch() for the time points.

-----

### Function `etl::chrono::operator<=`

``` cpp
template <typename Clock, typename Dur1, typename Dur2>
constexpr bool operator<=(time_point<Clock, Dur1> const& lhs, time_point<Clock, Dur2> const& rhs) noexcept;
```

Compares two time points. The comparison is done by comparing the results time\_since\_epoch() for the time points.

-----

### Function `etl::chrono::operator>`

``` cpp
template <typename Clock, typename Dur1, typename Dur2>
constexpr bool operator>(time_point<Clock, Dur1> const& lhs, time_point<Clock, Dur2> const& rhs) noexcept;
```

Compares two time points. The comparison is done by comparing the results time\_since\_epoch() for the time points.

-----

### Function `etl::chrono::operator>=`

``` cpp
template <typename Clock, typename Dur1, typename Dur2>
constexpr bool operator>=(time_point<Clock, Dur1> const& lhs, time_point<Clock, Dur2> const& rhs) noexcept;
```

Compares two time points. The comparison is done by comparing the results time\_since\_epoch() for the time points.

-----

### Type alias `etl::chrono::nanoseconds`

``` cpp
(1) using nanoseconds = duration<long long, etl::nano>;
(2) using microseconds = duration<long long, etl::micro>;
(3) using milliseconds = duration<long long, etl::milli>;
(4) using seconds = duration<long long>;
(5) using minutes = duration<int, ratio<60>>;
(6) using hours = duration<int, ratio<3600>>;
(7) using days = duration<int, ratio<86400>>;
(8) using weeks = duration<int, ratio<604800>>;
(9) using years = duration<int, ratio<2629746>>;
(10) using months = duration<int, ratio<31556952>>;
```

Signed integer type of at least 64 bits.

-----

### Function `etl::chrono::duration_cast`

``` cpp
template <typename ToDur, typename Rep, typename Period, int _concept_requires_645 = 42, ::etl::enable_if_t<(_concept_requires_645 == 43) || (detail::is_duration<ToDur>::value), int> = 0>
constexpr ToDur duration_cast(duration<Rep, Period> const& duration) noexcept('hidden');
```

Converts a duration to a duration of different type ToDur.

-----

### Function `etl::chrono::floor`

``` cpp
template <typename To, typename Rep, typename Period, int _concept_requires_661 = 42, ::etl::enable_if_t<(_concept_requires_661 == 43) || (detail::is_duration<To>::value), int> = 0>
constexpr To floor(duration<Rep, Period> const& d) noexcept('hidden');
```

Returns the greatest duration t representable in ToDuration that is less or equal to d. The function does not participate in the overload resolution unless ToDuration is an instance of etl::chrono::duration.

-----

### Function `etl::chrono::abs`

``` cpp
template <typename Rep, typename Period, int _concept_requires_699 = 42, ::etl::enable_if_t<(_concept_requires_699 == 43) || (numeric_limits<Rep>::is_signed), int> = 0>
constexpr duration<Rep, Period> abs(duration<Rep, Period> d) noexcept('hidden');
```

Returns the absolute value of the duration d. Specifically, if d \>= d.zero(), return d, otherwise return -d. The function does not participate in the overload resolution unless etl::numeric\_limits\<Rep\>::is\_signed is true.

-----

### Struct `etl::common_type`

``` cpp
template <typename Rep1, typename Period1, typename Rep2, typename Period2>
struct common_type<chrono::duration<Rep1, Period1>, chrono::duration<Rep2, Period2>
{
};
```

Exposes the type named type, which is the common type of two etl::chrono::durations, whose period is the greatest common divisor of Period1 and Period2.

The period of the resulting duration can be computed by forming a ratio of the greatest common divisor of Period1::num and Period2::num and the least common multiple of Period1::den and Period2::den.

-----

### Struct `etl::common_type`

``` cpp
template <typename Clock, typename Duration1, typename Duration2>
struct common_type<chrono::time_point<Clock, Duration1>, chrono::time_point<Clock, Duration2>
{
};
```

Exposes the type named type, which is the common type of two chrono::time\_points.

-----

### Function `etl::literals::chrono_literals::operator""_h`

``` cpp
constexpr etl::chrono::hours operator""_h(unsigned long long h);
```

Forms a etl::chrono::duration literal representing hours. Integer literal, returns exactly etl::chrono::hours(hrs).

-----

### Function `etl::literals::chrono_literals::operator""_h`

``` cpp
constexpr etl::chrono::duration<long double, ratio<3600, 1>> operator""_h(long double h);
```

Forms a etl::chrono::duration literal representing hours. Floating-point literal, returns a floating-point duration equivalent to etl::chrono::hours.

-----

### Function `etl::literals::chrono_literals::operator""_min`

``` cpp
constexpr etl::chrono::minutes operator""_min(unsigned long long m);
```

Forms a etl::chrono::duration literal representing minutes. Integer literal, returns exactly etl::chrono::minutes(mins).

-----

### Function `etl::literals::chrono_literals::operator""_min`

``` cpp
constexpr etl::chrono::duration<long double, etl::ratio<60, 1>> operator""_min(long double m);
```

Forms a etl::chrono::duration literal representing minutes. Floating-point literal, returns a floating-point duration equivalent to etl::chrono::minutes.

-----

### Function `etl::literals::chrono_literals::operator""_s`

``` cpp
constexpr etl::chrono::seconds operator""_s(unsigned long long m);
```

Forms a etl::chrono::duration literal representing seconds. Integer literal, returns exactly etl::chrono::seconds(mins).

-----

### Function `etl::literals::chrono_literals::operator""_s`

``` cpp
constexpr etl::chrono::duration<long double> operator""_s(long double m);
```

Forms a etl::chrono::duration literal representing seconds. Floating-point literal, returns a floating-point duration equivalent to etl::chrono::seconds.

-----

### Function `etl::literals::chrono_literals::operator""_ms`

``` cpp
constexpr etl::chrono::milliseconds operator""_ms(unsigned long long m);
```

Forms a etl::chrono::duration literal representing milliseconds. Integer literal, returns exactly etl::chrono::milliseconds(mins).

-----

### Function `etl::literals::chrono_literals::operator""_ms`

``` cpp
constexpr etl::chrono::duration<long double, etl::milli> operator""_ms(long double m);
```

Forms a etl::chrono::duration literal representing milliseconds. Floating-point literal, returns a floating-point duration equivalent to etl::chrono::milliseconds.

-----

### Function `etl::literals::chrono_literals::operator""_us`

``` cpp
constexpr etl::chrono::microseconds operator""_us(unsigned long long m);
```

Forms a etl::chrono::duration literal representing microseconds. Integer literal, returns exactly etl::chrono::microseconds(mins).

-----

### Function `etl::literals::chrono_literals::operator""_us`

``` cpp
constexpr etl::chrono::duration<long double, etl::micro> operator""_us(long double m);
```

Forms a etl::chrono::duration literal representing microseconds. Floating-point literal, returns a floating-point duration equivalent to etl::chrono::microseconds.

-----

### Function `etl::literals::chrono_literals::operator""_ns`

``` cpp
constexpr etl::chrono::nanoseconds operator""_ns(unsigned long long m);
```

Forms a etl::chrono::duration literal representing nanoseconds. Integer literal, returns exactly etl::chrono::nanoseconds(mins).

-----

### Function `etl::literals::chrono_literals::operator""_ns`

``` cpp
constexpr etl::chrono::duration<long double, etl::nano> operator""_ns(long double m);
```

Forms a etl::chrono::duration literal representing nanoseconds. Floating-point literal, returns a floating-point duration equivalent to etl::chrono::nanoseconds.

-----
