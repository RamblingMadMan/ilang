# Infinity Lang
> Functional Computer Speak

## Components
Here are links to repositories containing the individual components of the Infinity language system.

[Infinity Lang Type System](https://github.com/RamblingMadMan/ilang-types)  
[Infinity Lang Lexer](https://github.com/RamblingMadMan/ilang-lexer)  
[Infinity Lang Parser](https://github.com/RamblingMadMan/ilang-parser)  
[Infinity Lang Evaluator](https://github.com/RamblingMadMan/ilang-eval)  
[Infinity Lang REPL](https://github.com/RamblingMadMan/ilang-repl)  

## (Not Necessarily Working) Eamples

### Hello World
```javascript
let IO = import "IO"
let Fmt = import "Fmt"

main() = IO.outln "Hello, World!"
```

### Dumb Adder
```javascript
let Parse = import "Parse"

calc(a, b) = Parse.real(a) + Parse.real(b)

main() =
    IO.out "Enter 2 numbers separated by a space: "
    let input = IO.inln ()
    let nums = split input " "
    
    if (length num) != 2 then
        IO.outln "Invalid input"
        main ()
    else
        let res = calc nums[0] nums[1]
        IO.outln (Fmt.fmt "{} + {} = {}" nums[0] nums[1] res)
```
