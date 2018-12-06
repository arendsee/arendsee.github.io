---
layout: post
title: Classes in R, Java, and Haskell
---

The purpose of this post is to clarify the logic behind R classes, specifically
for the Java programmer.

A Java afficionado migrating to R may be dismayed at dismal state of R's class
system (I'll only talk about S3 here). In Java, classes are used to encapsulate
a set of data and functions. A class is an API to a set of data. It hides
internal details, exposing only what is needed.

Coming form this background, reactions of horror from Java programmers is not
surprising. R S3 classes do not store private data or private functions. They
own nothing. Indeed, they are nothing at all but a name attached to a thing.
Any thing. So how are these even classes?

An R S3 class is simply a label appended to the class vector of an object. You
can have massively multiple inheritance. You can cast any thing into any class
without error.

You can errorlessly create nonsensical classes:

```
x <- c(1,2,3)
class(x) <- 'letters'

y <- c('a','b','c')
class(y) <- 'letters'
```

R is a corrupt functional language.
