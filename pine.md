# Pine Langauge Specification
## Version 0.1.0

---

## Overview

Pine is a simple Dynamically-Typed Scripting Language. It takes elements from Go, C & JavaScript.

```pine
// Hello World Program.
println("Hello, World!");
```


## Grammar

```c
<program> := <Statement>*
<Statement> :=
      <Block>
    | <WhileStmt>
    | <IfStmt>
    | <ExprStmt>
    | <LetStmt>
    | <ReturnStmt>
    | <FuncDef>

<Block> := '{' (<Statement>)* '}'
<WhileStmt> := 'while' <Expr> <Block>
<IfStmt>    := 'if' <Expr> <Block> ('else' <Block>)?
<ExprStmt>  := <Expr>';'
<ReturnStmt> := 'return' <Expr>? ';'
<FuncDef> := 'fn' <Identifier> '(' (Identifier (',' <Identifier>)*)? ')' <Block>

<Expr> := <Comparison>
<Comparison>    := <Factor> (('==' | '>=' | '<=' | '!=') <Comparison>)?
<Factor> := <Term> (('*' | '/') <Factor>)?
<Term> := <Unary> (('+' | '-') <Term>)?
<Unary> := (('!' | '-') <Unary> ) | <Atom>

<Atom> := 
      <Integer>
    | <String>
    | <Boolean>
    | <Decimal>
    | <Identifier>
    | <Group>
    | <Call>

<Integer> := <Digit>+
<Decimal> := <Integer> ('.' <Integer>)?
<Digit> := [0-9]

<String> := '"' (.*) '"'
<Boolean> := 'true' | 'false'

<Identifier> := [A-Za-z]+[A-Za-z0-9_]*
<Group> := '(' <Expr> ')'

<Call> := <Identifier> '(' (<Expr> (',' <Expr>)*)? ')'

```
