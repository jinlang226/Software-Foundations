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



# Paper: Interactive Proofs in Higher-Order Concurrent Separation Logic

## Shallow Embedding

prove P and 

