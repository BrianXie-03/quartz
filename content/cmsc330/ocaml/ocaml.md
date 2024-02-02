---
title: Syntax and Semantics
tags:
- cmsc330
---

# Introduction

Things to first note about ocaml
* All files are named .ml
* Commenets are done using (* *)
* naming conventions are done using snake_case
* Almost everything in OCaml are expressions, but not all expressions are values
* Uses static and latent [[typing]]
* Variables are all immutable
* Expressions evaluate to values (v)
* All values are expressions, but not vice versa
* Expressions have types (t)


Similar to C, OCaml is a compiled language, meaning that it needs to go through multiple steps in order to run a OCaml program.

```bash
ocamlc name.ml #used to run OCaml programs

# Note that it'll create:
#prog_name.cmi
#prog_name.cmo
#a.out
```

## Functions and Expressions

While we say that almost everything is an expression, the binding of expressions, **let binding** is not an expresion. Futhermore, **let expression** can also be covered as there are alternative uses to let.

**let bindings:** is not an expression and just binds an expression to a variable
```ocaml
(* letBinding.ml *)
let x  = 3 + 4
(* let variable_name = e*)
```

**let expressions:** setting a local variable to be used in another expression
```ocaml
(* letExpression.ml *)
let x = 3 + 4 in x + 1
(* let variable_name = e1 in e2 *)
```
**in:** known to be more of a punctuation, allowws for parser languages to tell where one expression stops and another starts

```ocaml
(* scoping.ml *)
 let x = 3 in let y = 4 in x + y (* 7 *)
 let x = 3 in let x = 4 in x (* 4 *) (* overshadow *)
 let x = 3 in let z = 4 + x in let x = 1 in x + z (* 8 *)
 (* implicit parenthesis *)
 let x = 3 in (let z = 4 + x in (let x = 1 in x + z))

 let x = if true then false else true in
 let y = 3 + 4 in
 let z = if true then 2 else 6 in
 if x then y else z
```

## if Operator

The if operater is used in order to allow for two different results given a bool value. Provided is the bare syntax for using the if operator

```ocaml
(if e1:bool then e2:t else e3:t):t

if true then 3 else 4
```

> **Note:** the resulting output must be both evaluate to the same type

We can then apply the if statements to let bindings and let expressions.
```ocaml
let x = if true then false else true

let y = 3 + 4 - 10 in
if true then y else y + 10
```

Another application of if statements is that it can be nested/used for other tasks such as arithmatics or for a more complex use. 

```ocaml
1 + (if (if true then false else true) then 3 else 4))

(* return 5:int *)
```

## Functions as Expressions

A way to look into ocaml is that variables are functions that have no parameters that return a value. By following the initialization with variables.

```ocaml
(* functions.ml *)
let area l w = l * w
let area l w = l * w in area 2 3
```
Similar to let bindings, a function defintion by itself is not an expression, only when you use the keyword in, would you have it become an expression. Since we now know that functions are expressions, and that functions can take in expressions as inputs, we are able to have functions that take in other functions.

```ocaml
let area l w = l * w (* int -> int -> int *)
let apply f x y = f x y (* ('a -> 'b -> 'c) -> 'a -> 'b -> 'c *)
apply area 2 3 
```

## Type Inference

Type Inferencing is used to allow programming languages to determine the type of variable or value. The types of variables in Ocaml are determined by the operations or syntax of an expression (inferred).
> &&, || can only be used for bools  
> +, -, *, / can only be used on ints  
> +., -., *., /. alternatively can be used for floats

```ocaml
(* operations.ml *)
2 + 3 (* int and int *)
1.3 +. 4.3 (* float and float *)
"hello" ^ " world" (* string and string *)
true || false (* bool and bool *)
int_of_char ’a’ (* char input, int output *)
2 + 3.0 (* error *)
3 ^ 4 (* error *)
```

While the previously stated operators only work on certain types, there are some that are able to be used on different types.
> <, >, >=, <=, =, works for any inputs as long as they are the same type

```ocaml
(* compare.ml *)
2 > 4 (* false *)
"hello" <= "world" (* true *)
true = false (* false *)
```
Notice that = is used for both binding and comparison in ocaml. The neat thing about ocaml is that it knows that anything after the first = is the expression.

```ocaml
let compare x y = x > y in compare
```
> Initially, we dont know what types x and y are, but since the function knows that it is returning a bool then it would go from 'a -> 'a -> bool to bool -> bool -> bool.

```ocaml
let f x y = 3
```
This function will have type 'a -> 'b -> int. Since the type of x and y do not have to be the same to return the int, it gives it seperate symbols.

```ocaml
let apply f x y = f x y in apply (* (’a -> ’b -> ’c) -> ’a -> ’b -> ’c *)
```