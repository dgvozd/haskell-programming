What is **Prelude**? Prelude is a library of standard functions. Opening GHCi or Stack GHCi automatically loads those functions 
so they can be used without needing to do anything special.

**ghci commands**:

`:load <file.hs>` -- load this module, changes prompt from Prelude> to maybe `*Main>`

`:module` -- "quit" the loaded module, back to `Prelude>`

`:module *Main` -- jump back to the `*Main` module

`:reload` -- reload current module (e.g., re-read file)

`:type` and `:kind` look fun :)

`:info` -- type information for function, including infix, associativity, precedence


**Expression** vs **Declaration**:
- expressions evaluate to results
- declarations allow us to name expressions

We say that expressions are in **normal form** when there are no more evaluation steps that can be taken (when they've reached an *irreducible* form)
*Reducible* expressions are also called **redexes**.

**Expressions are the most basic unit of a Haskell program, and functions are a specific type of expression.**
As in the lambda calculus, all functions in Haskell take one argument and return one result.
The way to think of this is that, in Haskell, when it seems we are passing multiple arguments to a function, we are actually applying a series of nested functions, each to one argument. This is called **currying**.

**Define a function in a source file:**
*triple x = x * 3*

**Values** are expressions, but cannot be reduced further. Values are a terminal point of reduction.

Haskell doesn’t evaluate everything to canonical or normal form by default. Instead, it only evaluates to weak head normal form (WHNF) by default.

```
(\f -> (1, 2 + f)) 2
```
reduces to the following in WHNF:
```
(1, 2 + 2)
```
This representation is an approximation, but the key point here is that 2 + 2 is not evaluated to 4 until the last possible moment.
