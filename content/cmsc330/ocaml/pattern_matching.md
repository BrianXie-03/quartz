---
title: Pattern Matching
tags:
- cmsc330
---





------------------------------------



```ocaml
let func_name arg arg2 ... = body
```

mutliple parameters
```ocaml
let add x y = x + y

(* to call the function *)
add 3 4
```

if u add a float and a int then it truncats down as it returns an int

float -> int -> int



---- more meaningful functins ----

rec = keyword for recursion
without rec but calling like an recursion you get unbound value 

```ocaml
let rec fact x =
    if x = 1 then 1 else x * fact (x-1)
```

List data structure

must be homogenous (same type)

```ocaml
int lst = [1;2;3;] (*int list*)
bool list = [true;false] (*bool list*)
```

```ocaml
let is_empty lst =
    lst = []
```

'a list -> bool

" a tic a list to bool "

when comparing they must be the same type  < > <= >+

```ocaml
let cmp x y = x > y
```
'a -> 'a -> bool

```ocaml
let cmp x y = x > false
```
bool -> 'a -> bool

```ocaml
let cmp x y = 3
```
'a -> 'b -> int


cons operator (::) adds to the beginning 

```ocaml
0::[1;2;3]

[0;1;2;3]
```

defining variables

```ocaml
let x = 3
x + 4
```

```ocaml
let lst = [1;2;3]
0::lst (* [0;1;2;3] *)

let x = 4
x + 5 (* 9 *)
```

ocaml has garbage collection (since immutable auto clean up)

```ocaml
0::1::2::[] -> [1;2;3]
```

```ocaml
let add_0 lst = 0::lst

int list -> int list (* we know the later is int lsit and since its
homogenous the input is also int lsit *)
```

To make it more generic
```ocaml
let add_gen lst val = val::lst
```
'a -> 'a list -> 'a list

## Pattern Matching

otherwise known as a fancy switch statemnet

```ocaml
(match value:t with
| (value1):pattern -> (return_value1):t
| (value2):pattern -> (return_value2):t
| (value3):pattern -> (return_value3):t):t
```

a pattern can be a single struture, values, or wildcards

_ is a wildcard

```ocaml
let match_x x =
match x with
| 1 -> "a"
| 2 -> "b"
| 3 -> "c"
| _ -> "d"
```

int -> string = <fun>

```ocaml
let match_lst lst =
    match lst with
    | [] -> 0
    | [x] -> 1
    | head :: tail -> 2;;
```

> head:: tail is where head is currently on top and tail is the remaining (think linked list)


```ocaml
let match_lst lst =
    match lst with
    | [] -> -1
    | head :: tail ->head
```
int list -> int


```ocaml
let match_lst =
    match lst with
    | [] -> -1
    | h1::h2::tail -> h1+h2
```
> issue if list size 1

```ocaml
let rec add_list =
    match lst with
    | [] -> 0
    | x::xs -> x + add_list xs
```


## Tuple

(1,2,3)

int * int * int = (1,2,3)

(1, true, 3)
int * bool * int

(1, true)
int * bool

if putting tuple in list then all types in tuple must be the same
( int * int ) list

cannot have ( bool * int ) list


[(1,2);(3,4,5)]
size of the tuple also matters
(int * int) is not the same as (int * int * int)

```ocaml
let match_tup x =
    match x with
    (a,b,c) -> (b,c,a)
```
'a * 'b * 'c -> 'b * 'c * 'a


```ocaml
let match_tup x =
    match x with
    (a,b,c) -> (b+1,c,a&&false)
```
bool * int * 'c -> int * 'c * bool