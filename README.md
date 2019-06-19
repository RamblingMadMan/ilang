# Infinity Lang
> Functional Computer Speak

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

### Dumb Adder
```javascript
let IO = import "IO"
let Fmt = import "Fmt"
let Parse = import "Parse"

calc(a, b) = (Parse.real a) + (Parse.real b)

main() =
    IO.out "Enter 2 numbers separated by a space: "
    let input = IO.inln ()
    let nums = split input " "
    
    if (length nums) != 2 then
        IO.outln "Invalid input"
        main ()
    else
        let res = calc nums[0] nums[1]
        IO.outln (Fmt.fmt "{} + {} = {}" nums[0] nums[1] res)
```
