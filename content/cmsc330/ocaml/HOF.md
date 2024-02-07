---
Title: Higher Order Functions
tags:
- cmsc330
- wip
---

## random notes

tuples the size if fixed
tuples are , delimited


```ocaml
match (a,b) with
(x::xs, y:;ys) -> x + y
```


# Higher Order Functions

Anonymous functions: functions with no name

Functions : takes in input and returns output
1 input 1 ouput 
issue:
* 0 input
* \> 1 input
* 0 output
* \> 1 output

```ocaml
let f x = x + 1
```


```ocaml
int x = 4

func f = (....)

fun x -> x + 1 (*anonymous function*)

let f = fun x -> x + 1 (*fucntion, but looks a little bit gross*)

(*Syntatic sugar*)
let f x = x + 1 (*let f = fun x -> x + 1*)
```

```ocaml
(fun x -> x + 1) 5 (* will return 6*)
```

```ocaml
let x = print_string "a"
```

unit() something to be returned but not meaningful
```ocaml
print_string "hello"
(* unit = () *)
```
only have one output in a function but the output can be multiple elements (a tuple)


fun is the keyword to say its a function but there is no keywords that tell you the name of the function (anaonymous function)

haskell *curry*
```ocaml
fun x -> (fun y -> y + 1)
(* 'a -> (int -> int) *) 
```

```ocaml
let f x y = x + y
f 4 (* int - > int *)
let g = f 4 (* int -> int *)
g 6 (*int = 10 *)

fun x -> (fun y -> x + y) 4 5 (* int =  9*)

let f x y = x + y (* int -> int -> int*)
g 5 (* int = 9 *)
```

```ocaml
let g = f 5
(*same as *)
(fun x -> fun y -> x + y) 5 -> (fun y -> 5 + y) 
```

let apply f x = (f(x))

```ocaml
let addgenerator x = fun y -> x + y (* addgenerator returns a function *)
let add5 = addgenerator 5
let add3 = addgenerator 3

add5 3 = 8
add3 4 = 7

add5 3 
(*is equivilent to*)
(addgenerator 5) 3 = 8 
```

## Map

```ocaml
let rec map f lst = 
    match lst with
    | [] -> []
    | x :: xs -> (f x)::(map f xs)
```
> ( 'a -> 'b ) -> 'a list -> 'b list


execution
```ocaml
map (fun x -> x + 1) [1;2;3;4]
(*int list = [2;3;4;5] *)
```

```ocaml
let is_even_list = map (fun x -> if x mod 2 = 0 then true else false) lst 
is_even_list [1;2;3;4;5;6]
(*bool list = [false; true; false; true; false; true*)
```

## Fold

Consider
```ocaml
let rec concat lst = 
    match lst with
    | [] -> ""
    | h :: t -> h^(concat t)

let rec sum lst = 
    match lst with
    | [] -> 0
    | h :: t -> h+(sum t)

let rec product lst =
    match lst with
    | [] -> 1
    | h :: t -> h*(product)

(* hmmm *)

let rec fold f accumulator lst=
    match lst with
    | [] -> accumulator
    | h::t -> (f h (fold f accumulator t))

fold (fun x y -> x + y) 0 [1;2;3;4;5]
fold (fun x y -> x^y) "" ["a";"b";"c"]
fold (fun x y -> x * y) 1 [1;2;3;4;5]
```


```ocaml
let rec fold f accumulator lst=
    match lst with
    | [] -> accumulator
    | h::t -> (f h (fold f accumulator t))
```

```ocaml
let rec fold_left f a l = match l with
[] -> a
| x :: xs -> (fold_left f (f a x) xs)
```