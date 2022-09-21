# verifies result types and length

    Code
      map2_int(1, 1, ~"x")
    Condition
      Error in `map2_int()`:
      ! Computation failed in index 1
      Caused by error:
      ! Can't coerce from a character to a integer
    Code
      map2_int(1, 1, ~ 1:2)
    Condition
      Error in `map2_int()`:
      ! Computation failed in index 1
      Caused by error:
      ! Result must be length 1, not 2
    Code
      map2_vec(1, 1, ~1, .ptype = character())
    Condition
      Error:
      ! Can't convert <double> to <character>.

# requires vector inputs

    Code
      map2(environment(), "a", identity)
    Condition
      Error in `withCallingHandlers()`:
      ! `.x` must be a vector, not an environment.
    Code
      map2("a", environment(), "a", identity)
    Condition
      Error in `withCallingHandlers()`:
      ! `.y` must be a vector, not an environment.

# recycles inputs

    Code
      map2(1:2, 1:3, `+`)
    Condition
      Error in `withCallingHandlers()`:
      ! Mapped vectors must have consistent lengths:
      * `.x` has length 2
      * `.y` has length 3
    Code
      map2(1:2, integer(), `+`)
    Condition
      Error in `withCallingHandlers()`:
      ! Mapped vectors must have consistent lengths:
      * `.x` has length 2
      * `.y` has length 0
