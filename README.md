# Infinity Lang
> Functional Computer Speak

The Infinity language is designed to have the low runtime cost of a static low-level language like C++ but also the fast development rate of a dynamic high-level language like Python or Javascript.

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
