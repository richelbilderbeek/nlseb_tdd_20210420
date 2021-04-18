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

 * Why important?
 * Demo: is_one [YouTube](https://youtu.be/IPGfW4lrxOc) [download (.ogv)](http://richelbilderbeek.nl/r_tdd_is_one.ogv)
 * Practice: is_even [YouTube](https://youtu.be/4NBsCis584U) [download (.ogv)](http://richelbilderbeek.nl/r_tdd_is_even.ogv)
 * Practice: is_odd [YouTube](https://youtu.be/Lah3fm3lUiA) [download (.ogv)](http://richelbilderbeek.nl/r_tdd_is_odd.ogv)
 * Practice: fizz_buzz [YouTube](https://youtu.be/e_ZIfLMgPVc) [download (.ogv)](http://richelbilderbeek.nl/r_tdd_fizz_buzz.ogv)
 * Practice: is_prime [YouTube](https://youtu.be/JtM_YSrbiek) [download (.ogv)](http://richelbilderbeek.nl/r_tdd_is_prime.ogv)
 * Conclusion

## Solutions

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

### `fizz_buzz`

 * Video: [YouTube](https://youtu.be/e_ZIfLMgPVc) [download (.ogv)](http://richelbilderbeek.nl/r_tdd_fizz_buzz.ogv)

```
# From https://en.wikipedia.org/wiki/Fizz_buzz:
#
# Players generally sit in a circle.
# The player designated to go first says the number "1",
# and the players then count upwards in turn.
# However, any number divisible by three is replaced by the word fizz
# and any number divisible by five by the word buzz.
# Numbers divisible by 15 become fizz buzz.
# A player who hesitates or makes a mistake is eliminated from the game.
#
#For example, a typical round of fizz buzz would start as follows:
#
# 1, 2, Fizz, 4, Buzz, Fizz, 7, 8, Fizz, Buzz, 11, Fizz, 13, 14, Fizz Buzz,
# 16, 17, Fizz, 19, Buzz, Fizz, 22, 23, Fizz, Buzz, 26, Fizz, 28, 29, Fizz Buzz, 31, 32, Fizz, 34, Buzz, Fizz, ..

library(testthat)

fizz_buzz <- function(x) {
  if (!is.numeric(x)) { stop("'x' must be a number") }
  if (length(x) != 1) { stop("'x' must be one number") }
  if (is.infinite(x)) { stop("'x' must be a finite number") }
  if (x < 1) { stop("'x' must be at least 1") }
  if (x %% 3 == 0 && x %% 5 == 0) { return("Fizz Buzz") }
  if (x %% 3 == 0) { return("Fizz") }
  if (x %% 5 == 0) { return("Buzz") }
  as.character(x)
}

expect_silent(fizz_buzz(1))
expect_equal(fizz_buzz(1), "1")
expect_equal(fizz_buzz(3), "Fizz")
expect_equal(fizz_buzz(5), "Buzz")
expect_equal(fizz_buzz(15), "Fizz Buzz")
expect_error(fizz_buzz("nonsense"), "'x' must be a number")
expect_error(fizz_buzz(c(3, 5)), "'x' must be one number")
expect_error(fizz_buzz(0), "'x' must be at least 1")
expect_error(fizz_buzz(Inf), "'x' must be a finite number")
```

### `is_prime`

 * Video: [YouTube](https://youtu.be/JtM_YSrbiek) [download (.ogv)](http://richelbilderbeek.nl/r_tdd_is_prime.ogv)

```
library(testthat)

is_prime <- function(x) {
  if (!is.numeric(x)) stop("'x' must be a number")
  if (length(x) != 1) stop("'x' must be one number")
  if (is.infinite(x)) stop("'x' must be a finite number")
  if (x < 2) return(FALSE)
  if (x == 2) return(TRUE)
  divisors <- seq(2, x - 1)
  for (divisor in divisors) {
    if (x %% divisor == 0) return(FALSE)
  }
  TRUE
}

expect_silent(is_prime(7))
expect_false(is_prime(1))
expect_true(is_prime(2))
expect_false(is_prime(4))
expect_error(is_prime("nonsense"), "'x' must be a number")
expect_error(is_prime(c(1, 2)), "'x' must be one number")
expect_error(is_prime(Inf), "'x' must be a finite number")
```


