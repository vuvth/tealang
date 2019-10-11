# Teal Language

**ANTLR4**-based high level language for TEAL.
The goal is to hide stack VM of TEAM by high-level Go/Python/C-like syntax sugar.

## Language Features

Supports constants, variables, assignments, binary and unary operations, conditions and function calls.

```
const a = 1
const b = "string"
const c = "\x32\x33\x34";

let result = if b == c { 1 } else { 2 }
if result == 0 {
    error
} else {
}

return 1
```

## Build from sources

### Prerequisites

1. Set up **ANTLR4** as explained in [the documentation](https://www.antlr.org/)
2. Set `CLASSPATH`
    ```
    export CLASSPATH=.:$(pwd)/gen/java:$CLASSPATH
    ```
3. Install runtime for Go
    ```
    go get github.com/antlr/antlr4/runtime/Go/antlr
    ```

### Build and run Java AST visualizer

```
antlr4 Tealang.g4 -o gen/java && javac gen/java/Tealang*.java
cat examples/fee-reimburse.tl | grun Tealang prog -gui
```

### Build Go

```
antlr4 -Dlanguage=Go -visitor -o gen/go Tealang.g4
```