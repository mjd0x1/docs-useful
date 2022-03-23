# Julia 


## Multiple Dispatch
```julia
  f(x::Number, y::Number) = 2x - y
  f(x::Complex,y::Complex) = 2*x + y
  f(2im,3im)
  f(2,3)
```

## Structs

```julia
mutable struct SomeData
    id::Int
    name::String
    value::Float64
end

SomeData.([1,1,3],["s","l","f"],[2,3,4])
sort(b,by = (x) -> x.name)

struct Point{T}
    x::T
    y::T
end

mutable struct Robot 
    position::Point{Int}
    direction::Int
    Robot((x, y), d) = begin
        direction = d
        position = Point{Int}(x, y)
        new(position, direction)
    end
end

struct Dog end
struct Lion end

shout(x::Dog) = "bark"
shout(x::Lion) = "roar"

for x in [Dog(),Lion()]
    println(shout(x))
end

```

# Loops
```julia 
for x = 1:length(names)
    if names[x] == "down"
        aim += ids[x]
    end
end
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

# Functions
```julia
    add_one(x) =  x  + 1
    function add_one(x)
        x + 1
    end

```



## Arrays

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
     hcat(arr…) 
     length([1,2,3,4])
     size([1 2 ; 3 4])
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
     [1,2,3].+1
     parse.(Int,["2","2","2"])
     readlines("data.txt")
     3 in [3,4,5]
     3 ∈ [3,4,5]
     countmap("asdasdasdasdas") #using StatsBase
     map(x->x+1,[1,2,3])
     reduce((x,acc) -> acc + x,[1,2,3,4])
     filter(x-> x < 10,ls) 
     any(x -> x < 0,  d) 
     all(x -> x < 0,  d)
     a = [1,2,3,4,5] ; a[a.<5]
     a = [1,2,3,4,5] ; a'a
     digits(1000)
     (m.match[1] for m in eachmatch(r"[A-Za-z']+", phrase))
     match(r"[abc]", "banana").match 
     trunc_score = score > 255 ? score - 256 : score 
     Pkg.add("") 
     findall(x->x==2,[1,2,3,2]) 
     findfirst(x->x==2,[1,2,4,4]) 
     max([1,2,3]…) 
     [(i,j) for i=1:3,j=1:3 if i < j] 
     fact(x) = x == 0 ? 1 : x * fact(x-1) 
     f(ls,acc) =  ls==[] ? acc : f(ls[1:end-1],acc+ls[end]) 
     'a':'z' |> collect |> join
     split(“s,as,s,as”,”,”) 
     replace(x,"," => "") 
     Iterators.partition("weqweqwewq",2) |> collect 
     Iterators.Flatten([[1,2,3],[2,3,4]]) |> collect
     intersect(a,b)
     union(a,b)
     setdiff(a,b)
     readlines("data.txt")
     println(a)

```

# Symbols
```julia

\pi 
\cap 
\in 
\equiv 
\ge 
\le 
\ne 
\notin 
\subseteq 

```



# Consuming web service

```julia
using HTTP 
using JSON 

url =  "http://localhost:3005/asd 
headers = Dict("Content-Type" => "application/json") 
body = Dict("x" => 10 , "y" => 20) 
data = HTTP.request("POST",url,headers,JSON.json(body)) 
JSON.Parser.parse(String(data.body))["output"] 
```

# Web API

```julia
route("/testFunc", method = POST) do 
    data = jsonpayload() 
    m = convert(Array{Float64,1}, data["data"])
    json(Dict("Output" => ones(5,5) )) 
end 

```

# Tests

```julia
using Test

include("collatz-conjecture.jl")

# canonical data
@testset "Canonical data" begin
    @test collatz_steps(1) == 0
    @test collatz_steps(16) == 4
    @test collatz_steps(12) == 9
    @test collatz_steps(1000000) == 152
    @test_throws DomainError collatz_steps(0)
    @test_throws DomainError collatz_steps(-15)
end
```

# Benchmarks

```julia
using BenchmarkTools

include("prime-factors.jl")

for f in  [prime_factors,prime_factors2,prime_factors3]
    println(f)
    @btime $f(901255)
end
```

# Errors
```julia
 if base_out < 2 throw(DomainError("output base must be > 1")) end
 if length(strand_1) != length(strand_2) throw(ArgumentError("Require equal length of vectors")) end
```







