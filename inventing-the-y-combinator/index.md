---
title: Inventing the Y-Combinator
publishedAt: 2020-04-28
editedAt: 2020-12-08
---

In this post we will derive the [Y-combinator](https://en.wikipedia.org/wiki/Fixed-point_combinator#Y_combinator) from first principles.

In other words, we will invent a reusable way to use recursion in [lambda calculus](https://en.wikipedia.org/wiki/Lambda_calculus).

To ground our understanding, we will reference the Python implementation of the Fibonacci series as our main example:

```python
# fibonacci
def f(n):
    if n == 0:
        return 1
    if n == 1:
        return 1
    return f(n - 1) + f(n - 2)
```

**Step 1:**

Start with a function $f$ whose implementation is self-referencing.

If $f$'s body references itself once, $f$ will have a form like:

$$
f_1 = ...f_1...
$$

For two self-references:

$$
f_2 = ...f_2...f_2...
$$

Or three:

$$
f_3 = ...f_3...f_3...f_3...
$$

etc..

Here we use $...$ to denote any lambda calculus expression.

For our example, we have two self-references (`f(n - 1)` and `f(n - 2)`), but our analysis will hold for any number of self-references.

$$
f = ...f...f...
$$

**Step 2:**

Instead of hardcoding $f$ in the body, let's factor out $f$:

$$
f = (\lambda r ...r...r...)f = Mf
$$

where we define $M := \lambda r ...r...r...$

Logically, $...$s encode all the non-recursive logic.

For our Python example, the non-recursive logic look like:

```python
# non-recursive
def M(r, n):
    if n == 0:
        return 1
    if n == 1:
        return 1
    return r(n - 1) + r(n - 2)
```

Notice that this function is no longer recursive; there are no calls to `M` in its body.

We've made progress: $M$ does not depend on $f$!

But we still depend on $f$ for it's own definition:

$$
f = (\lambda r ...r...r...)f = Mf
$$

Can we construct an input for $M$ that does not depend on $f$?

**Step 3:**

Let's try using $M$ in place of $f$:

$$
f \stackrel{?}{=} (\lambda r ...r...r...)(\lambda r ...r...r...) = MM
$$

This may seem like a shot in the dark. And it is!

We don't expect this to work, but exploring this construction will give us insight to what the answer should be.

If we assume $f = M$ then $f = MM$ (because $f = Mf$).
How far is this from the truth?

Looking at our Python examples, we know that `f` is not the same function as `M`, but there is a lot of overlap!

So $f = Mf \ne MM$, but could we tweak $M$ to make this work?

**Step 4:**

What if $M$ didn't take $f$ as a variable, but expected itself as a variable?!

In other words, let's work backward from what we want: define $M'$ such that $f = M'M'$ .

$$
f = M'M'
$$

Then, to create $f$, we can just apply that variable in $M'$ to itself!

$$
f = (\lambda r (rr)) M'
$$

Can we solve for $M'$ and use it to define $f$? Yes!

$$
f = (\lambda r ...(rr)...(rr)...)(\lambda r ...(rr)...(rr)...) = M'M'
$$

**Step 5:**

Cleaning up, we can express $M'$ in terms of $M$:

$$
M' = \lambda r ...(rr)...(rr)...
$$

$$
M = \lambda r ...r...r...
$$

$$
\therefore M' = \lambda x.M(xx)
$$

$$
\therefore f = (\lambda x.M(xx))(\lambda x.M(xx))
$$

**Step 6:**

Can we generalize this approach for _any_ recursive function? Yes!

Starting with the expression:

$$
f = (\lambda x.M(xx))(\lambda x.M(xx))
$$

we can factor out $M$ as a parameter to define the Y-combinator:

$$
\Upsilon = \lambda m.(\lambda x.m(xx))(\lambda x.m(xx))
$$

For any recursive function $f$, we can extract its non-recursive logic $M$ like we did in our Python example.
Then we simply pass $M$ into the Y-combinator to define $f$.

$$
f = \Upsilon M = (\lambda m.(\lambda x.m(xx))(\lambda x.m(xx)))M
$$

Philosophically, the variable $m$ encodes all interesting parts of $f$'s implementation.
The rest of this expression just plumbs through the recursion.
