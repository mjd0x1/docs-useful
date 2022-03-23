# Haskell

```haskell
[1..100] 
maximum  [1,2,23,4,5] 
minimum  [1,2,23,4,5] 
drop  2 [1,2,23,4,5] 
take 3 [1,2,23,4,5] 
take 3 [1..]        ** Try removing the take 
sort [10,2,3,12,3] 
[2,3,2,112]!!1 
nub [1,2,3,3,4]      ** you may need to ‘import Data.List’ 
3:34:23:23:[] 
[2,3] ++ [2,3,4] 
length [1..10] 
show 23 
read "23.232"::Double 
concat [[1,2,3],[1,2,3]] 
(1,"2323",223.23)    ** tuples 
zipWith (\x y -> x *y) [1,2,3,4,5] [5,4,3,2,1]
map (\x-> x**2) arr
filter (\x-> x < 5) arr
foldl (\x y-> x + y) 0 arr
```

# Hello World
```haskell
  f x =  "hello " ++ x 
  f “world” 
```

# Simple Function
```haskell
  f x y  = x + y 
  f 2.1 3 
```

# Recursion
```haskell
  sum_list (x:xs) acc  =  if xs == [] then (acc+x) else sum_list xs (acc+x) 
```

# Guards Pattern Matching
```haskell
sum_list (x:xs) acc  
                    | xs == [] =  (acc+x) 
                    | otherwise = sum_list xs (acc+x) 

sum_list [] acc = acc 
sum_list (x:xs) acc = sum_list xs (acc+x) 

```

# Case
```haskell
sum_list (x:xs) acc  = case (x:xs) of 
        (x:[]) ->  (acc+x) 
        otherwise -> sum_list xs (acc+x) 

```

# Where
```haskell
binomial:: Double-> Double-> Double-> Double 
binomial x n p  = p ** x * (1-p) **(n-x) * c where 
      c  = (factorial n) / ((factorial x) * factorial (n-x)) 
      factorial t = product [1..t] 
```

# Functors

Functors are things that can be mapped over e.g lists.. 
Described by the typeclass functor which has one method fmap 

```haskell
:t fmap 
fmap :: Functor f => (a -> b) -> f a -> f b 
```

# Maybe Types 

Maybe is a box with something inside it, we can pass it ‘purely’ around without looking inside the box 

```haskell
x  = Just 10 
y =  Nothing   
:t [x,y] 
[x,y] :: Num a => [Maybe a] 
```
 
# Applicatives 

 One level up from functors.  This defines  pure and <*>  Solves the problem how do I quickly add Just 20 and Just 10 and have the result still inside Just?

```haskell
pure(+)  <*> Just 20  <*> Just 10       
Just 30 
Just(+) <*> Just 20 <*> Just 10 
Just 30 
```

# Monads 

One level up from applicatives. 

```haskell
f = \x -> return (x*10)::Maybe Int 
f 10     Just 100 
f 3 	   Just 30 
f (Just 3)     doesn’t work??
```

So how do we solve the problem of a function that takes an 'unboxed' value and returns a 'boxed' value but we want to pass it a 'boxed' value?

```haskell
  >>= bind    take a value in a 'box',  feed into a function that expects a normal value  
  Just 3  >>= f	returns Just 30!!
```

Monads give us all the powers of functors, mapping over,  applicatives operating inside the 'boxes' without opening them and finally the ability to use a 'boxed' value for
functions that expect pure input. 

Monads are basically a 'box' that contain data/computations and a set of rules.  We can operate inside the box without necessarily opening the 'box'  

 



