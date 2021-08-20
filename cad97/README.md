# whyc
(pronounced whick)

A jam programming language with "first class comments."

What does that mean? It means that **comments are your only conditional primitive**.
There is no `if`, no `for`; only `comment(line)` and `uncomment(line)`.

## Quick exampless

### Hello, World!

```
println("Hello, World!");
```

### Greetings, User!

```
user = input();

comment(5 + (user != "CAD"));

println("Hello, " + user = "!");
println("Hello, creator!");
```

### Is Even

```
value = input();

comment(5 + (value % 2));

println(value + " is odd");
println(value + " is even");
```

### Add

```
lhs = parse(input());
rhs = parse(input());
println(lhs + " + " rhs + " = " + (lhs + rhs));
```

### Is Prime

```
value = parse(input());
divisor = 1;

{
    divisor = divisor + 1;
    comment(14 - (value == divisor));
    comment(8 + (value % divisor == 0));
    // this is line 8
}

println(
    value + " is " +
    "not " +
    // this is line 14
    "prime!"
);
```

## How to

### Build instructions

0. Install latest [Rust stable](https://www.rust-lang.org/learn/get-started) (1.54.0)
0. `cargo build`

### Test instructions

0. Install latest [Rust stable](https://www.rust-lang.org/learn/get-started) (1.54.0)
0. `cargo test`

### Run instructions

0. Install latest [Rust stable](https://www.rust-lang.org/learn/get-started) (1.54.0)
0. `cargo run [-v] input.why`


## What?

### stdlib

- `input()` - read a line from stdin. returns a string.
- `parse(string)` - parse a string into an integer.
- `comment(line)` - comment line `line` of source code.
- `uncomment(line)` - uncomment line `line` of source code.
                      noop if line is not commented.
- `println(string)` - print a string to stdout.

### syntax

- `// text text text` - comment (until end of line)
- `"text"` - literal string
- `binding = value;` - assign `value` to name `binding`
- `lhs + rhs` - add `lhs` and `rhs` together
  - if both `lhs` and `rhs` are integers, numeric addition
  - if `lhs` or `rhs` are strings, coerce both to string and concat
- `lhs - rhs` - subtract `rhs` from `lhs`
  - if both `lhs` and `rhs` are integers, numeric subtraction
  - if `lhs` or `rhs` are strings, coerce both to string and remove suffix
- `lhs % rhs` - compute `lhs % rhs`
  - if both `lhs` and `rhs` are integers, numeric (programmer's) modulo
  - if `lhs` or `rhs` are strings... you'll figure it out
- `{` - line marker used by `}`
- `}` - jump execution back to the matching `{`

<!-- Author note: I _might_ have to add `[` and `]` to jump forward,
     to make writing an interesting program more possible... -->

There is no UB. The implementation is perfect, and will not change after the jam is finished.
Rely on any and all quirks of the interpreter to manage to write a useful program. Please.

## Why?

Why not? Also, #langjam20201

I could've given you a `goto`, but `{}` is more _structured_
(and also, `goto` would've been easier to use).
