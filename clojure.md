# Clojure

```clojure
(range 1 100) 
(vec (range 1 100)) 
(apply max (range 1 100)) 
(apply min (range 1 100)) 
(take 2 [1,2,3,4,5]) 
(sort [10,2,3,2,12,3])  
(distinct [10,2,3,2,12,3]) 
(cons 3 (cons 2 []))  
(str  "a" "b") 
(count [1,2,3,4,5]) 
(str 34) 
(Float/parseFloat "0.34234") 
(concat [1,2,3] [1,2,3])  
(mod 10 2) 
(Math/floor 23.2) 
(reverse "12312asdas") 
(apply str data)   list char to string 
(seq "sdasdasd")   string to list char 
(apply + [1,2,3,4])   add 
(map vector  '(1,2,3) '(2,5,6))  is zip 
```

# Let blocks
```clojure
(defn pangram? [s] 
  (let [a (set (str/lower-case s)) b (set (map char (range 97 123)))]
    (= (count (set/difference b a)) 0)))
```

# Tail Recursion
```clojure
(loop [output [] [x & xs] coll]
    (if (= x nil)
      output
      (recur (conj output (f x)) xs))))
```

# Thread Macros
```clojure
(defn get-digits [n]
  (->>  n
        (iterate #(quot % 10))
        (take-while pos?)
        (map #(mod % 10))))

```


