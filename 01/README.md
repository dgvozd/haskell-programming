The **lambda** in lambda calculus is the greek letter 𝜆 used to introduce, or abstract, arguments for binding in an expression.

**Referential transparency** means that the same function, given the same values to evaluate, will always return the same result in pure functional programming, as they do
in math.

The **lambda calculus** has three basic components, or lambda terms: 
- expressions
- variables
- abstractions

An _abstraction_ is a function. 
-- It is an _anonymous function_ which has no name.
- Abstractions consist of two parts, a head and a body.
-- The head of the function is a 𝜆 (lambda) followed by a variable name.
-- The body of the function is another expression.
- Abstractions are applied to an argument.
--- An _argument_ is an input value.

```
𝜆𝑥.𝑥
```

- The variable named in the head is the _parameter_ and _binds_ all instances of that same variable in the body of the function.
- Applying this function to an argument each `𝑥` in the body of the function will have the value of that argument.

```
λ x . x
^___^       
            the extent of the head of the lambda.

λ x . x
  ^_______    
            the single parameter of the function. This
            binds any variables with the same name
            in the body of the function.

λ x . x
      ^___    
            body, the expression the lambda returns
            when applied. This is a bound variable.
```

The dot (`.`) separates the parameters of the lambda from the function body.

The reason we call it an **abstraction** is that it is a generalization, or abstraction,
from a concrete instance of a problem, and it abstracts through the introduction of names.
- The names stand for concrete values. 
-- By using named variables we allow for the possibility of applying the general function to different values.
- When we apply the abstraction to arguments, we replace the names with values, making it concrete.

##### Alpha Equivalence
-- Meaning all of these functions are the same thing:

```
𝜆𝑥.𝑥 
𝜆𝑑.𝑑 
𝜆𝑧.𝑧
```

**beta reduction**
Substituting the input expression for all bound variables within the body and eliminating the head of the abstraction

**free variables**
```
𝜆𝑥.𝑥𝑦 
```
- When we apply this function to an argument, nothing can be done with the 𝑦. It remains irreducible.

That whole abstraction can be applied to an argument, `𝑧`, like this: `(𝜆𝑥.𝑥𝑦)𝑧`.

1. `(𝜆𝑥.𝑥𝑦)𝑧`
  -- We apply the lambda to the argument 𝑧.
2. `(𝜆[𝑥 ∶= 𝑧].𝑥𝑦)`
  -- Since `𝑥` is the bound variable, all instances of `𝑥` in the body of the function will be replaced with `𝑧`. The head will be eliminated, and we replace any `𝑥` in the body with a 𝑧.
3. `𝑧𝑦`
  -- The head has been applied away, and there are no more heads or bound variables. Since we know nothing about `𝑧` or `𝑦`, we can reduce this no further.

**multiple Arguments (currying)**
```
𝜆𝑥𝑦.𝑥𝑦
```
is shorthand for

```
𝜆𝑥.(𝜆𝑦.𝑥𝑦)
```

```
1. (𝜆𝑥𝑦𝑧.𝑥𝑧(𝑦𝑧))(𝜆𝑚𝑛.𝑚)(𝜆𝑝.𝑝)
2. (𝜆𝑥.𝜆𝑦.𝜆𝑧.𝑥𝑧(𝑦𝑧))(𝜆𝑚.𝜆𝑛.𝑚)(𝜆𝑝.𝑝)
3. (𝜆𝑦.𝜆𝑧(𝜆𝑚.𝜆𝑛.𝑚)𝑧(𝑦𝑧))(𝜆𝑝.𝑝)
4. 𝜆𝑧(𝜆𝑚.𝜆𝑛.𝑚)(𝑧)((𝜆𝑝.𝑝)𝑧)
5. 𝜆𝑧(𝜆𝑛.𝑧)((𝜆𝑝.𝑝)𝑧)
6. 𝜆𝑧.𝑧

1. x => y => z => x(z)(y(z))(m => n => m)(p)

2. (x => y => z => x(z)(y(z))(m => n => m)(p => p)

3. x = (m => n => m)
   (y => z => (m => n => m)(z)(y(z))(p => p)

4. y = (p => p)
   z => (m => n => m)(z)((p => p)z)

5. m = z
   z => (n => z)((p => p)z)

6. n = ((p => p)z)
   z => z
```

**beta normal form** - can't beta reduce further

**combinator** - lambda with no free variables

can't inject any new values or random data
**divergence** - reduction never terminates

some additional information here: https://habr.com/ru/post/215807/
