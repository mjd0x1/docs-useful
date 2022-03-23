# Julia 

## REPL

## Benchmark Tools

## Structs

```julia
    mutable struct SomeData
        id::Int
        name::String
        value::Float64
    end

    SomeData.([1,1,3],["s","l","f"],[2,3,4])
    sort(b,by = (x) -> x.name)

```

## Dictionaries

```julia
    d = Dict("a"  => 1, "b" => 2)
    get(d,"c",0)
    d["r"]= 10
    keys(d)
    values(d)
    Dict(["a","b","c"] .=> ones(3))
```

## Arrays/Functions

```julia
     maximum([1,2,3])
     minimum([1,2,3])
     sort([3,2,3,4,5,6])
     "sdasdasd" * "asdas" * string(3424)
     string(0,1,2,3,4)
     parse(Int,"323243")
     parse(Float64,"33.3434")
     1:100
     100:-1:1
     'a':'z'
     zeros(10)
     zeros((10,20))
     ones(10,10)
     fill(10,(5,5))
     diff([2,3,4,5,6,6])
     [1 2 3 ; 4 5 6 ; 7 8 9]
     vcat([0 0 0], [1 2 3 ; 4 5 6 ; 7 8 9])
     hcat([0;0;0], [1 2 3 ; 4 5 6 ; 7 8 9])
     length([1,2,3,4])
     size([1 2 ; 3 4])
     vcat([1,2,3],[2,3])
     vcat([1;2;3],[2;3])
     unique([2,3,34,4,5,6,7,7,7,7])
     reverse([2,3,4,5,10])
     reverse("abcdefgh")
     mod(10,2)
     div(20,3)
     fld(5,2)
     push!([2,3,4],20)
     pop!([2,3,3])
     a,b...= [1,2,3,4,4]
     1,2,3].+1
     parse.(Int,["2","2","2"])
     readlines("data.txt")
     3 in [3,4,5]
     3 ∈ [3,4,5]
     countmap("asdasdasdasdas") #using StatsBase
     map(x->x+1,[1,2,3])
     reduce((x,acc) -> acc + x,[1,2,3,4])

```
