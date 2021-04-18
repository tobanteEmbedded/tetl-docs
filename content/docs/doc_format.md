---
title: "format.hpp"
---

# Header file `format.hpp`

``` cpp
#include "etl/version.hpp"
#include "etl/vector.hpp"

namespace etl
{
    template <typename It>
    using diff_t = typename ::etl::iterator_traits< ::etl::remove_cvref_t<It>>::difference_type;

    template <typename OutputIt, typename ... Args>
    OutputIt format_to(OutputIt out, etl::string_view fmt, const Args &... args);

    template <typename Out>
    struct format_to_n_result;

    template <typename OutputIter, typename ... Args>
    format_to_n_result<OutputIter> format_to_n(OutputIter out, diff_t<OutputIter> n, ::etl::string_view fmt, const Args &... args);
}
```

### Function `etl::format_to` \[Strings\]

``` cpp
template <typename OutputIt, typename ... Args>
OutputIt format_to(OutputIt out, etl::string_view fmt, const Args &... args);
```

Format args according to the format string fmt, and write the result to the output iterator out.

*Notes:* [cppreference.com/w/cpp/utility/format/format\_to](https://en.cppreference.com/w/cpp/utility/format/format_to)

-----

### Struct `etl::format_to_n_result` \[Strings\]

``` cpp
template <typename Out>
struct format_to_n_result
{
};
```

etl::format\_to\_n\_result has no base classes, or members other than out, size and implicitly declared special member functions.

*Notes:* [cppreference.com/w/cpp/utility/format/format\_to\_n](https://en.cppreference.com/w/cpp/utility/format/format_to_n)

-----

### Function `etl::format_to_n` \[Strings\]

``` cpp
template <typename OutputIter, typename ... Args>
format_to_n_result<OutputIter> format_to_n(OutputIter out, diff_t<OutputIter> n, ::etl::string_view fmt, const Args &... args);
```

Format args according to the format string fmt, and write the result to the output iterator out. At most n characters are written.

*Notes:* [cppreference.com/w/cpp/utility/format/format\_to\_n](https://en.cppreference.com/w/cpp/utility/format/format_to_n)

-----
