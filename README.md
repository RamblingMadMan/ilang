# Infinity Lang
> Functional Computer Speak

The Infinity language is designed to have the low runtime cost of a static low-level language like C++ but also the fast development rate of a dynamic high-level language like Python or Javascript.

## Tenets

- Everything is abstract
- Everything is immutable
- Everything is first-class

### Everything is abstract

In ilang, everything you write is an abstract representation of an underlying concept. Numerics, strings, functions and logical statements; these (and all other objects) are represented by abstract types that are filled in later by the compiler. This fundamental way of thinking allows the compiler to choose the most appropriate/efficient algorithm to handle any situation.

As an example; any numeric literal typed in source has the abstract type `Number`. when the literal is used for the first time it's true (underlying) type will be emplaced by the compiler and the correct function/variable will be instantiated. This underlying type could be any of `Real`, `Nat`, `Int` or some other suitable numeric type.

### Everything is immutable

As an important tenant of functional programming, all data in ilang is immutable. This may feel foreign coming from an imperative language such as C, Python, Java, etc. but is a very useful limitation that gives us 'referential transparency'. This special property of functional languages paired with deterministic side effects gives us full determinism: each call of the same function with the same parameters and equal state will return an identical result.

### Everything is first-class

This feature is important for dynamic programming and thinking about problems in a more abstract sense. Types, numerics, strings, functions and any type not listed can be passed through parameters and all have some form of literal syntax.

## Language Features

- ML-like syntax
- Hindley–Milner style type system
- Effect system integrated in type system

## Components
Here are links to repositories containing the individual components of the Infinity language system.

[Infinity Lang Base](https://github.com/RamblingMadMan/ilang-base)  
[Infinity Lang REPL](https://github.com/RamblingMadMan/ilang-repl)  

## (Not Necessarily Working) Eamples

### Hello World
```javascript
let IO = import "IO"

main() = IO.outln "Hello, World!"
```

### Simple BinOp Calculator
```javascript
let IO = import "IO"
let Fmt = import "Fmt"
let Parse = import "Parse"

calcInner('+', a, b) = a + b
calcInner('-', a, b) = a - b
calcInner('*', a, b) = a * b
calcInner('/', a, b) = a / b
calcInner('^', a, b) = a ^ b

calc(op, a, b) = calcInner op (Parse.real a) (Parse.real b)

main() =
    IO.out "Enter an op and 2 numbers (separated by spaces): "
    let input = IO.inln ()
    let ins = split input " "
    
    if (length ins) != 3 then
        IO.outln "Invalid input"
        main ()
    else
        let res = calc ins[0] ins[1] ins[2]
        IO.outln (Fmt.fmt "{} + {} = {}" ins[0] ins[1] res)
```
