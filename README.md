## Instructions to install

```bash
opam pin add scylla git@github.com:anmolsahoo25/ocaml-scylla
opam pin add mrdt git@github.com:anmolsahoo25/ocaml-mrdt-v2
```

Minimal usage instructions -

On one node - 
```ocaml;
module Set = Mrdt.Mset.Make (struct type t = int [@@deriving irmin] let compare
= compare end)

let conn = Scylla.connect ~ip:"127.0.0.1" ~port:9042 |> Result.get_ok in
let set1 = Set.init 0 "setA" [conn]
```

On another node - 
```ocaml;
module Set = Mrdt.Mset.Make (struct type t = int [@@deriving irmin] let compare
= compare end)

let conn = Scylla.connect ~ip:"127.0.0.1" ~port:9042 |> Result.get_ok in
let set1 = Set.init 1 "setA" [conn]
```
