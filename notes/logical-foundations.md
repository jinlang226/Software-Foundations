https://coq.inria.fr/doc/v8.12/refman/proof-engine/tactics.html

destruct as [|n’] is called intro pattern. Tells coq what variable names to introduce in each subgoal 

apply

injection

discriminate

simpl in H

What we can do instead is to first introduce all the quantified
    variables and then _re-generalize_ one or more of them,
    selectively taking variables out of the context and putting them
    back at the beginning of the goal.  The [generalize dependent]
    tactic does this.

Unfolding Definitions



# Tactics

Here are the ones we've seen:

  - [intros]: move hypotheses/variables from goal to context

  - [reflexivity]: finish the proof (when the goal looks like [e =
    e])

  - [apply]: prove goal using a hypothesis, lemma, or constructor

  - [apply... in H]: apply a hypothesis, lemma, or constructor to
    a hypothesis in the context (forward reasoning)

  - [apply... with...]: explicitly specify values for variables
    that cannot be determined by pattern matching

  - [simpl]: simplify computations in the goal

  - [simpl in H]: ... or a hypothesis

  - [rewrite]: use an equality hypothesis (or lemma) to rewrite the goal
    1. **`rewrite Hx`**: This command is used when you have a hypothesis `Hx : a = b` and you want to replace occurrences of `a` with `b` in your goal. It takes the left-hand side (LHS) of the equation in `Hx` and replaces it with the right-hand side (RHS).
    2. **`rewrite <- Hx`**: This command is used when you have a hypothesis `Hx : a = b` but you want to do the replacement in the opposite direction, replacing occurrences of `b` with `a` in your goal. It takes the RHS of the equation in `Hx` and replaces it with the LHS. This is essentially using the symmetry of equality: if `a = b`, then `b = a`.

  - [rewrite ... in H]: ... or a hypothesis

  - [symmetry]: changes a goal of the form [t=u] into [u=t]

  - [symmetry in H]: changes a hypothesis of the form [t=u] into
    [u=t]

  - [transitivity y]: prove a goal [x=z] by proving two new subgoals,
    [x=y] and [y=z]

  - [unfold]: replace a defined constant by its right-hand side in
    the goal

  - [unfold... in H]: ... or a hypothesis

  - [destruct... as...]: case analysis on values of inductively
    defined types

  - [destruct... eqn:...]: specify the name of an equation to be
    added to the context, recording the result of the case
    analysis

  - [induction... as...]: induction on values of inductively
    defined types

  - [injection... as...]: reason by injectivity on equalities
    between values of inductively defined types

  - [discriminate]: reason by disjointness of constructors on
    equalities between values of inductively defined types

  - [assert (H: e)] (or [assert (e) as H]): introduce a "local
    lemma" [e] and call it [H]

  - [generalize dependent x]: move the variable [x] (and anything else that depends on it) from the context back to an explicit hypothesis in the goal formula

  - [f_equal]: change a goal of the form [f x = f y] into [x = y] *





# Logic

## Logical Connectives

When the current proof context contains a hypothesis [H] of the form [A /\ B], writing [destruct H as [HA HB]] will remove [H]  from the context and replace it with two new hypotheses: [HA], stating that [A] is true, and [HB], stating that [B] is true.  

- left
- right

## Disjunction

[A \/ B] is true when either [A] or [B] is.  This infix notation stands for [or A B], where [or : Prop -> Prop -> Prop]. 

## Falsehood and Negation

- Coq actually makes a slightly different but equivalent choice, defining [~ P] as [P -> False], where [False] is a specific un-provable proposition defined in the standard library

- Notation "x <> y" := (~(x = y))

- Since reasoning with [ex_falso_quodlibet] is quite common, Coq provides a built-in tactic, [**exfalso**], for applying it. 

- Besides [False], Coq's standard library also defines [True], a
      proposition that is trivially true. To prove it, we use the
      constant [I : True], which is also defined in the standard
      library:

## Logical Equivalence 

- if and only if <->

## Existential Quantification

there is some [x] of type [T] such that some property [P] holds of [x], we write [exists x : T, P]

## Programming with Propositions

## Applying Theorems to Arguments

So far, we've seen one primary place that propositions can appear:
    in [Theorem] (and [Lemma] and [Example]) declarations. 





 We can later use this name in any situation where a proposition is
    expected -- for example, as the claim in a [Theorem] declaration. 



(** However, if we like, we can add functional extensionality to Coq's
    core using the [Axiom] command. *)

Axiom functional_extensionality : forall {X Y: Type}
                                    {f g : X -> Y},
  (forall (x:X), f x = g x) -> f = g.

(** Defining something as an [Axiom] has the same effect as stating a
    theorem and skipping its proof using [Admitted], but it alerts the
    reader that this isn't just something we're going to come back and
    fill in later! *)