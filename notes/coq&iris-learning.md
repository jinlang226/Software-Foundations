# Logic

## Propositional Logic

Propositional Logic deals with propositions that can either be true or false. It uses logical connectives such as AND (∧), OR (∨), NOT (¬), IMPLIES (→), and IFF (if and only if, ↔) to form more complex statements from simpler ones.

## First Order Logic (FOL)

FOL extends Propositional Logic by introducing quantifiers, variables, and predicates. This allows for the expression of statements about some or all elements of a domain, making it more expressive for modeling and reasoning about the properties of objects and their relationships.

- **Quantifiers** such as the existential quantifier (∃, "there exists") and the universal quantifier (∀, "for all") enable statements over sets of objects.
- **Variables** represent objects in the domain.
- **Predicates** represent properties or relations among objects.
- **Functions** can be used to denote mappings from objects to objects.

Example: ∀book∃authorAuthorOf(author,book)

## Temporal Logic

Temporal Logic is used to reason about the ordering of events in time, with applications in verifying concurrent and distributed systems. It introduces modalities related to time, such as "always" (□), "eventually" (◊), "until," and "next."

**Example**: Using Linear Temporal Logic (LTL), consider *p* as "request is made," and *q* as "request is granted."

- □p→◊q: If a request is made (and keeps being made), eventually, the request will be granted. This captures the notion of an eventual response to a persistent condition.

## Meta Logic

Meta Logic is a branch of logic that studies the properties of various logical systems themselves. It involves reasoning about logics, their expressiveness, consistency, completeness, and other properties.

**Example**: A meta-logical statement might involve the completeness theorem for propositional logic, which asserts that if a formula is true under every interpretation, then there is a proof of the formula within the logic system. This is more about the property of the logic system itself rather than a statement within the system.

- "Every consistent set of propositional logic formulas has a model." This is a meta-logical statement about propositional logic, referring to its completeness and consistency.

These examples illustrate the richness and diversity of logical systems and their applicability in various domains, from formal verification and reasoning about time-dependent processes to understanding the foundations of logic and reasoning itself.

### Meta Language

A meta language is a language used to express, define, or model another language. 



## Object Logic

- State
- Prop



# Paper: Interactive Proofs in Higher-Order Concurrent Separation Logic, [Video](https://www.youtube.com/watch?v=LSYiMjubeHs&ab_channel=POPLPARIS2017)

## Motivation

- interactive proofs instead of automating everything
  - Concurrent Algorithms in Iris
  - Logical relations in Iris
  - ...



## To embed a logic in to a proof assistant

### Shallow Embedding

In a shallow embedding, the constructs of the object logic (the logic being represented) are directly mapped to the constructs of the meta-language (the language in which the logic is being represented). The meta-language's own syntax and semantics are used to represent and reason about the object logic.

```haskell
-- Shallow embedding
type Expr = Integer

-- Functions directly use Haskell's arithmetic
add :: Expr -> Expr -> Expr
add x y = x + y

multiply :: Expr -> Expr -> Expr
multiply x y = x * y

-- Example usage:
-- The expression (2 + 3) * 4 is represented and evaluated using Haskell's arithmetic
example :: Expr
example = multiply (add 2 3) 4
```



### Deep Embedding

In a deep embedding, the constructs of the object logic are represented as data structures within the meta-language. This involves creating explicit representations for all syntax elements and possibly their semantics as well.

```haskell
-- Deep embedding
data Expr
  = Lit Integer      -- A literal value
  | Add Expr Expr    -- Addition of two expressions
  | Mul Expr Expr    -- Multiplication of two expressions

-- An evaluator function that traverses the AST and computes a value
eval :: Expr -> Integer
eval (Lit n)     = n
eval (Add e1 e2) = eval e1 + eval e2
eval (Mul e1 e2) = eval e1 * eval e2

-- Example usage:
-- The expression (2 + 3) * 4 is represented as an AST
example :: Expr
example = Mul (Add (Lit 2) (Lit 3)) (Lit 4)

-- The expression can be evaluated to a value
result :: Integer
result = eval example

```



## Contexts in IPM

variable and pure Coq hypotheses 

---------------------------------------\

Persistent hypotheses in object logic

--------------------------------------- $\square$

Spatial hypotheses in object logic 

---------------------------------------*

Goal in object logic



## Proving Hoare Triples

The "Texan triple" [ {{{ P }}} e {{{ RET v, Q }}} ] is syntactic sugar for:

p -* WP e {{ v, Q v}}

 ∀ Φ, P -∗ (Q -∗ Φ v) -∗ WP e {{ v, Φ v }}

 Which is logically equivalent to [ P -∗ WP e {{ x, x = v ∗ Q }} ]



## Others

- φ - “fai”  “fi”
- ψ - “sai” or “psi”



# Iris References

[Heap Lang](https://gitlab.mpi-sws.org/iris/iris/-/blob/master/docs/heap_lang.md?ref_type=heads)

[tactics](https://gitlab.mpi-sws.org/iris/iris/-/blob/master/docs/proof_mode.md?ref_type=heads)
