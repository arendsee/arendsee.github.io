---
layout: single
comments: true
author_profile: true
author: Zebulun Arendsee
title:  "Transparent composition"
categories: [R, programming]
tags: [R, functional programming]
---

A powerful strategy in functional programming is building complex functions
from simple ones using functional composition. A basic composition function can
be implemented in R as below



{% highlight r %}
compose <- function(...){
    fs <- list(...)
    function(...){
        x <- fs[[1]](...)
        for(f in fs[-1]){
            x <- f(x)
        }
        x
    }
}
foo <- compose(runif, mean, abs, log)
set.seed(42)
foo(100, min=-5, max=5)
{% endhighlight %}



{% highlight text %}
## [1] -1.407365
{% endhighlight %}

This code is correct, but the returned function is not informative.


{% highlight r %}
foo
{% endhighlight %}



{% highlight text %}
## function(...){
##         x <- fs[[1]](...)
##         for(f in fs[-1]){
##             x <- f(x)
##         }
##         x
##     }
## <environment: 0x170ee08>
{% endhighlight %}

It would be nice if the composed function printed like this:


{% highlight text %}
## function(n, min=0, max=1){
##     log(abs(mean(runif(n, min, max))))
## }
{% endhighlight %}

These compositions are first-class citizens, in that they can be used,
modified, and viewed exactly like any other function. This is especially
important if compositions are returned from inside a package. Transparent
compositions are also open to metaprograming. For example, if we want to reset
the default value for `max` to 2, we can call `formals(foo)$max = 2`. This
would be impossible for the opaque compositions.

To build a transparent composition, there are three levels we need to consider:

1. formal parameters -- `n, min=0, max=1`
2. body -- `log(abs(mean(runif())))`
3. arguments passed to runif -- `n, min, max`

The first step is pretty easy


{% highlight r %}
compose_a <- function(...){
  # get the innermost function
  inner <- list(...)[[1]]
     
  # start with the innermost function
  fun <- inner

  # remove its body
  body(fun) <- NULL

  fun
}
compose_a(runif, mean, abs, log)
{% endhighlight %}



{% highlight text %}
## function (n, min = 0, max = 1) 
## NULL
## <environment: namespace:stats>
{% endhighlight %}

We can build the body of the function piece by piece, like this


{% highlight r %}
foo <- runif
body_str <- '{log(abs(mean(runif(n, min, max))))}'
body(foo) <- parse(text=body_str)
{% endhighlight %}

But of course, we have to build `body_str` from the input arguments.

We can get the character names of the given arguments


{% highlight r %}
compose_b <- function(...){
    sapply(match.call(expand.dots=TRUE), deparse)[-1]
}
{% endhighlight %}

and the names of the paramers `runif` takes 


{% highlight r %}
compose_c <- function(...){
    inner <- list(...)[[1]]
    methods::formalArgs(inner)
}
{% endhighlight %}

Now for a bit of string manipulation


{% highlight r %}
compose_d <- function(...){
  inner <- list(...)[[1]]

  fun_names  <- sapply(match.call(expand.dots=TRUE)[-1], deparse)
  inner_args <- paste0(methods::formalArgs(inner), collapse=', ')

  # function for recursive wrapping of calls
  compose_ <- function(f, g){ sprintf("%s(%s)", g, f) }
  # functional body as an expression
  body_expr <- Reduce(compose_, fun_names, init=inner_args)
}
compose_d(runif, mean, abs, log)
{% endhighlight %}

Putting all this together we get the function


{% highlight r %}
compose2 <- function(...){
  inner <- list(...)[[1]]

  fun_names  <- sapply(match.call(expand.dots=TRUE)[-1], deparse)
  inner_args <- paste0(methods::formalArgs(inner), collapse=', ')
  compose_   <- function(f, g){ sprintf("%s(%s)", g, f) }
  body_expr <- Reduce(compose_, fun_names, init=inner_args)
  body_expr <- parse(text=body_expr)

  fun              <- inner
  body(fun)        <- body_expr
  environment(fun) <- parent.frame()

  fun
}
foo <- compose2(runif, mean, abs, log)
set.seed(42)
foo(100, min=-5, max=5)
{% endhighlight %}



{% highlight text %}
## [1] -1.407365
{% endhighlight %}

Now `foo` prints cleanly


{% highlight r %}
foo
{% endhighlight %}



{% highlight text %}
## function (n, min = 0, max = 1) 
## log(abs(mean(runif(n, min, max))))
{% endhighlight %}

You can view the default values with `formals(foo)`. You can alter the
defaults, e.g. `formals(foo)$min <- 0`.
