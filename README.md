# Monkey

This repository contains the Monkey interpreter built while following [Writing an Interpreter in Go](https://interpreterbook.com/) by Thorsten Ball. It is a learning project written in Go, exploring how a programming language works from tokenizing source code to evaluating expressions. The Monkey language and the implementation approach come from the book.

## Features

- Lexer for turning source code into tokens
- Pratt parser and abstract syntax tree (AST)
- Tree-walking evaluator with lexical scope and closures
- Integers, booleans, strings, arrays, and hash maps
- Variable bindings, arithmetic and comparison operators, conditionals, and return statements
- First-class functions and function calls
- Built-in functions: `len`, `first`, `last`, `rest`, `push`, and `puts`
- Interactive read-eval-print loop (REPL) with persistent bindings between inputs
- Tests for the lexer, parser, AST, evaluator, and object model

This repository implements an interpreter, not a bytecode compiler or virtual machine.

## Getting Started

Requires Go 1.25 or newer, as declared in `go.mod`. The project has no external module dependencies.

```sh
git clone https://github.com/MajdTaweel/monkey.git
cd monkey
go run .
```

Enter one complete expression or statement per line. Function definitions and other compound expressions must fit on a single input line. Press `Ctrl+D` to exit.

### Example

```text
>> let add = fn(x, y) { x + y; };
>> add(2, 3);
5
>> let newAdder = fn(x) { fn(y) { x + y; }; };
>> let addTwo = newAdder(2);
>> addTwo(5);
7
>> let numbers = [1, 2, 3];
>> len(push(numbers, 4));
4
>> {"answer": 42}["answer"];
42
```

## Testing

Run all tests:

```sh
go test ./...
```

## Project Layout

The code is organized using the stages described in the book:

```text
main.go       # starts the interactive interpreter
token/        # token types and keywords
lexer/        # source-code tokenization
ast/          # abstract syntax tree nodes
parser/       # Pratt parser for expressions and statements
object/       # runtime values and scoped environments
evaluator/    # AST evaluation and built-in functions
repl/         # interactive read-eval-print loop
```
