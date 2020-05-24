---
layout: post
title: "Short Variable Names in Go"
date: "2020-05-24 06:00:00 +0000"
tags: [ "Golang" ]
permalink: "blog/short-variable-names-in-go"
---
When I first started learning Go, I heard a lot of people talk about the idiomatic way of doing things. "Sure, that way works, but *this* is the way we do it in Go." I'm OK with that - a strict convention can give every piece of code a strong sense of familiarity - and Go has quite a few of these. One such convention is to use [short variable names](https://github.com/golang/go/wiki/CodeReviewComments#variable-names).

> Variable names in Go should be short rather than long. This is especially true for local variables with limited scope. Prefer `c` to `lineCount`. Prefer `i` to `sliceIndex`.

<!--more-->

This makes perfect sense. However, the latter part of the comment goes on to make an important distinction.

> The basic rule: the further from its declaration that a name is used, the more descriptive the name must be. For a method receiver, one or two letters is sufficient. Common variables such as loop indices and readers can be a single letter (i, r). More unusual things and global variables need more descriptive names.

So variable names should be short, but only where it makes sense. This is why you'll often see `w` and `r` used in a HTTP handler function. The context is clear, so there is little ambiguity as to what those variables represent. Anything longer would be unnecessary.

```go
http.HandleFunc("/bar", func(w http.ResponseWriter, r *http.Request) {
    fmt.Fprintf(w, "Hello, %q", html.EscapeString(r.URL.Path))
})
```

To this extent, when used properly, the short variable names actually help make the code more readable. If you know you're looking at a HTTP handler, you'll instantly know that `r` is a `Request`. However, if the function starts to get bigger, or there are more variables in the mix, things can change pretty quickly and there is a risk short names could become less clear. This may also be an argument for keeping functions and the number of variables as short and limited as possible, but both of these issues are closely related. Will this code make sense to someone else reading it? What's the cognitive load? After all, good code isn't just about engineering, it's also about communication.
