# You Don't Know JS: Scope & Closures

## Table of Contents

* Foreword
* Preface
* Chapter 1: What is Scope?
  * Compiler Theory
  * Understanding Scope
  * Nested Scope
  * Errors
* Chapter 2: Lexical Scope
  * Lex-time
  * Cheating Lexical
* Chapter 3: Function vs. Block Scope
  * Scope From Functions
  * Hiding In Plain Scope
  * Functions As Scopes
  * Blocks As Scopes
* Chapter 4: Hoisting
  * Chicken Or The Egg?
  * The Compiler Strikes Again
  * Functions First
* Chapter 5: Scope Closures
  * Enlightenment
  * Nitty Gritty
  * Now I Can See
  * Loops + Closure
  * Modules
* Appendix A: Dynamic Scope
* Appendix B: Polyfilling Block Scope
* Appendix C: Lexical-this
* Appendix D: Acknowledgments

## Compiler Theory

### Steps

  1. Tokenizing/Lexing: breaking up a string of characters into meaningful chunks;
  2. Parsing: taking a stream of tokens e turning into a "AST" (Abstract Syntax Tree);
  3. Code-Generation: the process of taking an AST and turning it into executable code;

## Understanding Scope

### The Cast

  1. Engine: responsible for start-to-finish compilation and execution of our JavaScript program;
  2. Compiler: handles all the dirty work of parsing and code-generation;
  3. Scope: collects and maintains a look-up list of all the declared identifiers, and enforces a strict set of rules as to how these are accessible to currently executing code;

### Back & Forth

`var a = 2;`

  1. Compiler declares a variable (if not previously declared in the current scope);
  2. Engine looks up the variable in Scope and assigns to it, if found;

### Compiler Speak

  1. LHS - "Left-hand Side", *left-hand side of an assignment*;
     1. `a = 2;`
  2. RHS - "Right-hand Side" *go get the value of...*;
     1. `console.log( a );`

### Engine/Scope Conversation

```js

function foo(a) {
	console.log( a ); // 2
}

foo( 2 );

```

1. `foo()` - RHS
2. `a` - LHS
3. `a = 2`
4. `console` - RHS
5. `a` - RHS

## Nestes Scope

If a variable cannot be found in the immediate scope, Engine consults the next outer containing scope, continuing until found or until the outermost (aka, global) scope has been reached.

## Errors

* Strict mode
  * LHS - `ReferenceError`;
  * RHS - `TypeError`;
* Lazy mode
  * LHS - automatic/implicit global variable creation;
  * RHS - `ReferenceError`;

