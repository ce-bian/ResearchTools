# Julia Tricks & Cheatsheet *(in progress)*

A collection of **useful Julia commands and packages** for scientific computing and data analysis.  
Designed for quick reference and copy-paste use.

**Last updated:** Jan 2026  
**Author:** Eileen Bian

---

## 1. Learning Resources

### Core Tutorials
- QuantEcon Julia Intro  
  https://julia.quantecon.org/intro.html
- QuantEcon: Julia by Example  
  https://julia.quantecon.org/getting_started_julia/julia_by_example.html
- Julia for Science & Engineering  
  https://www.matecdev.com/posts/julia-tutorial-science-engineering.html

### Course Repositories (UBC Econ)
- ECON 622  
  https://github.com/ubcecon/ECON622
- ECON 628 (2018)  
  https://github.com/ubcecon/ECON628_2018

---

## 2. Setting up Julia Environment

---

## 3. Core Data Structures

#### Arrays, Vectors, Matrices

```julia
A = Array{Float64}(undef, 3, 3)
v = Vector{Float64}(undef, 5)
M = Matrix{Float64}(undef, 4, 4)
```

- `Vector` is an alias for a **1-D Array**
- `Matrix` is a **2-D Array**

Reference:  
https://stackoverflow.com/questions/61171531/difference-between-array-and-vector

---


## 4. Macros 

#### `@show`

Print both the **expression and its value**.

```julia
@show 2x - 3y
@show x + y
```

Output:
```
2x - 3y = 1.0
x + y = 3.0
```

---

## 5. Data manipulation with DataFrames.jl
Package: https://dataframes.juliadata.org/stable/
#### Vertical Concatenation with Source ID

```julia
vcat(df1, df2; source=:source)
```

#### `mapcols` (similar to `lapply`)

```julia
mapcols(mean, df)
```

Reference:  
https://dataframes.juliadata.org/stable/lib/functions/#DataFrames.mapcols

---

## 6. Linear Algebra, Calculus & Probability

##### Solve Linear System `Ax = b`

```julia
using LinearSolve

prob = LinearProblem(A, b)
sol  = solve(prob)
```

Reference:  
https://linearsolve.sciml.ai/stable/tutorials/linear/

---

##### Probability Distributions

```julia
using Distributions

quantile(Chisq(k), 0.95)
pdf(Normal(0, 1), x)
```

---

#### Numerical Integration

```julia
using QuadGK
quadgk(z -> (z + 3)^2 / exp(-z), 2, Inf, atol=1e-8)[1]
```

---

## 7. Input / Output

### CSV

```julia
using CSV, DataFrames
df = CSV.read("data.csv", DataFrame)
```

### JLD2
Compressed storage of Julia objects.

```julia
using JLD2
@save "data.jld2" A B C
@load "data.jld2" A B C
```

---

## 8. Solving Equations & Root Finding

```julia
using NLsolve
nlsolve(f, x0)

using Roots
find_zero(x -> f(x, t), (a, b), atol=1e-10)
```

---


## 9. Optimization


---

## 10. Integer Programming


---

## 11. Plotting & Tables

```julia
using LaTeXStrings
plot!(xlabel=L"\lambda", ylabel=L"\pi(\lambda,k)")

using PrettyTables
pretty_table(df)
```

---

## 12. Parallel Computing

```julia
using ThreadsX
ThreadsX.map(f, collection)
```

---

## 13. Across languages

---



## Miscellaneous Julia Tricks

#### `push!`

Add elements **in place**.

```julia
v = Int[]
push!(v, 3)
push!(v, 5)
```

Explore documentation:

```julia
?push!
```

Reference:  
https://towardsdatascience.com/everything-you-need-to-know-about-push-in-julia-1f01891f1c0a

---
