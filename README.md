# Spend less time coding using test-driven development

[NLSEB PhD and Postdoc Day](http://nlseb.nl/nlseb2021-phd-postdoc-meeting/) workshop: spend less time coding using Test-Driven Development

 * When: Tuesday April 20 2021 11.00–12.30 in Workshop session III
 * Where:  https://gather.town/i/ALM0dO9o

# Content

On average, 80% of the time we spend debugging.
Test-driven development is a technique used by
professional software developers to reduce this time,
by writing tests before the actual code.
Although this initially feels 'inside-out', it results
in correct code quicker.

In this hands-on workshop, we'll write tests for simple functions
to practice this way of developing.

It is assumed you can read basic R code and that you
have an R environment (e.g. R Studio) installed.

## Schedule



## Coarse schedule

 * Why important?
  * Use new things quicker
  * Work from big to small, focus on usage over details
  * Good architecture
  * Less bugs
  * Less worry
  * Select better packages, rOpenSci
 * Demo: is_one [YouTube](https://youtu.be/IPGfW4lrxOc) [download (.ogv)](http://richelbilderbeek.nl/r_tdd_is_one.ogv)
 * Practice: is_even [YouTube](https://youtu.be/4NBsCis584U) [download (.ogv)](http://richelbilderbeek.nl/r_tdd_is_even.ogv)
 * Practice: is_odd [YouTube](https://youtu.be/Lah3fm3lUiA) [download (.ogv)](http://richelbilderbeek.nl/r_tdd_is_odd.ogv)
 * Practice: fizz_buzz [YouTube](https://youtu.be/e_ZIfLMgPVc) [download (.ogv)](http://richelbilderbeek.nl/r_tdd_fizz_buzz.ogv)

 * Practice: to_roman
 * Practice: is_prime
 * Practice: roman_to_int





## Detailed schedule


### First test

```
expect_silent(is_prime(2))
```


```
expect_true(is_prime(2))
```


```
expect_false(is_prime(1))
```


```
expect_false(is_prime(0))
```

Write the real function:

```
expect_true(is_prime(3))
```

Write the error handling:

```
expect_error(
  is_prime("nonsense"),
  "input must be a number"
)
```

```
expect_error(
  is_prime(c(1, 2)),
  "input must be one number"
)
```

```
expect_error(
  is_prime(c(1, 2)),
  "input must be one number"
)

expect_silent(
  are_prime(c(1, 2)),
  "input must be one number"
)
```


### `is_one`

 * Video: [YouTube](https://youtu.be/IPGfW4lrxOc) [download (.ogv)](http://richelbilderbeek.nl/r_tdd_is_one.ogv)

```
library(testthat)

is_one <- function(x) {
  if (!is.numeric(x)) {
    stop("'x' must be a number")
  }
  if (length(x) != 1) {
    stop("'x' must be one number")
  }
  x == 1
}

expect_silent(is_one(1))
expect_true(is_one(1))
expect_error(is_one("nonsense"), "'x' must be a number")
expect_error(is_one(c(1, 2)), "'x' must be one number")
```

### `is_even`

 * Video: [YouTube](https://youtu.be/4NBsCis584U) [download (.ogv)](http://richelbilderbeek.nl/r_tdd_is_even.ogv)

```
library(testthat)

is_even <- function(x) {
  if (!is.numeric(x)) {
    stop("'x' must be a number")
  }
  if (length(x) != 1) {
    stop("'x' must be one number")
  }
  if (is.infinite(x)) {
    stop("'x' must be a non-infinite number")
  }
  x %% 2 == 0
}

expect_silent(is_even(2))
expect_true(is_even(2))
expect_false(is_even(3))
expect_error(is_even("nonsense"), "'x' must be a number")
expect_error(is_even(c(1, 2)), "'x' must be one number")
expect_error(is_even(Inf), "'x' must be a non-infinite number")
expect_error(is_even(-Inf), "'x' must be a non-infinite number")
```






### `is_odd`

 * Video: [YouTube](https://youtu.be/Lah3fm3lUiA) [download (.ogv)](http://richelbilderbeek.nl/r_tdd_is_odd.ogv)

```
library(testthat)

is_odd <- function(x) {
  if (!is.numeric(x)) {
    stop("'x' must be a number")
  }
  if (length(x) != 1) {
    stop("'x' must be one number")
  }
  if (is.infinite(x)) {
    stop("'x' must be a finite number")
  }
  x %% 2 == 1
}

expect_silent(is_odd(3))
expect_true(is_odd(3))
expect_false(is_odd(2))
expect_error(is_odd("nonsense"), "'x' must be a number")
expect_error(is_odd(c(1, 2)), "'x' must be one number")
expect_error(is_odd(Inf), "'x' must be a finite number")
```


