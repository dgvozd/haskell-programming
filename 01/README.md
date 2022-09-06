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

**beta reduction** - apply the function

(\x . x)(2) = 2
function applications are left associative
